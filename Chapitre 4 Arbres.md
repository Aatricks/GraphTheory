# I - Cycles, cocycles

## 1 - Vecteurs associés aux cycles

On considère un graphe $G = [X,U]$ orienté et un cycle $\mu$ élémentaire. On associe au cycle $\mu$ un sens de parcours donné par un des arcs du cycle.

On note $\mu^{+}$ l'ensemble des arcs dans le sens de parcours et $\mu^{-}$ l'ensemble des arcs dans le sens opposé.

Exemple : image hugo 
Sens du parcours : (2,0)
$\mu^{+} = \{(2,0)\}$
$\mu^{-} = \{(4,0), (3,4), (2,3)\}$

On associe au cycle $\mu$ un vecteur $\vec{\mu}$ de taille M défini par

$$\mu_{u} = \begin{cases}
1 & \text{si } u \in \mu^{+} \\
-1 & \text{si } u \in \mu^{-} \\
0 & \text{si } u \notin \mu
\end{cases}$$

$-\vec{\mu}$ correspond au sens de parcours opposé.
On dit que $p$ cycles $\mu_{1}, \mu_{2}, \ldots, \mu_{p}$ sont **dépendants** s'il existe $\alpha_{1}, \alpha_{2}, \ldots, \alpha_{p}$ non tous nuls tq .

$\sum_{i=1}^{p} \alpha_{i} \vec{\mu}_{i} = \vec{0}$

Lorsque $\sum_{i=1}^{p} = \vec{0} \Rightarrow \alpha_{i} = 0 \forall i \in \{1, \ldots, p\}$

On dit que les $p$ cycles sont indépendants (famille libre).
On associe un vecteur uniquement à un cycle élémentaire.
La somme de cycles élémentaires $\mu_1$ et $\mu_2$ est $\vec{\mu} = \vec{\mu}_1 + \vec{\mu}_2$.
Tout cycle est la somme de cycles élémentaires disjoints.

exemple : $\mu_2 = \{(0,1), (1,4), (4,0)\}$
image hugo graphe, tableau

## 2 - Cocycles

Soit $A \subset X$ in sous-ensemble de sommets. On note $\omega^{+}(A)$ l'ensemble des arcs incidents à A vers l'exterieur.
On note $\omega^{-}(A)$ l'ensemble des arcs incidents à A vers l'intérieur.

image hugo

On pose $\omega(A) = \omega^{+}(A) \cup \omega^{-}(A)$.
**Un cocycle** est un ensemble d'arcs de la forme $\omega(A)$ avec $A \subseteq X$.

image hugo graphe

exemple :
$A = \{1,3\}$
$\omega^{+}(A) = \{(1,4), (3,4)\}$
$\omega^{-}(A) = \{(1,4), (3,4)\}$

Un **cocircuit** est un cocycle où $\omega^{+}$ ou $\omega^{-}$ est vide (tous les arcs sont orientés dans le même sens).

On associe au cocycle $\theta = \omega(A)$ le vecteur $\vec{\theta}=\vec{\omega}(A)$ défini par

$$\theta_{u} = \begin{cases}
1 & \text{si } u \in \omega^{+}(A) \\
-1 & \text{si } u \in \omega^{-}(A) \\
0 & \text{si } u \notin \omega(A)
\end{cases}$$

image hugo tableau

Par extension on notera $\omega^{+}_{i}$ (respectivement $\omega^{-}_{i}$) l'ensemble des arcs ayant $i$ comme origine (respectivement destination).

**Proposition**
Soit $G=(X,U)$ un graphe, $\mu$ un cycle $G$, A la matrice d'incidence sommets-arcs de $G$. $A \vec{\mu} = \vec{0}

image hugo sommes

$A * \vec{\mu} = \vec{v}$ avec dimensions $A$ (NxM), $\vec{\mu}$ (M), $\vec{v}$ (N)

$v_i = \sum_{u=1}^{M} a_{iu}\mu_u = \sum_{u\in \mu^{+}}^{M} a_{iu}\mu_u(=+1) + \sum_{u\in \mu^{-}}^{M} a_{iu}\mu_u(=-1) + \sum_{u\notin \mu}^{M} a_{iu}\mu_u(=0)$

$v_i = \sum_{u\in \mu^{+}}^{M} a_{iu} + \sum_{u\in \mu^{-}}^{M} a_{iu}$

a) i est dans le cycle : image hugo

si $u_1$ et $u_2$ $\in \mu{+}$ image hugo $v_i = a_{iu_1}+a_{iu_2} = +1 + -1 = 0$

si $u_1$ et $u_2$ $\in \mu{-}$, $v_i = -a_{iu_1} - a_{iu_2} = -1 - (-1) = 0$

si $u_1 \in \mu^{+}$ et $u_2 \in \mu^{-}$
image hugo
$v_i = a_{iu_1}-a_{iu_2} = -1 - (-1) = 0$
image hugo 
$v_1 = 1 - 1 = 0$

