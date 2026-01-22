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

iamge hugo
