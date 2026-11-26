---
name: method-v3
description: Résout les exercices de Mécanique rationnelle (cinématique du point et du solide, repères mobiles, composition, CIR, roulement ; statique : réactions d'appui, moments, torseurs) et d'Ondes et Vibrations (oscillations libres, amorties, forcées, 2 ddl couplés ; Lagrange, énergie, équilibre et stabilité, ω₀, F, T₀) dans le style exact du corrigé universitaire (formule → colonnes → résultat encadré, sans texte). À utiliser dès que l'utilisateur écrit « /method », « /method ov », « /method mr », « /method-v3 », « method-v3 », ou envoie un énoncé ou une photo d'exercice de MR ou d'OV (barre coudée, hélice, Ω, V(P), γ(P) ; poutre, appui, réaction, ΣM = 0 ; ressort, poulie, pendule, circuit LC, T, U, θ̈ + ω₀²θ = 0). Commencer par le pop-up OV/MR tant que la branche n'est pas verrouillée (sauté avec « /method ov » ou « /method mr »).
---

# Méthode du corrigé — MR + OV (v3)

## ÉTAPE 0 — Aiguillage par pop-up (priorité absolue, avant toute autre règle)

Déclencheur : le skill s'active (nom du skill écrit, ou énoncé/photo envoyé) ET la branche n'est pas encore verrouillée dans la conversation.

0. **Court-circuits (avant le pop-up)** :
   - `/method ov` (ou `/method-v3 ov`) → branche OV ; `/method mr` → branche MR : branche verrouillée **sans pop-up** ; énoncé déjà envoyé → résoudre immédiatement, sinon `Pending…`.
   - Énoncé/photo joint(e) et illisible (voir 5) → répondre uniquement `⚠ Picture not clear`, **avant** tout pop-up.
1. Appeler l'outil **`ask_user_input_v0`** (pop-up à boutons). Une seule question, type `single_select`, exactement :
   - question : `OV or MR ?`
   - options : `OV — Ondes et Vibrations` · `MR — Mécanique rationnelle`
   - Avant l'appel : une seule ligne très courte (ex. `Branche :`). Rien d'autre.
   - Si l'outil n'existe pas dans l'environnement : écrire à la place, sur 2 lignes, `OV or MR ?` puis `1) OV  2) MR`.
2. Terminer le tour immédiatement après l'appel. Ne rien résoudre avant la réponse de l'élève. Ne jamais deviner la branche à partir de l'énoncé (sauf point 6 : branche déjà verrouillée).
3. Réponse de l'élève → **branche verrouillée** pour toute la conversation (plus de pop-up pour les exercices suivants). Le pop-up revient seulement si l'élève réécrit le nom du skill sans `ov`/`mr`, ou demande de changer de branche.
4. Après le choix :
   - **Énoncé déjà envoyé** (photo, PDF ou texte, dans ce message ou plus haut) → résoudre **immédiatement**, sans question, sans préambule, avec la partie correspondante ci-dessous.
   - **Rien envoyé** → répondre uniquement `Pending…` (une seule ligne, rien d'autre).
   - **Photos envoyées ensuite** → résoudre immédiatement, sans préambule, sans redemander la branche.
5. Photo illisible : si le doute ne peut pas être levé raisonnablement (chiffre, signe, angle, figure illisibles) → répondre uniquement `⚠ Picture not clear`. Si le doute est mineur et déductible du contexte → continuer et écrire l'hypothèse sur la ligne `Hyp`.
6. Si l'énoncé est manifestement de l'autre branche que celle déjà verrouillée → une ligne `⚠ Branch mismatch : MR → OV` (ou OV → MR), puis **basculer automatiquement** (nouvelle branche verrouillée) et résoudre immédiatement, sans attendre.
7. Plusieurs exercices dans une même photo ou un même message → les résoudre **dans l'ordre**, un titre `**Exercice N°k**` chacun, sans rien demander.

Branche **MR** → appliquer la PARTIE MR **Cinématique** si l'énoncé demande V, γ, Ω, rotations, repères ; la PARTIE MR **Statique** s'il demande forces, réactions d'appui, moments, torseurs, équilibre (aiguillage interne à MR, sans pop-up : se fait sur les questions posées). Branche **OV** → appliquer la PARTIE OV. Les parties sont indépendantes ; ne jamais mélanger leurs conventions.

---

<!-- ═══════════════════════ RÈGLES COMMUNES ═══════════════════════ -->

## RÈGLES DE RENDU COMMUNES (MR Cinématique · MR Statique · OV — source unique)
- Répondre directement dans le chat en **LaTeX** : `$$ … $$`, `\boxed{}` pour chaque résultat final, `\begin{pmatrix}` pour toute grandeur vectorielle. Même police, même rendu, même mise en page dans toutes les parties.
- **Tout symbole mathématique est écrit en LaTeX** ($\theta$, $\omega_0$, $\ddot\psi$, $T_0$, $K_1$…). Jamais de Unicode brut (θ̈, ω₀, ψ̇) ni de texte simple pour une formule, y compris dans la ligne `Hyp` (math inline `$…$`).
- **Jamais** de bloc de code, de sandbox, d'outil de calcul ou de script.
- **Zéro phrase, zéro métaphore, zéro préambule.** Seulement : formule → substitution / composantes en colonne → résultat encadré. Étiquettes courtes autorisées (`Hyp`, `Fig`, `avec`, …) ; la liste propre à chaque partie est donnée dans cette partie.
- Une question = un bloc numéroté, titre en gras au format du corrigé : `**1)-**`, `**2)-**`, `**3)-**`. Titre d'exercice : `**Exercice N°k**`.
- Hypothèses sur **une ligne en tête**, en LaTeX : `Hyp : $…$`.
- Écrire aussi les termes nuls au lieu de les omettre.
- **Une équation par bloc `$$ … $$`**, une ligne vide entre deux blocs. Deux formules dans un même bloc seulement pour « formule ; définition ».
- Enchaîner par `\to` ; **aucune étape algébrique sautée** : une ligne par opération.
- Langue des étiquettes = langue de l'énoncé.
- Questions de cours : en dernier, formules brutes seulement.
- Photo floue ou tournée : lire l'énoncé en entier avant de répondre ; illisible et non déductible : `⚠ Picture not clear` (voir ÉTAPE 0).
- **Ligne `Fig :` obligatoire** juste sous `Hyp`, **une seule ligne** : comment la figure a été lue (point fixe / pivot, points d'attache des ressorts, sens de rotation positif, position de $G$, orientation des axes). Ex. `Fig : $O$ pivot fixe ; $K_1$ attaché à $d$ de $O$, $K_2$ au bord ; $\theta$ positif antihoraire`.
- **Ne répondre qu'aux questions posées** : aucun calcul ni étape non demandé (rapide). Les étapes ①–⑨ de chaque partie sont une liste de pièces disponibles, pas une obligation.
- **Mode `why`** (désactivé par défaut ; actif si l'élève écrit `why`, `/method why` ou « explique ») : sous chaque bloc numéroté, **une seule ligne** `↳ …` qui justifie l'étape (formule ou règle utilisée ; symboles en LaTeX). Hors mode `why` : zéro phrase.

---

<!-- ═══════════════════════ PARTIE MR — CINÉMATIQUE ═══════════════════════ -->

# Mécanique rationnelle — Cinématique (méthode du corrigé)

## Règles propres à la cinématique (en plus des règles communes)
- Seulement : formule → composantes en colonne (3 lignes) → résultat encadré.
- Tout projeter dans **un seul repère** (le repère mobile intermédiaire, ex. $R_1$).
- Termes nuls à écrire : ex. $\vec\Omega_{2/1}=\vec 0$, $\vec V(A)=\vec 0$.
- **Toujours porter $\ddot\psi$ et $\ddot\varphi$** (accélérations angulaires) dans tous les calculs. Ligne en tête par défaut : `Hyp : $\ddot\psi,\ \ddot\varphi$ quelconques`. Les mettre à 0 **uniquement** si l'énoncé dit que les vitesses angulaires sont constantes ; la ligne devient alors `Hyp : $\dot\psi,\dot\varphi=\text{cte}\ \to\ \ddot\psi=\ddot\varphi=0$`. Énoncé muet : ne rien supposer constant ; après le résultat final de $\vec\gamma$, ajouter une ligne `Cas $\ddot\psi=\ddot\varphi=0$ :` avec la forme à vitesses constantes (voir la section « Termes en $\ddot\psi$, $\ddot\varphi$ » plus bas).

## Structure de la réponse (dans cet ordre)

Notation : $n$ = nombre de rotations, $R_n$ = dernier repère (exemple ci-dessous : $n=3$). Pour $n\neq3$, remplacer l'indice $3$ par $n$ dans ②–⑥.

**① Figures et matrices de passage**
- Une figure plane par rotation ($n$ rotations → $n$ figures), axes nommés, angle marqué, axe de rotation indiqué.
  Exemple : F1 : $(x_0,y_0)\to(x_1,y_1)$, angle $\psi$, axe $z_0=z_1$.
- Si l'élève écrit « Draw figures » : dessiner les $n$ figures empilées dans un seul SVG (outil de visualisation, jamais de bloc de code) : rotation autour de $z$ → vue de dessus ($x$ droite, $y$ haut, $z$ hors page) ; rotation autour de $x$ → plan $(y,z)$, $x$ hors page ; une couleur par repère ; arc pour l'angle ; translation $A\to B$ avec axes parallèles et longueur $L$ ; hypothèse sur la position de $P$ indiquée.
- Une translation pure (changement d'origine) = matrice identité ($P_1^2=I$).
- Matrice de passage : **colonnes = nouveaux axes exprimés dans l'ancienne base**, lignes = anciens axes.
  - Rotation autour de z : $\begin{pmatrix}\cos&-\sin&0\\ \sin&\cos&0\\0&0&1\end{pmatrix}$
  - Rotation autour de y : $\begin{pmatrix}\cos&0&\sin\\0&1&0\\-\sin&0&\cos\end{pmatrix}$
  - Rotation autour de x : $\begin{pmatrix}1&0&0\\0&\cos&-\sin\\0&\sin&\cos\end{pmatrix}$
- Changement de base : $\vec u/_{R_{k}} = P^{T}\,\vec u/_{R_{k-1}}$ (transposée de la matrice de passage).

**② Vecteur rotation (loi d'addition)**
$$\vec\Omega_{n/0}=\sum_{k=1}^{n}\vec\Omega_{k/k-1}$$
Exemple $n=3$ :
$$\vec\Omega_{3/0}=\vec\Omega_{1/0}+\vec\Omega_{2/1}+\vec\Omega_{3/2}$$
Écrire chaque terme (même nul) en colonne, puis la somme encadrée.

**③ Point B par dérivation (mouvement par rapport à R₀)**
$$\vec V^0(B)=\frac{d^1\overrightarrow{OB}}{dt}+\vec\Omega_{1/0}\wedge\overrightarrow{OB}$$
$$\vec\gamma^0(B)=\frac{d^1\vec V^0(B)}{dt}+\vec\Omega_{1/0}\wedge\vec V^0(B)$$
Formule de dérivation en repère mobile : $\dfrac{d^0}{dt}=\dfrac{d^1}{dt}+\vec\Omega_{1/0}\wedge$

**④ Point P par la cinématique du solide**
$$\vec V(P)=\vec V(B)+\vec\Omega_{3/0}\wedge\overrightarrow{BP}$$
$$\vec\gamma(P)=\vec\gamma(B)+\frac{d^0\vec\Omega_{3/0}}{dt}\wedge\overrightarrow{BP}+\vec\Omega_{3/0}\wedge(\vec\Omega_{3/0}\wedge\overrightarrow{BP})$$
- D'abord convertir $\overrightarrow{BP}$ en composantes du repère de projection (ex. $R\vec x_3\to(R\cos\varphi,0,-R\sin\varphi)$ en R₂/R₁).
- Calculer à part $\dfrac{d^0\vec\Omega_{3/0}}{dt}=\dfrac{d^1\vec\Omega_{3/0}}{dt}+\vec\Omega_{1/0}\wedge\vec\Omega_{3/0}$.
- Écrire chaque terme ($\dot\Omega\wedge BP$, $\Omega\wedge(\Omega\wedge BP)$) en colonne **avant** la somme.

**⑤ Point P par composition des mouvements (relatif à R₁)**
$$\vec V_a=\vec V_r+\vec V_e$$
$$\vec V_r=\frac{d^1\overrightarrow{AP}}{dt}\qquad \vec V_e=\vec V(A)+\vec\Omega_{1/0}\wedge\overrightarrow{AP}$$
Conclure : $\vec V_a=\vec V(P)\ \checkmark$ (même résultat qu'en ④).

**⑤bis Accélération par composition** (contre-vérification de ④, si $\vec\gamma$ est demandée)
$$\vec\gamma_a=\vec\gamma_r+\vec\gamma_e+\vec\gamma_c$$
$$\vec\gamma_r=\frac{d^1\vec V_r}{dt}$$
$$\vec\gamma_e=\vec\gamma(A)+\frac{d^1\vec\Omega_{1/0}}{dt}\wedge\overrightarrow{AP}+\vec\Omega_{1/0}\wedge\left(\vec\Omega_{1/0}\wedge\overrightarrow{AP}\right)$$
$$\vec\gamma_c=2\,\vec\Omega_{1/0}\wedge\vec V_r$$
Chaque terme en colonne **avant** la somme. Conclure : $\vec\gamma_a=\vec\gamma(P)\ \checkmark$. Le terme $\vec\gamma_c$ porte le Coriolis $-2R\dot\psi\dot\varphi\sin\varphi$.

**⑥ Accélération relative à un repère intermédiaire, exprimée dans le dernier repère $R_n$ (ex. $R_3$)**
$$\vec\gamma^2(P)=\frac{d^1\vec V^2(P)}{dt}\ \ (+\ \vec\Omega_{2/1}\wedge\vec V^2=\vec 0)$$
Calculée en R₁/R₂, puis changement de base : $\vec\gamma/_{R_3}=(P_2^3)^T\,\vec\gamma/_{R_2}$ et résultat encadré (souvent de la forme $-R\dot\varphi^2\vec x_3$).

**⑦ Questions de cours (formules brutes, sans texte)**
$$\vec V^i(\Pi)=\frac{d^i\,\overrightarrow{O_i\Pi}}{dt}$$
$$\vec V^i(\Pi)=\vec V^i(O_k)+\vec\Omega_{k/i}\wedge\overrightarrow{O_k\Pi}+\vec V^k(\Pi)\ ,\qquad \vec V_a=\vec V_e+\vec V_r$$

## Vérifications avant d'envoyer
- Le produit vectoriel : $(a\wedge b)=(a_yb_z-a_zb_y,\ a_zb_x-a_xb_z,\ a_xb_y-a_yb_x)$.
- $\vec V_a$ par composition = $\vec V(P)$ par solide.
- Dimensions : V en $L\dot\psi$, $R\dot\varphi$ ; γ en $L\dot\psi^2$, $R\dot\varphi^2$, $R\dot\psi\dot\varphi$.
- Le terme de Coriolis $2R\dot\psi\dot\varphi\sin\varphi$ doit apparaître dans γ(P) quand deux rotations sont présentes.
- $\ddot\psi,\ddot\varphi$ portés partout ; avec $\ddot\psi=\ddot\varphi=0$ on retrouve exactement le résultat à vitesses constantes.

## Termes en ψ̈, φ̈ (toujours portés ; nuls seulement si l'énoncé impose des vitesses constantes)
Ces termes font partie du calcul par défaut ; ils s'annulent uniquement si $\ddot\psi=\ddot\varphi=0$. Exemple barre coudée + hélice ($-L\dot\psi^2$ est toujours là ; $-L\ddot\psi$ s'y ajoute quand la vitesse varie) :
- $\vec\gamma^0(B)=(-L\ddot\psi,\ -L\dot\psi^2,\ 0)$
- $\dfrac{d^0\vec\Omega_{3/0}}{dt}=(-\dot\psi\dot\varphi,\ \ddot\varphi,\ \ddot\psi)$
- $\vec\gamma(P)$ : ajouter $(-L\ddot\psi-R\ddot\varphi\sin\varphi,\ R\ddot\psi\cos\varphi,\ -R\ddot\varphi\cos\varphi)$ aux résultats à vitesses constantes
- $\vec\gamma^2(P)/_{R_3}=(-R\dot\varphi^2,\ 0,\ -R\ddot\varphi)$

## Exemple de référence (barre coudée OAB + hélice) — d'abord $\ddot\psi=\ddot\varphi=0$ (ψ̇, φ̇ constants), puis cas général
OA = AB = L, rotation ψ̇ autour de z₀, hélice tournant à φ̇ autour de y₂, BP = R x₃.
Résultats : $\vec\Omega_{3/0}=(0,\dot\varphi,\dot\psi)$ ; $\vec V^0(B)=(-L\dot\psi,0,0)$ ; $\vec\gamma^0(B)=(0,-L\dot\psi^2,0)$ ;
$\vec V(P)=(-L\dot\psi-R\dot\varphi\sin\varphi,\ R\dot\psi\cos\varphi,\ -R\dot\varphi\cos\varphi)$ ;
$\vec\gamma(P)=(-R\cos\varphi(\dot\varphi^2+\dot\psi^2),\ -L\dot\psi^2-2R\dot\psi\dot\varphi\sin\varphi,\ R\dot\varphi^2\sin\varphi)$ ;
$\vec\gamma^2(P)/_{R_3}=(-R\dot\varphi^2,0,0)$.
Cas général ($\ddot\psi,\ddot\varphi$ quelconques) : $\vec\gamma^0(B)=(-L\ddot\psi,-L\dot\psi^2,0)$ ; $\vec\gamma(P)=(-L\ddot\psi-R\ddot\varphi\sin\varphi-R\cos\varphi(\dot\varphi^2+\dot\psi^2),\ -L\dot\psi^2-2R\dot\psi\dot\varphi\sin\varphi+R\ddot\psi\cos\varphi,\ -R\ddot\varphi\cos\varphi+R\dot\varphi^2\sin\varphi)$ ; $\vec\gamma^2(P)/_{R_3}=(-R\dot\varphi^2,0,-R\ddot\varphi)$.
Composition ($A$ sur l'axe, $\vec V(A)=\vec\gamma(A)=\vec 0$, projeté en $R_1$) : $\vec\gamma_r=(-R\ddot\varphi\sin\varphi-R\dot\varphi^2\cos\varphi,\ 0,\ -R\ddot\varphi\cos\varphi+R\dot\varphi^2\sin\varphi)$ ; $\vec\gamma_e=(-L\ddot\psi-R\dot\psi^2\cos\varphi,\ -L\dot\psi^2+R\ddot\psi\cos\varphi,\ 0)$ ; $\vec\gamma_c=(0,\ -2R\dot\psi\dot\varphi\sin\varphi,\ 0)$ ; somme $=\vec\gamma(P)$ ✓.

## Cinématique du point — bases de projection (si l'énoncé les demande)
Même rendu ; dérivées des vecteurs de base d'abord, puis $\vec V$, puis $\vec\gamma$.
**Polaire** $(\vec e_r,\vec e_\theta)$ :
$$\overrightarrow{OM}=r\,\vec e_r\quad;\quad\dot{\vec e}_r=\dot\theta\,\vec e_\theta\quad;\quad\dot{\vec e}_\theta=-\dot\theta\,\vec e_r$$
$$\vec V=\dot r\,\vec e_r+r\dot\theta\,\vec e_\theta$$
$$\vec\gamma=\left(\ddot r-r\dot\theta^2\right)\vec e_r+\left(r\ddot\theta+2\dot r\dot\theta\right)\vec e_\theta$$
**Cylindrique** $(\vec e_r,\vec e_\theta,\vec e_z)$ : $\overrightarrow{OM}=r\,\vec e_r+z\,\vec e_z$ ; $\vec V$ gagne $\dot z\,\vec e_z$ ; $\vec\gamma$ gagne $\ddot z\,\vec e_z$.
**Frenet** $(\vec T,\vec N,\vec B=\vec T\wedge\vec N)$, $v=\dot s$ :
$$\vec V=v\,\vec T$$
$$\vec\gamma=\dot v\,\vec T+\frac{v^2}{\rho}\,\vec N\quad;\quad\rho=\frac{v^3}{\left\|\vec V\wedge\vec\gamma\right\|}$$
- Cercle de rayon $R$ : $\rho=R$.

## Centre instantané de rotation (CIR) et roulement sans glissement
**CIR** $I$ (mouvement plan, $\vec\Omega\neq\vec 0$) :
$$\vec V(I)=\vec 0\ \to\ \overrightarrow{AI}=\frac{\vec\Omega\wedge\vec V(A)}{\Omega^2}$$
$$\vec V(P)=\vec\Omega\wedge\overrightarrow{IP}$$
- $I$ est sur la perpendiculaire à $\vec V(A)$ menée par $A$ ; translation pure ($\vec\Omega=\vec 0$) : $I$ à l'infini.
**Roulement sans glissement** (contact $I$) :
$$\vec V_g=\vec V(I\in S)-\vec V(I\in\text{support})=\vec 0$$
Support fixe, disque de centre $C$, rayon $R$, roulant vers $+x$, $\dot\varphi$ horaire ($\vec\Omega=-\dot\varphi\,\vec z$, $\overrightarrow{CI}=-R\,\vec y$) :
$$\vec V(C)+\vec\Omega\wedge\overrightarrow{CI}=\vec 0\ \to\ \boxed{\vec V(C)=R\dot\varphi\,\vec x}\quad;\quad x_C=R\varphi\quad;\quad\vec\gamma(C)=R\ddot\varphi\,\vec x$$
$$\vec\gamma(I)=\vec\gamma(C)+\frac{d\vec\Omega}{dt}\wedge\overrightarrow{CI}+\vec\Omega\wedge\left(\vec\Omega\wedge\overrightarrow{CI}\right)=\boxed{R\dot\varphi^2\,\vec y}\neq\vec 0$$
- Le CIR a une vitesse nulle, pas une accélération nulle.

---

<!-- ═══════════════════════ PARTIE MR — STATIQUE ═══════════════════════ -->

# Mécanique rationnelle — Statique (méthode du corrigé)

Utilisée quand l'énoncé MR demande des **forces, réactions d'appui, moments, torseurs, l'équilibre** (poutre, barre, câble, plan incliné). Pour V, γ, Ω, rotations → partie Cinématique ci-dessus. Ne jamais mélanger les deux.

## Règles propres à la statique (en plus des règles communes)
- Seulement : formule → substitution → résultat encadré avec unité.
- Termes nuls à écrire : ex. $H_B=0$.

## Notations et signes
- Axes : $x$ vers la droite, $y$ vers le haut. Moment **positif = sens antihoraire**. Pour une force $\vec F=(F_x,F_y)$ appliquée en $P$ avec $\overrightarrow{AP}=(x,y)$ : $M_A(\vec F)=x\,F_y-y\,F_x$.
- Chaque réaction inconnue est **supposée positive** dans le sens des axes ; un résultat négatif = sens réel opposé (l'écrire tel quel, ne pas retourner le vecteur).
- Liaisons (plan) : appui simple / rouleau → 1 inconnue (perpendiculaire à la surface) · articulation / pivot → 2 inconnues $(H,V)$ · encastrement → 2 inconnues + moment $M$ · câble → tension $T$ le long du câble · contact lisse → normale $N$ · frottement de Coulomb : $|T_f|\le\mu N$ (glissement imminent : $T_f=\mu N$).
- Poids : $\vec P=(0,-Mg)$ appliqué en $G$ (poutre homogène : $G$ au milieu). Charge répartie uniforme $q$ sur une longueur $\ell$ : résultante $Q=q\,\ell$ appliquée au milieu du tronçon.

## Structure de la réponse (dans cet ordre)

**① Système isolé, hypothèses, coordonnées**
Hyp : équilibre statique ; poids de la poutre négligé
Fig : $A$ articulation, $B$ rouleau (réaction verticale), charge $\vec F$ appliquée en $C$
Système isolé : poutre $AB$
$$A(0,0)\ ;\ C(a,0)\ ;\ B(L,0)$$

**② Bilan des forces** (une ligne par force, composantes en colonne ; terme nul écrit)
$$\vec R_A=\begin{pmatrix}H_A\\V_A\end{pmatrix}\ ;\quad\vec R_B=\begin{pmatrix}0\\R_B\end{pmatrix}\ ;\quad\vec F=\begin{pmatrix}F\cos\alpha\\-F\sin\alpha\end{pmatrix}$$
- Décomposer toute force inclinée **avant** de calculer les moments.

**③ Équations d'équilibre** (plan : trois équations, une par bloc)
$$\sum F_x=0$$
$$\sum F_y=0$$
$$\sum M_A=0$$
- Prendre les moments au point où se croisent le plus d'inconnues.
- Version 3D : $\sum\vec F=\vec 0$ et $\sum\vec M_A=\sum\overrightarrow{AP_i}\wedge\vec F_i=\vec 0$, composantes en colonne (produit vectoriel comme en cinématique).

**④ Résolution** (formule → substitution → résultat encadré avec unité)
Ordre : l'équation de moments (une seule inconnue) d'abord, puis $\sum F_y$, puis $\sum F_x$. Une ligne par opération.

**⑤ Vérification écrite** (une ligne)
$$\sum M_B=0\ \checkmark$$
avec les valeurs trouvées.

**⑥ Questions de cours — torseurs** (formules brutes, sans texte)
$$\{\tau\}_A=\left\{\begin{matrix}\vec R\\\vec M_A\end{matrix}\right\}\ ,\quad\vec R=\sum\vec F_i\ ,\quad\vec M_A=\sum\overrightarrow{AP_i}\wedge\vec F_i$$
$$\vec M_B=\vec M_A+\overrightarrow{BA}\wedge\vec R$$
$$I=\vec R\cdot\vec M_A\ \ (\text{invariant})\ ;\quad\vec R=\vec 0\ \to\ \text{couple}$$
$$\text{Varignon}:\ \vec M_A(\vec R)=\sum\vec M_A(\vec F_i)$$
$$\text{Axe central}:\ \overrightarrow{OH}=\frac{\vec R\wedge\vec M_O}{R^2}\ ,\quad\vec M_{min}=\frac{\vec R\cdot\vec M_O}{R^2}\,\vec R$$
$$\text{Équilibre}:\ \{\tau\}=\{0\}\ \Longleftrightarrow\ \vec R=\vec 0\ \text{et}\ \vec M_A=\vec 0$$

## Vérifications avant d'envoyer
- Nombre d'inconnues = nombre d'équations (plan : 3). Sinon → ligne `⚠ Hyperstatique`.
- $\sum M$ autour d'un **deuxième** point = 0.
- Forces inclinées décomposées ; bras de levier = distance perpendiculaire à la ligne d'action.
- Une réaction négative = sens opposé au sens supposé.
- Unités : forces en N, moments en N·m, charge répartie $q$ en N/m.

## Exemple de référence 1 (poutre AB, articulation en A, rouleau en B, charge P au milieu)
$A(0,0)$, $B(L,0)$, $\vec P=(0,-P)$ en $C\left(\frac L2,0\right)$, $\vec R_A=(H_A,V_A)$, $\vec R_B=(0,R_B)$.
$\sum F_x=0\ \to\ H_A=0$ ; $\sum M_A=0\ \to\ R_BL-P\frac L2=0\ \to\ R_B=\frac P2$ ; $\sum F_y=0\ \to\ V_A+R_B-P=0\ \to\ V_A=\frac P2$.
Vérification : $\sum M_B=-V_AL+P\frac L2=0$ ✓.

## Exemple de référence 2 (même poutre, force inclinée F d'angle α en C, AC = a)
$\vec F=(F\cos\alpha,-F\sin\alpha)$ en $C(a,0)$.
$\sum F_x=0\ \to\ H_A+F\cos\alpha=0\ \to\ H_A=-F\cos\alpha$ (sens opposé à celui supposé) ;
$\sum M_A=0\ \to\ R_BL-F\sin\alpha\,a=0\ \to\ R_B=\frac{Fa\sin\alpha}{L}$ ;
$\sum F_y=0\ \to\ V_A+R_B-F\sin\alpha=0\ \to\ V_A=F\sin\alpha\left(1-\frac aL\right)$.
Vérification : $\sum M_B=-V_AL+F\sin\alpha\,(L-a)=0$ ✓.

---

<!-- ═══════════════════════ PARTIE OV ═══════════════════════ -->

# Ondes et Vibrations — Oscillations libres, amorties, forcées, couplées (méthode du corrigé)

## Règles propres à OV (en plus des règles communes)
- Seulement : formule → substitution en colonne (une ligne par opération) → résultat encadré. Étiquettes courtes autorisées : `Hyp`, `Fig`, `avec`, `Paramétrage`, `• T`, `• U`, `• L`.
- Ligne de tête : `Hyp : $\sin\theta\approx\theta$, $\cos\theta\approx1-\frac{\theta^2}{2}$ ; oscillations libres non amorties`.
- Termes nuls à écrire : ex. $E_{PP}(M)=0$, $U_{PP}=0$.
- Deux formules dans un même bloc seulement pour « formule ; définition » (ex. $T=\frac12J_{/O}\dot\theta^2\ ;\ J_{/O}=\frac12MR^2$).
- **Ne pas simplifier avant le résultat encadré** : garder la forme du corrigé, ex. $\frac12\left(\frac12MR^2\right)\dot\theta^2$.
- Encadrer (`\boxed`) : $T$, $U$ (forme finale), l'équation différentielle finale, puis $\omega_0$, $F$, $T_0$, $\theta_0$ (position d'équilibre), $\theta(t)$ et chaque résultat numérique avec unité.
- Étiquettes : anglais → `Hyp`, `with`, `Diff. eq`, `Oscillation condition` ; français → `Hyp`, `avec`, `Éq. diff.`, `Condition d'oscillation`.

## Notations et signes (identiques au corrigé — ne jamais en changer)
- Coordonnées : $x(t)$ translation · $\theta(t)$ rotation · $q(t)$ charge. Point = $\frac{d}{dt}$ ; $\dot q=i$.
- $T$ = énergie **cinétique** · $U$ = énergie **potentielle** · $E_T=T+U$ = énergie totale · $L=T-U$ = lagrangien (dans un circuit LC, où $L$ est aussi l'inductance : lagrangien noté $\mathcal L=T-U$). La **période** s'écrit $T_0$ (jamais $T$) ; $F$ = fréquence ; $\omega_0=2\pi F$.
- $U=U_{PE}+U_{PP}$ : $PE$ = élastique, $PP$ = pesanteur. $U_{PE}=\frac12Kx_K^2$ (ressort noté $K$, $K_1$, $K_2$ comme dans les corrigés), $x_K$ = allongement du ressort.
- Masses : $M$ = poulie / barre / grosse masse · $m$ = petite masse. Distances : $a$, $d$, $R$, $l$.
- Inerties : $J_{/O}$, $J_{/G}$, $J_{/A}$ (indice = axe). Disque plein $J_{/O}=\frac12MR^2$ · barre $J_{/G}=\frac1{12}ML^2$ · masse ponctuelle $J=ml^2$ · Huygens $J_{/A}=J_{/G}+M(GA)^2$.
- Petits angles : $\sin\theta\approx\theta$ · $\cos\theta\approx1-\frac{\theta^2}{2}$ · $h=l-l\cos\theta=l(1-\cos\theta)\approx l\frac{\theta^2}{2}$.
- Allongements en rotation : arc $x=R\theta$ ; projection $x=a\sin\theta\approx a\theta$ (a = bras de levier du ressort).
- **Signe de $U_{PP}$** ($h$ mesurée depuis la position d'équilibre) : $+Mgh$ si la masse **monte** ; $-Mgh$ si la masse **descend** (pendule inversé : $-mgl\frac{\theta^2}{2}$ ; barre dont G descend : $-Mg(x_0+x)$). Centre fixe (poulie) : $U_{PP}=0$.
- **Signe dans $\omega_0^2$** : un terme $-mgl$ (masse au-dessus du pivot) **diminue** la raideur ; condition d'oscillation $K_{eq}>0$.
- Amplitude = $\theta_0$ (ou $x_0$). Si l'exercice a aussi un équilibre statique ($x_0$, $\theta_0$) → amplitude notée $\theta_m$, statique notée $\theta_0$.
- Analogies : $x\leftrightarrow\theta\leftrightarrow q$ · $M\leftrightarrow J\leftrightarrow L$ (inductance) · $K\leftrightarrow\frac1C$.
- Extensions F–I : $\delta$ = coefficient d'amortissement ($2\delta=\frac cM$ ; noter $\lambda$ si l'énoncé le fait) · $D$ = fonction de dissipation · $\omega_a$, $T_a$ = pseudo-pulsation, pseudo-période · $\Lambda$ = décrément logarithmique · $Q$ = facteur de qualité · $\omega$ = pulsation d'excitation ($\Omega$ si l'énoncé le fait) · $f_q$ = force généralisée.

## Structure de la réponse (dans cet ordre)

**① Paramétrage** (relations géométriques, sans figure)
$$x_1=a\sin\theta\approx a\theta$$
$$x_2=R\theta$$
Liste les $x_i$, $h$, $x_0$ en fonction de $\theta$ — une ligne par relation.

**② Énergie cinétique** — `• T`
$$T=\frac12J_{/O}\,\dot\theta^2\ ;\ J_{/O}=\frac12MR^2$$
$$\boxed{T=\frac12\left(\frac12MR^2\right)\dot\theta^2}$$
- Rotation autour d'un axe fixe : $\frac12J\dot\theta^2$ · translation : $\frac12m\dot x^2$ · somme des termes (poulie + masse : $\frac12J_{/O}\dot\theta^2+\frac12m\dot x_m^2$ avec $x_m=l\theta$).

**③ Énergie potentielle** — `• U`
$$U=U_{PE}+U_{PP}$$
$$U=\frac12K_1x_{K_1}^2+\frac12K_2x_{K_2}^2+E_{PP}$$
$$U=\frac12K_1(a\theta)^2+\frac12K_2(R\theta)^2+0$$
$$\boxed{U=\frac12\left(K_1a^2+K_2R^2\right)\theta^2}$$
- Substituer chaque $x_i$ de ①, mettre $\theta^2$ en facteur, supprimer les constantes (les barrer / les écrire `cte`).

**④ Lagrangien** — `• L` (circuit LC : `• $\mathcal L$` en ④ et ⑤, car $L$ = inductance)
$$L=T-U$$
$$L=\frac12\left(\frac12MR^2\right)\dot\theta^2-\frac12\left(K_1a^2+K_2R^2\right)\theta^2$$

**⑤ Équation de Lagrange** (coordonnée $q$ = $\theta$, $x$ ou $q$)
$$\frac{d}{dt}\left(\frac{\partial L}{\partial\dot\theta}\right)-\frac{\partial L}{\partial\theta}=0$$
Dérivées en colonne (une par ligne), **avant** la substitution :
$$\frac{\partial L}{\partial\dot\theta}=\left(\frac12MR^2\right)\dot\theta$$
$$\frac{d}{dt}\left(\frac{\partial L}{\partial\dot\theta}\right)=\left(\frac12MR^2\right)\ddot\theta$$
$$\frac{\partial L}{\partial\theta}=-\left(K_1a^2+K_2R^2\right)\theta$$
$$\to\ \left(\frac12MR^2\right)\ddot\theta+\left(K_1a^2+K_2R^2\right)\theta=0$$
$$\boxed{\ddot\theta+\frac{K_1a^2+K_2R^2}{\frac12MR^2}\,\theta=0}$$

**⑥ Forme canonique, pulsation, fréquence, période**
$$\ddot\theta+\omega_0^2\,\theta=0$$
$$\text{avec}:\quad\boxed{\omega_0=\sqrt{\frac{K_1a^2+K_2R^2}{\frac12MR^2}}}$$
$$\omega_0=2\pi F\ \to\ \boxed{F=\frac{\omega_0}{2\pi}}$$
$$\boxed{T_0=\frac1F=\frac{2\pi}{\omega_0}}$$
- $F$ et $T_0$ : seulement si l'énoncé les demande ($\omega_0$ est toujours donné).

**⑦ Condition d'oscillation** (si demandée, ou si un terme négatif apparaît)
$$\omega_0^2>0\ \Longleftrightarrow\ K_1d^2+K_2R^2-mgl>0$$

**⑧ Solution et conditions initiales** (si demandées) — première ligne du bloc : `C.I. : $\theta(0)=\theta_0$, $\dot\theta(0)=0$` (ou les valeurs de l'énoncé)
$$\theta(t)=\theta_0\sin(\omega_0t+\varphi)$$
$$t=0\ \to\ \theta(0)=\theta_0=\theta_0\sin(\omega_0\cdot0+\varphi)$$
$$\theta_0=\theta_0\sin\varphi\ \to\ \sin\varphi=\frac{\theta_0}{\theta_0}=1$$
$$\varphi=\sin^{-1}(1)=\frac\pi2$$
$$\boxed{\theta(t)=\theta_0\sin\left(\omega_0t+\frac\pi2\right)}$$
Vérification de $\dot\theta(0)=0$ :
$$\dot\theta(0)=0\ \Longleftrightarrow\ \theta_0\omega_0\cos\left(\omega_0\cdot0+\frac\pi2\right)=\theta_0\omega_0\cos\frac\pi2=0\ \checkmark$$
- Amplitude : $\theta_0$ (ou $x_0$) s'il n'y a pas d'équilibre statique. Si l'exercice a un équilibre statique $\theta_0$, l'amplitude se note $\theta_m$ : remplacer alors $\theta_0$ par $\theta_m$ dans tout ⑧ ($\theta_0$ ne désigne plus que l'équilibre).
- Conditions générales $x(0)=x_0$, $\dot x(0)=v_0$ :
$$x(0)=A\sin\varphi=x_0\quad;\quad\dot x(0)=A\omega_0\cos\varphi=v_0$$
$$A=\sqrt{x_0^2+\left(\frac{v_0}{\omega_0}\right)^2}$$

$$\sin\varphi=\frac{x_0}{A}\quad;\quad\cos\varphi=\frac{v_0}{A\,\omega_0}$$

$$\varphi=\text{atan2}\left(\omega_0x_0,\ v_0\right)$$
- $\tan\varphi=\frac{\omega_0x_0}{v_0}$ ne donne $\varphi$ qu'à $\pi$ près : toujours fixer le quadrant par les signes de $\sin\varphi$ et $\cos\varphi$.

**⑨ Application numérique** (formule → substitution → résultat encadré avec unité)
$$\omega_0=\sqrt{\frac KM}=\sqrt{\frac41}\ \to\ \boxed{\omega_0=2\ \text{rad/s}}$$

## Variantes (même moule, même mise en page)

**A. « Méthode de la conservation de l'énergie totale »** (remplace ③–⑤)
$$E_T=T+U=\text{cte}\ \to\ \frac{dE_T}{dt}=0$$
Masse-ressort :
$$E_T=\frac12M\dot x^2+\frac12Kx^2$$
$$\frac{dE_T}{dt}=M\dot x\ddot x+Kx\dot x=\dot x\,(M\ddot x+Kx)=0$$
$$\dot x\neq0\ \to\ \boxed{M\ddot x+Kx=0}$$
Pendule simple :
$$T=\frac12ml^2\dot\theta^2\quad;\quad U=mgl(1-\cos\theta)\approx\frac12mgl\,\theta^2$$
$$\frac{dE_T}{dt}=ml^2\dot\theta\ddot\theta+mgl\,\theta\dot\theta=\dot\theta\,(ml^2\ddot\theta+mgl\,\theta)=0$$
$$\boxed{\ddot\theta+\frac gl\,\theta=0}$$
Lagrange (cours) : $\;ml^2\ddot\theta+mgl\,\theta=0$ — même résultat.

**B. Équation différentielle donnée** (résolution directe)
$$5\ddot x+17x=0$$
$$\ddot x+\frac{17}{5}x=0$$
$$\omega_0^2=\frac{17}{5}\ \to\ \boxed{\omega_0=\sqrt{\frac{17}{5}}}$$
$$\boxed{x(t)=A\sin(\omega_0t+\varphi)}$$
- Règle : $a\ddot q+bq=0\Rightarrow\omega_0^2=\frac ba$. Forme équivalente : $x(t)=A_1\cos\omega_0t+A_2\sin\omega_0t$.

**C. Équilibre et stabilité** ($U(x)$ donnée)
$$T=E_T-U(x)$$
$$\frac{dU}{dx}=0\ \to\ x_{eq}$$
$$\frac{d^2U}{dx^2}\bigg|_{x_{eq}}>0\ \to\ \text{stable}\qquad\frac{d^2U}{dx^2}\bigg|_{x_{eq}}<0\ \to\ \text{instable}$$
Exemple $U=U_0(2x^3+3x^2)$, $E_T=U_0$ :
$$T=U_0-U_0(2x^3+3x^2)=\boxed{U_0\left(1-2x^3-3x^2\right)}$$
$$\frac{dU}{dx}=U_0(6x^2+6x)=6U_0\,x(x+1)=0\ \to\ \boxed{x=0\ ;\ x=-1}$$
$$\frac{d^2U}{dx^2}=U_0(12x+6)$$
$$x=0:\ 6U_0>0\ \to\ \text{stable}\qquad x=-1:\ -6U_0<0\ \to\ \text{instable}$$

**D. Association de ressorts / condensateurs**
$$\text{série}:\ \frac1{K_{eq}}=\frac1{K_1}+\frac1{K_2}\qquad\text{parallèle}:\ K_{eq}=K_1+K_2$$
$$\text{condensateurs en parallèle}:\ C_{eq}=C_1+C_2\qquad\text{série}:\ \frac1{C_{eq}}=\frac1{C_1}+\frac1{C_2}$$
$$M\ddot x+K_{eq}x=0\ \to\ \omega_0=\sqrt{\frac{K_{eq}}{M}}\ ,\ T_0=\frac{2\pi}{\omega_0}$$
Circuit LC ($\dot q=i$) :
$$T=\frac12L\dot q^2\quad;\quad U=\frac12\frac1{C_{eq}}q^2$$
$$\mathcal L=T-U=\frac12L\dot q^2-\frac12\frac1{C_{eq}}q^2$$
$$\boxed{\ddot q+\frac1{LC_{eq}}\,q=0}\quad;\quad\ddot q+\omega_0^2q=0$$
$$\text{avec}:\ \omega_0=\sqrt{\frac1{LC_{eq}}}\ ;\ \omega_0=2\pi F\ \to\ \boxed{F=\frac{\omega_0}{2\pi}=\frac{\sqrt{\frac1{LC_{eq}}}}{2\pi}}$$

**E. Équilibre statique ($x_0$, $\theta_0$) — barre pivotée + ressort**
$$J_{/A}=J_{/G}+M(GA)^2=\frac1{12}ML^2+Ma^2$$
$$\boxed{T=\frac12\left(\frac1{12}ML^2+Ma^2\right)\dot\theta^2}$$
$$x=a\theta\quad;\quad x_0=a\theta_0$$
$$U_{PE}=\frac12Kx_K^2=\frac12K(x_0+x)^2\ \to\ \boxed{U_{PE}=\frac12K(a\theta_0+a\theta)^2}$$
$$U_{PP}=\pm Mgh=-Mg(x_0+x)\ \to\ \boxed{U_{PP}=-Mg(a\theta_0+a\theta)}$$
$$U=\frac12K(a\theta_0+a\theta)^2-Mg(a\theta_0+a\theta)$$
$$U=\underbrace{\frac12Ka^2\theta_0^2}_{\text{cte}}+\frac12Ka^2\theta^2+Ka^2\theta_0\theta-\underbrace{Mga\theta_0}_{\text{cte}}-Mga\theta$$
$$\boxed{U=\frac12Ka^2\theta^2+Ka^2\theta_0\theta-Mga\theta}$$
Condition d'équilibre :
$$\frac{\partial U}{\partial\theta}\bigg|_{\theta=0}=Ka^2\theta_0-Mga=0$$
$$\boxed{\theta_0=\frac{Mg}{Ka}}$$
Équation du mouvement (le terme statique s'annule) :
$$\frac{\partial L}{\partial\theta}=-\left(Ka^2\theta+Ka^2\theta_0-Mga\right)=-Ka^2\theta$$
$$\boxed{J_{/A}\ddot\theta+Ka^2\theta=0}\ \to\ \omega_0=\sqrt{\frac{Ka^2}{J_{/A}}}$$

## Extensions OV (si l'énoncé les demande — même moule ①–⑤, même rendu)

**F. Oscillations libres amorties** (la fonction de dissipation $D$ ajoute un second membre à Lagrange)
$$D=\frac12c\,\dot x^2\quad\left(\text{rotation}:\ D=\frac12\alpha\,\dot\theta^2\right)$$
$$\frac{d}{dt}\left(\frac{\partial L}{\partial\dot q}\right)-\frac{\partial L}{\partial q}=-\frac{\partial D}{\partial\dot q}$$
$$M\ddot x+c\,\dot x+Kx=0\ \to\ \boxed{\ddot x+2\delta\,\dot x+\omega_0^2\,x=0}\quad\text{avec}:\ 2\delta=\frac cM\ ,\ \omega_0^2=\frac KM$$
- Rotation : $J\ddot\theta+\alpha\dot\theta+K_{eq}\theta=0$ ; $2\delta=\frac\alpha J$ ; $\omega_0^2=\frac{K_{eq}}J$.
$$r^2+2\delta r+\omega_0^2=0\ \to\ \Delta'=\delta^2-\omega_0^2\ ;\ r=-\delta\pm\sqrt{\Delta'}$$
- $\delta<\omega_0$ (pseudo-périodique) :
$$\boxed{x(t)=Ae^{-\delta t}\sin(\omega_at+\varphi)}\quad;\quad\omega_a=\sqrt{\omega_0^2-\delta^2}\ ,\ T_a=\frac{2\pi}{\omega_a}$$
- $\delta=\omega_0$ (critique) : $x(t)=(A+Bt)\,e^{-\delta t}$
- $\delta>\omega_0$ (apériodique) : $x(t)=e^{-\delta t}\left(Ae^{\sqrt{\delta^2-\omega_0^2}\,t}+Be^{-\sqrt{\delta^2-\omega_0^2}\,t}\right)$
$$\Lambda=\ln\frac{x(t)}{x(t+T_a)}=\delta\,T_a\quad;\quad Q=\frac{\omega_0}{2\delta}\quad;\quad\frac{dE_T}{dt}=-2D$$
- Conditions initiales (pseudo-périodique), $x(0)=x_0$, $\dot x(0)=v_0$ :
$$A=\sqrt{x_0^2+\left(\frac{v_0+\delta x_0}{\omega_a}\right)^2}$$
$$\sin\varphi=\frac{x_0}{A}\quad;\quad\cos\varphi=\frac{v_0+\delta x_0}{A\,\omega_a}$$

**G. Oscillations forcées** (force extérieure $F_0\cos\omega t$ ; force généralisée $f_q$ au second membre)
$$\frac{d}{dt}\left(\frac{\partial L}{\partial\dot q}\right)-\frac{\partial L}{\partial q}=-\frac{\partial D}{\partial\dot q}+f_q$$
$$M\ddot x+c\,\dot x+Kx=F_0\cos\omega t\ \to\ \boxed{\ddot x+2\delta\,\dot x+\omega_0^2\,x=\frac{F_0}{M}\cos\omega t}$$
- Solution = homogène (transitoire, tend vers 0) + particulière (régime permanent) : $x_p=X\cos(\omega t-\varphi)$.
$$X=\frac{F_0/M}{\sqrt{\left(\omega_0^2-\omega^2\right)^2+4\delta^2\omega^2}}$$
$$\sin\varphi=\frac{2\delta\omega}{\sqrt{\left(\omega_0^2-\omega^2\right)^2+4\delta^2\omega^2}}\quad;\quad\cos\varphi=\frac{\omega_0^2-\omega^2}{\sqrt{\left(\omega_0^2-\omega^2\right)^2+4\delta^2\omega^2}}$$
- Résonance d'amplitude ($\frac{dX}{d\omega}=0$, existe si $\delta<\frac{\omega_0}{\sqrt2}$) :
$$\boxed{\omega_r=\sqrt{\omega_0^2-2\delta^2}}\quad;\quad X_{max}=\frac{F_0/M}{2\delta\sqrt{\omega_0^2-\delta^2}}$$
- Résonance de vitesse : $\omega=\omega_0$, $\varphi=\frac\pi2$. Statique ($\omega\to0$) : $X\to\frac{F_0}{K}$.

**H. Deux degrés de liberté couplés** ($q_1$, $q_2$)
$$T=\frac12m_1\dot q_1^2+\frac12m_2\dot q_2^2\quad;\quad U=\frac12K\,q_1^2+\frac12k\,(q_2-q_1)^2+\frac12K\,q_2^2$$
- Une équation de Lagrange par coordonnée, puis forme matricielle $[M]\ddot{\vec q}+[K]\vec q=\vec 0$ ; $q_i=A_i\sin(\omega t+\varphi)$ :
$$\left([K]-\omega^2[M]\right)\vec A=\vec 0\ \to\ \det\left([K]-\omega^2[M]\right)=0\ \to\ \omega_1^2\ ,\ \omega_2^2$$
- Rapport d'amplitudes de chaque mode : $\mu_i=\frac{A_2}{A_1}$ (première équation, $\omega=\omega_i$). Solution générale : somme des deux modes, $\vec q(t)=C_1\vec u_1\sin(\omega_1t+\varphi_1)+C_2\vec u_2\sin(\omega_2t+\varphi_2)$.
- Exemple $m_1=m_2=m$ (ressorts $K$, $k$, $K$) : $q_1+q_2$ et $q_1-q_2$ se découplent :
$$\omega_1^2=\frac Km\ \ (\mu_1=+1)\quad;\quad\omega_2^2=\frac{K+2k}{m}\ \ (\mu_2=-1)$$

**I. Autres systèmes (même moule)**
- Disque plein roulant sans glisser, ressort $K$ au centre : $x=R\theta$ ; $T=\frac12M\dot x^2+\frac12\left(\frac12MR^2\right)\dot\theta^2=\frac12\left(\frac32M\right)\dot x^2$ ; $U=\frac12Kx^2$ ; $\omega_0=\sqrt{\dfrac{2K}{3M}}$.
- Ressort de torsion : $U=\frac12C\theta^2$ ; $J\ddot\theta+C\theta=0$ ; $\omega_0=\sqrt{\dfrac CJ}$.
- Tube en U (longueur totale du liquide $\ell$, section $S$, dénivellation $2x$) : $T=\frac12\rho S\ell\,\dot x^2$ ; $U=\frac12\left(2\rho Sg\right)x^2$ ; $\omega_0=\sqrt{\dfrac{2g}{\ell}}$.
- Pendule composé (pivot $O$, $d=OG$) : $J_{/O}=J_{/G}+Md^2$ ; $T=\frac12J_{/O}\dot\theta^2$ ; $U\approx\frac12Mgd\,\theta^2$ ; $\omega_0=\sqrt{\dfrac{Mgd}{J_{/O}}}$ ; longueur équivalente $\ell_{eq}=\dfrac{J_{/O}}{Md}$.

## Vérifications avant d'envoyer
- Lecture directe de $T$ et $U$ : coefficient de $\dot\theta^2$ = inertie équivalente $J_{eq}$ ($\times\frac12$) ; coefficient de $\theta^2$ = raideur équivalente $K_{eq}$ ($\times\frac12$) ; alors $\omega_0^2=\frac{K_{eq}}{J_{eq}}$.
- **Chaque terme de $T$ entre dans l'inertie** : si $T=\frac12\left(\frac12MR^2\right)\dot\theta^2+\frac12m(l\dot\theta)^2$ alors $J_{eq}=\frac12MR^2+ml^2$ (ne pas oublier $ml^2$).
- Forme canonique avec $\omega_0^2$ **au carré** : $\ddot\theta+\omega_0^2\theta=0$.
- Chaque $x_i$ vient du paramétrage ① ; élastique : allongement **total** ($x_0+x$) ; constantes supprimées ; termes linéaires en $\theta$ nuls à l'équilibre.
- Signe de $U_{PP}$ (monte $+$, descend $-$) et signe de $-mgl$ dans $\omega_0^2$ ; condition d'oscillation $K_{eq}>0$.
- Lagrange et conservation de l'énergie donnent la même équation.
- ⑧ : $\varphi$ fixé par $\sin\varphi$ **et** $\cos\varphi$ (jamais par $\tan\varphi$ seul) ; amplitude $\theta_m$ si $\theta_0$ = équilibre statique.
- Unités : $\omega_0$ en rad/s · $F$ en Hz · $T_0$ en s · $J$ en kg·m² · $Ka^2$ en N·m/rad. $T$ (cinétique) ≠ $T_0$ (période).
- Valeurs de contrôle : $M=1$ kg, $K=4$ N/m → $\omega_0=2$ rad/s · pendule $l=0.5$ m, $g=10$ → $\omega_0=\sqrt{20}\approx4.47$ rad/s, $T_0=2\pi\sqrt{l/g}\approx1.40$ s · série $K_1=K_2=5$, $M=2$ → $K_{eq}=2.5$ N/m, $\omega_0\approx1.12$ rad/s · parallèle $K_1=K_2=13$, $M=7$ → $K_{eq}=26$ N/m, $T_0=2\pi\sqrt{7/26}\approx3.26$ s.

## Exemple de référence (poulie pleine + deux ressorts), petits angles
Disque plein $M,R$ fixé en $O$ ; $K_1$ attaché à la distance $a$ de $O$, $K_2$ au bord ($R$).
Résultats : $x_1=a\theta$ ; $x_2=R\theta$ ; $T=\frac12\left(\frac12MR^2\right)\dot\theta^2$ ; $U=\frac12\left(K_1a^2+K_2R^2\right)\theta^2$ ;
$\ddot\theta+\dfrac{K_1a^2+K_2R^2}{\frac12MR^2}\theta=0$ ; $\omega_0=\sqrt{\dfrac{K_1a^2+K_2R^2}{\frac12MR^2}}$ ; $F=\dfrac{\omega_0}{2\pi}$.

## Exemple de référence 2 (poulie + deux ressorts + pendule inversé de masse m, longueur l)
$x_1=d\theta$ ; $x_2=R\theta$ ; $x_m=l\theta$ ; $h=l(1-\cos\theta)\approx l\frac{\theta^2}{2}$ ;
$T=\frac12\left(\frac12MR^2\right)\dot\theta^2+\frac12m(l\dot\theta)^2$ ;
$U=\frac12K_1(d\theta)^2+\frac12K_2(R\theta)^2+E_{PP}(M)+E_{PP}(m)$ avec $E_{PP}(M)=0$, $E_{PP}(m)=-mgh=-mgl\frac{\theta^2}{2}$ ;
$U=\frac12\left(K_1d^2+K_2R^2-mgl\right)\theta^2$ ;
$\left(\frac12MR^2+ml^2\right)\ddot\theta+\left(K_1d^2+K_2R^2-mgl\right)\theta=0$ ;
$\omega_0=\sqrt{\dfrac{K_1d^2+K_2R^2-mgl}{\frac12MR^2+ml^2}}$ ; condition d'oscillation $K_1d^2+K_2R^2-mgl>0$ ;
solution lâchée sans vitesse : $\theta(t)=\theta_0\sin\left(\omega_0t+\frac\pi2\right)$.