# II - Arbres

## 1 - Définitions, propriétés

Un **arbre** est un graphe connexe sans cycle - c'est une notion non orientée.

Un graphe sans cycle non connexe est une forêt où chaque composante connexe est un arbre.

**Propriété**
$G = [X,T]$ est un arbre ssi il existe une chaîne et une seule entre 2 sommets quelconques.

CN : $G$ est un arbre, donc connexe, donc il existe une chaîne entre 2 sommets quelconques. Peut one avoir 2 chaînes entre 2 sommets quelconques? non car $G$ est sans cycle.

CS : $\exists$ 1 chaîne $\Rightarrow$ connexe
$\exists$ 1 chaîne $\Rightarrow$ sans cycle
$\Rightarrow$ un arbre

**Propriété**
Un arbre comporte $N-1$ arrêtes.

Soit $G=[X,U]$ un graphe.
**Un arbre de G** est un graphe partiel connexe sans cycle de $G$.
Un graphe partiel sans cycle de $G$ non nécéssairement connexe est **une forêt de $G$**

Une forêt maximale de $G$ est une forêt de $G$ maximale pour l'inclusion (on ne peut plus ajouter d'arrête).

Exemple : image forêt hugo

Algorithme de construction **d'une forêt maximale de $G$**

**Pour tout** $u\in G$ **faire**
&emsp;**si** $u$ passe par un cycle élémentaire $\mu$ dont toutes les arrêtes ($\noteq u$) sont rouges **alors**
&emsp;&emsp;on colorie $u$ en vert
&emsp;**sinon**
&emsp;&emsp;on le colorie en rouge
&emsp;**finsi**
**finpour**

Le graphe partiel des arrêtes rouges est une forêt maximale de $G$.

Exemple : image d'hugo

(0,1)R
(1,3)R
(2,4)R
(5,6)R
(1,2)R
(5,7)R
(3,4)- On les passe car ils créeraient un cycle
(0,3)-
(6,7)-

image hugo


**Application pour déterminer une base de cycles**

image hugo

(0,1)X
(0,4)X
(1,2)X
(2,1)-
(1,4)-
(1,2)-
(4,2)-
(4,3)x
(3,2)-

$\mu_1 = \{(1,2), (2,1) \}$
$\mu_2 = \{(0,1), (0,4), (1,4) \}$
$\mu_3 = \{(0,1), (1,2), (4,2), (0,4) \}$
$\mu_4 = \{(0,1), (1,2), (3,2), (4,3), (0,4) \}$
Ces 4 cycles forment une base de cycles.

$\mu_1 = (0,0,1,1,0,0,0,0)$
$\mu_2 = (1,-1,0,0,1,0,0,0)$
$\mu_3 = (1,-1,1,0,0,-1,0,0)$
$\mu_4 = (1,-1,1,0,0,0,-1,-1)$

