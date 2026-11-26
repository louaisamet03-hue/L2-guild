method-v3
A Claude skill that solves Rational Mechanics (MR) and Waves & Vibrations (OV) exercises in the exact style of a university answer key: formula → column substitution → boxed result, with no prose.

The skill itself (SKILL.md) is written in French, since it targets French-language university courses (Algeria / France). The output language follows the language of the problem statement.

What it does
Send an exercise (text or photo) and the skill answers directly in the chat, in LaTeX, following the layout of the official corrigé: numbered questions, one equation per block, every algebraic step written out, final results boxed.

Branches
Branch	Topics covered
MR – Kinematics	Point and rigid-body kinematics, moving frames, change of basis, successive rotations (ψ, θ, φ), V(P) and γ(P) by derivation / rigid-body / composition, instantaneous center of rotation (CIR), rolling without slipping
MR – Statics	Support reactions, moments, torsors, equilibrium of beams and bodies
OV	Free undamped oscillations (mass-spring, pendulum, pulley, disk, bar, LC circuit), Lagrange method, energy conservation, equilibrium and stability, damped, forced, and 2-DOF coupled oscillations, spring/capacitor combinations, ω₀, F, T₀
Usage
Command	Effect
/method	Shows an OV or MR pop-up, then locks the branch for the conversation
/method ov	Skips the pop-up, locks the OV branch
/method mr	Skips the pop-up, locks the MR branch
/method-v3 · method-v3	Same as /method
/method why	Enables why mode: one ↳ line under each step justifying the formula or rule used
Draw figures	(MR kinematics) draws the frame-rotation figures as a single SVG
Then send the exercise as text, a photo, or a PDF.

Typical flow
Type /method (or /method ov / /method mr).
Pick the branch if prompted.
Send the problem statement or a photo.
Get the full solution immediately, with no preamble and no follow-up questions.
Behavior
Branch lock: the branch is chosen once and kept for the whole conversation. If a problem clearly belongs to the other branch, the skill prints ⚠ Branch mismatch : MR → OV (or the reverse) and switches automatically.
Unreadable photo: if a digit, sign, angle, or figure can't be read reliably, the answer is just ⚠ Picture not clear. Minor, inferable doubts are written on an Hyp line.
Several exercises in one message: solved in order, each under **Exercice N°k**.
Only what is asked: no extra calculations beyond the questions posed.
No code, no scripts, no sandbox: pure LaTeX output.
Output format
Hyp : one-line hypotheses at the top
Fig : one line stating how the figure was read (fixed point, spring attachments, positive rotation direction, axes)
**1)-**, **2)-**, … one block per question
\boxed{} on every final result, \begin{pmatrix} for vectors
Zero terms are written out rather than omitted
Course questions come last, as raw formulas only
Kinematics specifics
Rotation matrices follow the corrigé convention: columns = new axes expressed in the old basis.
Angular accelerations ψ̈ and φ̈ are always carried through the calculation. They are set to zero only if the statement says the angular velocities are constant; otherwise a final Cas ψ̈ = φ̈ = 0 line gives the constant-velocity form.
Vibrations specifics
Standard sequence: parametrization → T → U → Lagrange (or energy method) → ω₀, F, T₀ → solution θ(t) with initial conditions.
Variants handled: energy method, given differential equation, equilibrium and stability from U(x), spring/capacitor series and parallel, static equilibrium offset (x₀, θ₀), damped (dissipation function D), forced (resonance), and coupled 2-DOF (normal modes).
Built-in sanity checks (units, canonical form ω₀², sign of U_PP, oscillation condition K_eq > 0).
Installation
Claude.ai / Claude app
Go to Settings → Capabilities → Skills.
Upload the method-v3 folder (or a zip containing SKILL.md).
Enable the skill.
Claude Code
Place the folder in your skills directory:

mkdir -p ~/.claude/skills/method-v3
cp SKILL.md ~/.claude/skills/method-v3/SKILL.md
Restart the session, then use /method.

Repository layout
method-v3/
├── SKILL.md      # the skill (instructions + examples)
└── README.md     # this file
Limitations
Accuracy depends on how clearly the figure and statement can be read from the photo. Always check the Hyp and Fig lines first, since they show how the exercise was interpreted.
The style targets one specific corrigé format. Other universities' conventions (axis names, sign conventions, notation) may differ.
It is a study aid. Compare the result with your own work and your course notes.
Contributing
Issues and pull requests are welcome, especially:

extra worked reference examples
new variants (e.g. more coupled systems, additional statics cases)
fixes to conventions that differ from your course
License
Add your license here (e.g. MIT).
