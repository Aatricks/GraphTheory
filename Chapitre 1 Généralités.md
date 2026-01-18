## I- Définitions

Un graphe ${G=[X,U]}$ est défini par
- un ensemble de sommets X, ${|X| = N}$
- un ensemble de U de couples de sommets

${u=(i,j) \in U}$
est un arc si le couple est ordonné
est une arrête sinon.

${i -u-> j}$ arc
${i -u- j}$ arrête

${|U|=M}$

Si u=(i,j) est un arc, i est l'origine, j est la destination
Si u=(i,j) est une arrête, i et j sont les extrémités

Un arc u=(i,j) est une boucle.
Un p-graphe est un graphe dans lequel il n'existe pas plus de p arcs de la forme (i,j) entre 2 sommets quelconque i et j.

On note ${Mj}$ l'ensemble des successeurs de j
	    ${Mj^{-1}}$ l'ensemble des prédécesseurs de j

Un **graphe simple** est 1 graphe sans boucle.

**exemple :** ${Cf.}$ graphe simple hugo



Soit ${G=[X,U]}$ un graphe orienté.

Une **chaîne** L de longueur q est une séquence de q arcs de la forme ${L=\{u_1,u_2,...,u_q\}}$ telle que chaque arc ${u_r(2 \leq r \leq q-1)}$ a une extrémité commune avec ${u_{r+1}}$. L'extrémité de ${u_1}$ non commune avec ${u_2}$ et l'extrémité de ${u_q}$ non commune avec ${u_{q-1}}$ sont les extrémités de la chaîne.

**exemple :**
${L=\{(2,0),(1,2),(1,3)\}}$ a pour extrémités 0 et 3.
Dans une chaîne élémentaire, on ne rencontre pas deux fois le même sommet.

Un **cycle** est une chaîne dont les extrémités coincident.

**exemple**:
${L=\{(1,0),(2,0),(1,2)\}}$ un cycle élémentaire ne contient auncun autre cycle.
Un graphe sans cycle est acyclique.


**Un** **chemin** est une chaîne dont tous les arcs sont orientés dans le même sens ("de parcours du chemin").

**exemple:**
${L=\{(1,2),(2,0)\}}$

**exemple**:
${Cf.}$ dessin chemin hugo ${L=\{(0,1),(1,0)\}}$ est un chemin

Un **circuit** est un chemin dont les extrémités coincident.

**exemple**:
${Cf.}$ dessin circuit hugo
${L=\{(0,1),(1,3),(3,5)\}}$ chemin
${L=\{(0,1),(1,3),(6,3),(5,6)\}}$ chaîne
${L=\{(2,4),(4,7),(7,2)\}}$ circuit
${L=\{(2,4),(7,4),(7,2)\}}$ cycle



Un graphe **biparti** est tel que X peut être partitioné en ${X_1}$ et ${X_2}$ (${X_1 \cup  X_2 = X}$ et ${X_1 \cap X_2 = \emptyset}$
et ${\forall u = (i,j) \in U}$ , ${i \in X_1}$ et ${j \in X_2}$
			ou ${i \in X_2}$ et ${j \in X_1}$

Un **graphe** **connexe** est tel que ${\forall (i,j) \in X^{2}}$ , il existe une chaîne reliant ${i}$ et ${j}$.

## II - Matrices associées à un graphe

### 1 - matrice d'incidence sommets-arcs

${G}$ graphe sans boucle, **orienté**

${A = (a_{iu}) _{\substack{ {1\leq i \leq N } \\ { 1 \leq u \leq M}}} }$
$$
\begin{cases}
  +1  \text{ si }  i \text{ est l'origine de u} \\
  -1 \text{ si } i \text{ est la destination de u} \\
0 \text{ si } i \text{ n'est pas une extrémité de } u
\end{cases}
$$
Autrement dit si ${u=(1,j)\in U}$ alors $$
\begin{cases}
  a_{iu}=+1  \\
  a_{ju}=-1 \\
a_{ku}=0 \forall k \in X, k\neq i,j
\end{cases}
$$
**exemple**:
${Cf.}$ dessin chemin hugo

$$
\begin{array}{c|cccccccc}
% Ligne de Titres (Indices de colonnes)
& 0 & 1 & 2 & 3 & 4 & 5 & 6 & 7 \\

% Contenu de la matrice
0 & & 1 & & 1 & & 1 & & \\
1 & & & & 1 & & & & \\
2 & & & & & 1 & & & \\
3 & & & & & & 1 & & \\
4 & & & & & & & & 1 \\
5 & & & & & & & 1 & \\
6 & & 1 & & 1 & & & & \\
7 & & & 1 & & 1 & & & \\
\end{array}
$$


### 3- matrice d'incidence sommets-sommets ou matrices d'adjacence

${G=[X,U]}$ un 1-graphe

${A = (a_{iu}) _{\substack{ {1\leq i \leq N } \\ { 1 \leq u \leq M}}} }$
${a_ij = }$ $$
\begin{cases}
  1 \text{ si } (i,j)\in U  \\
  0 \text{ sinon}
\end{cases}
$$
Si le graphe est non orienté ${u=(i,j)\in U \Rightarrow a_ij = a_ji =1}$


## III Codage d'un graphe

Les matrices sont creuses, on utilise des vecteurs

### 1 - Liste d'adjacence

G est un 1-graphe orienté

**exemple**

${Cf.}$ dessin hugo

Le nombre de successeurs de i est ${\alpha [i+1] - \alpha [i]}$

Si les arcs possèdent des attributs on ajoute autant de vecteurs $\beta$ que necessaire


### 2 - Liste des arrêtes/arcs

G sans boucle

**exemple**: ${Cf.}$ dessin hugo

${\forall u = (i,j) \in U}$

Pours les attributs, on ajoute des vecteurs $\beta$ comme necessaire