$$
\mu_u = \begin{cases}
  +1  \text{ si }  i \text{ est l'origine de u} \\
  -1 \text{ si } i \text{ est la destination de u} \\
0 \text{ si } i \text{ n'est pas une extrémité de } u
\end{cases}
$$

Soit $\mu_A = \{(2,1), (1,4), (4,2)\}$ et $\mu_B = \{(1,2),(3,2),(4,3),(1,4) \}$
$\mu_A = (0,0,0,1,1,1,0,0)$
$\mu_B = (0,0,1,0,-1,0,-1,-1)$
$\mu_A = \mu_1 + \mu_2 - \mu_3$
$\mu_B = \mu_4 - \mu_2$

**Théorème**
Soit $G = [X,U]$ un graphe, $|X| = N, |U|=M$, p composantes connexes, soit $\mathcal{T} = [X,T]$ une forêt de $G$. Pour tout $u\in \overline{T} (\overline{T} = U \backslash \overline{T}$  on note $\mu^u$ le cycle unique contenu dans $T U \{u\}$. Les cycles $\mu^u$ pour $u\in \overline{T}$ forment une base de cycles dont la dimension est **M-N+p**.

**Propriété**
Soit $G=[X,U]$ un graphe, $|X|=N$, p composantes connexes. Une forêt maximale de $G$ comporte **N-p** arrêtes.

**Propriété**
$\mathcal{T}$ forest maximale de $G=[X,U]$. $\forall u \in \overline{T} = 0$ passe un cycle unique $\mu$ tq $\forall v \in \mu , v \neq u , v \in T$

image hugo

$u \in \overline{T}$ donc $u \notin T$
$u$ ne peut pas relier 2 composantes connexes sinon $\mathcal{T}$ ne serait pas maximale. Donc $u=(i,j)$ avec i et j dans la même composante connexe, donc il existe une chaîne unique reliant $i$ et $j$, donc cette chaîne $+\{u\}$ est le cycle cherché.

**Propriété**
$\mathcal{T} = [X,T]$ forêt maximale de $G=[X,U]$. $\forall u \in T$ il existe un cocycle unique $\theta$ tq $\forall v \in \theta, v \neq u, v\in\overline{T}$

image hugo

Les extrémités de $u$ appartiennent à la même composante connexe de $\mathcal{T}$. En retirant $u=(i,j)$ de $T$ on crée 2 composantes connexes notés $X^i$ et $X^j$. Le cocycle $\theta = \omega(X^i)$ contient $u$ et d'autres arrêtes qui ne sont pas dans $T$. On notera par la suite ce cocycle $\theta$.


## 2 - Arbres de poids minimum

Soit $G=[X,U]$ un graphe. On associe à chaque arrête $u$ un nombre $w_u$ appelé le poids de l'arrête $u$. Soit $G' = [X,U']$ un graphe partiel de $G$. Le poids de $G'$ est $w(G')= \sum_{u\in U'} w_u$

Par la suite on suppose que $G$ est connexe. Le problème de l'arbre de poids minimum est de rechercher un arbre de $G$ $\mathcal{T}^{*}$ tq $w(\mathcal{T}^*) = \min_{\forall \mathcal{T} \text{ arbre de } G} w(\mathcal{T})$

**Théorème**
$\mathcal{T} = [X,T]$ est un arbre de $G=[X,N]$ de poids minimum si et seulement si $\forall u \in T$, le cocycle $\theta^u$ est tel que $\forall v \in \theta^u, w_v \geq w_u$

image hugo

$\Rightarrow$ CN , s'il existe $v \in \theta^u$, $v\neq u$ et $w_v < w_u$, alors $\mathcal{T'}=[X,T']$ avec $T'=T\backslash \{u\} \cup \{v\}$ est encore un arbre de $G$ et $w(\mathcal{T'}) < w(\mathcal{T})$
impossible.

$\Leftarrow$ CS , On suppose que $\forall u \in \overline{T}$, le cocycle $\theta^u$ est tq $w_v \geq w_u$ $\forall v \in \theta^u$
On note $\mathcal{T^*}=[X, T^*]$ un arbre de poids minimum. On veut montrer que $w(\mathcal{T})=w(\mathcal{T^*})$

image hugo

Soit $u \in T$, $u \notin T^*$
Soit $\theta^u$ le cocycle associé à $u$, $u \notin T^* \Rightarrow$ par $u$ il passe un cycle unique dans $\mathcal{T^*}$ avec toutes les arrêtes dans $\mathcal{T^*}$ sauf $u$.
On note $\mu^u$ ce cycle.
Soit $v \in \theta^u \cap \mu^u, v\neq u$ 
$v \in T^*$ car $v \in \mu^u$ et $v\neq u$
$v \in T$ car $v \in \theta^u$ et $v\neq u$
donc $w_v \geq w_u$

Sin on avait $w_v>w_u$, en remplaçant $v$ par $u$ dans $\mathcal{T}$, on aurait un arbre de poids $< w(\mathcal{T^*})$, impossible.

Donc $w_v=w_u$
Donc $\forall u \in T$, $u \notin T^*$, on peut trouver une arrête $v \in T^*$ et $v \notin T$ tq $w_u=w_v$
Donc $w(\mathcal{T})=w(\mathcal{T^*})$


**Algorithme de Kruskal, 1956**

$w_{u_1} \leq w_{u_2} \leq \dots \leq w_{u_M}$
$T=\{u_1\}
$k=2$
**Pour** toute arrête $u_k$ **faire**
&emsp;&emsp;**si** $u_k$ ne génère pas de cycle avec les arrêtes de $T$ **alors**
&emsp;&emsp;&emsp;&emsp;$T=T\cup\{u_k\}$
&emsp;&emsp;**finsi**
**finpour**

image hugo

(0,1) 10 x
(7,8) 15 x
(2,3) 17 x
(3,8) 17 x
(1,2) 19 x
(0,6) 21 x
(3,4) 21 x
(2,8) 26 -
(0,7) 28 - 
(5,7) 31 x
(6,7) 33 -
(4,5) 36 -
(5,6) 42 -

image hugo

0: 0
1: $\not{1}$ 0
2: $\not{2}$ 0
3: $\not{3}$ $\not{2}$ 0
4: $\not{4}$ 0
5: $\not{5}$ 0
6: $\not{6}$ 0
7: $\not{7}$ $\not{2}$ 0
8 : $\not{8}$ $\not{7}$ $\not{2}$ 0

**Algorithme de Prim, 1957**

$A=\{S\}$
$T=\emptyset$
$\theta = \omega(A)$
**tant que** $A \neq X$ **faire**
&emsp;&emsp;rechercher dans $\theta$ l'arrête de poids minimum $u=(i,j)$ $j$ l'extrémité de $u$ qui n'est pas dans $A$
&emsp;&emsp;$A=A\cup\{j\}$
&emsp;&emsp;$\theta = \theta \Delta w(\{j\})$
&emsp;&emsp;$T=T\cup\{u\}$
**fin tant que**

avec $\Delta$ la distance géométrique

image emilio

