# I - Définitions, propriétés

## 1- Définitions

Soit $G=[X,U]$ un graphe connexe orienté.

**Un flot dans $G$** est un vecteur $\phi = (\phi_1, \phi_2, \dots, \phi_M)$ de dimension M tq
$\forall i \in X, \sum_{u \in w^{+}(i)} \Phi_u = \sum_{u \in w^{-}(i)} \Phi_u$
On appelle $\Phi_u$ la quantité de flot sur l'arc $u$.

image hugo

**Propriété**
Soit $A=(a_{iu})_{1 \leq i \leq N, 1 \leq u \leq M}$ la matrice d'incidence sommets-arcs de $G=[X,U]$.
$\forall i \in X, \omega^{+}(i)=\{u\in U / a_{iu}=+1\}, \omega^{-}(i)=\{u\in U / a_{iu}=-1\}$ est équivalent à $A * \Phi = \vec{0}$

image démo hugo


## 2 - Le lemme des arcs colorés ou lemme de Minty

Soit $G=[X,U]$ un graphe orienté, dont les arcs sont aléatoirement colorés en Noir, Vert, Rouge, certains arcs peuvent être incolores.

image hugo lemme

Soit $u_0$ un arc Noir. Une et une seule des deux propositions suivantes est vraie:

* (a) par $u_0$ il passe un cycle Noir Rouge Vert avec tous les arcs Noirs orientés dans le même sens que $u_0$, tous les arcs Verts orientés dans le sens opposé à $u_0$ et tous les arcs Rouges orientés dans un sens quelconque et sans arcs incolores.

* (b) par $u_0$ il passe un cocycle Noir Vert Incolore avec tours les arcs Noirs orientés dans le même sens que $u_0$, tous les arcs Verts orientés dans le sens opposé à $u_0$ et tous les arcs Incolores orientés dans un sens quelconque et sans arcs Rouges.

image hugo (a)

image hugo (b)

démo :

On pose $u_0 = (t,s)$
On va marquer de proche en proche les sommets en utilisant la procédure de marquage suivante:
1 - marquer S
2 - Si i est un sommet marqué
- et $\exists u=(i,j) \in U$ avec j non marqué et $u$ Noir ou Rouge, alors on marque j
- et $\exists u=(j,i) \in U$ avec j non marqué et $u$ Vert ou Rouge, alors on marque j
On marque tous les sommets possibles - Deux cas se présentent:
* (a) le sommet $t$ est marqué
Par construction, on a une chaîne de $s$ à $t$ avec tous les arcs Noirs dans le sens de $u_0$, tous les arcs Verts dans le sens opposé à $u_0$ et tous les arcs Rouges dans un sens quelconque. Avec $u_0$ cette chaîne forme le cycle cherché.

image hugo (a)2

* (b) le sommet $t$ n'est pas marqué
On note A l'ensemble des sommets marqués.
Le cocycle $\omega(A)$ ne peut pas contenir d'arc Noir de A vers $x_i A$ (sinon le sommet de $x_i A$ serait marqué) donc tous les arcs Noirs sont dans le sens de $u_0$.
Le cocycle $\omega(A)$ ne peut pas contenir d'arc Vert de $x_i A$ vers $A$ (sinon le sommet de $x_i A$ serait marqué) donc tous les arcs Verts sont dans le sens opposé à $u_0$.
Le cocycle $\omega(A)$ ne peut pas contenir d'arc Rouge (sinon le sommet de $x_i A$ serait marqué) donc tous les arcs Rouges sont orientés dans un sens quelconque.
Il peut contenir des arcs Incolores orientés dans un sens quelconque.

image hugo (b)2


# II - Le problème du flot maximum

## 1 - Définitions

On considère un graphe $G=[X,U]$ possédant un sommet source $S \in X$ et un sommet puits $T \in X$ sans successeur.

image hugo

On notera $U^{0} = U \cup \{(t,s)\}$ et $G^{0} = [X,U^{0}]$.
$(t,s)$ est appelé l'arc de retour.
On dit que $\phi = (\phi_1, \phi_2, \dots, \phi_M)$ est un flot de $s$ à $t$ dans $G$ ssi $\forall i \in X, i \neq s, t, \sum_{u \in w^{+}(i)} \Phi_u = \sum_{u \in w^{-}(i)} \Phi_u$ et $\sum_{u \in w^{+}(s)} \Phi_u = \sum_{u \in w^{-}(t)} \Phi_u = \phi_{0}$.

Autrement dit, $\phi=(\phi_1, \phi_2, \dots, \phi_M)$ est un flot de $s$ à $t$ dans $G$ ssi $(\phi_0, \phi_1, \phi_2, \dots, \phi_M)$ est un flot dans $G^{0}$.

image hugo exemple

On associe à chaque arc $u\in U$ un nombre $c_u$ appelé la capacité de l'arc $u$.
Un **flot compatible** est un flot $\phi = (\phi_1, \phi_2, \dots, \phi_M)$ tq $\forall u \in U, \phi_u \leq c_u$.

Un flot maximum de $s$ à $t$ dans $G$ est un flot de $s$ à $t$ compatible tel que $\phi_0$ est maximum.

image exemple hugo

Le problème s'écrit :

image accolades hugo

On appelle coupe séparant $s$ et $t$ un ensemble d'arcs de la forme $\omega^{+}(A)$ avec $A \subset X$ tq $s \in A$ et $t \notin A$.

image hugo coupe séparant

La capacité de la coupe est la somme des capacités des arcs de la coupe.

## 2 - Propriétés, théorèmes

**Lemme** La valeur maximale d'un flot de $s$ à $t$ dans $G$ n'excède jamais la capacité d'une coupe séparant $s$ et $t$.

démo :
Soit $\phi$ un flot de $s$ à $t$ dans $G$.
Soit $A \subset X$ tq $s \in A$ et $t \notin A$.

image hugo démo

$\sum_{u \in \omega^{+}(A)} \phi_u = \phi_0 + \sum_{u \in \omega^{-}(A)} \phi_u$

$\Rightarrow \phi_0 = \sum_{u \in \omega^{+}(A)} \phi_u - \sum_{u \in \omega^{-}(A)} \phi_u$

$\Rightarrow \phi_0 \leq \sum_{u \in \omega^{+}(A)} \phi_u$

or $\phi_u \leq c_u \forall u \in \omega^{+}(A)$

donc $\phi_0 \leq \sum_{u \in \omega^{+}(A)} c_u$

**NB** ceci est vrai pour $\phi_0$ donnant sa valeur maximale.

**NB** Vrai aussi pour la coupe séparant $s$ et $t$ de capacité minimale.

$\max_{\phi_0} \leq \min_{\forall A \subset X, s \in A, t \notin A}C(\omega^{+}(A))$


**Théorème du flot maximum et de la coupe minimale**

Soit $G=[X,U]$ un graphe muni de capacités $c_u$, $S \in X$ un sommet source, $t \in X$ un sommet puits.
La valeur maximale d'un flot compatible de $s$ à $t$ dans $G$ est égale à la capacité d'une coupe minimale séparant $s$ et $t$.

démo :

Soit $\phi$ un flot maximum de $s$ à $t$ dans $G$ compatible avec les capacités $c_u$.
On associe aux arcs la couleur suivante:
- l'arc $(t,s)$ est Noir
- un arc $u$ tq $\phi_u = 0$ est Noir
- un arc $u$ tq $\phi_u = c_u$ est Vert
- un arc $u$ tq $0 < \phi_u < c_u$ est Rouge

Deux cas se présentent:
* (a) par l'arc $(t,s)$ il passe un cycle Noir Rouge Vert, soit $\vec{u}$ le vecteur associé à ce cycle. On pose $\phi' = \phi + \epsilon \vec{u}$ un nouveau vecteur $\epsilon > 0$ (suffisamment petit).

$A \phi' = A \phi + \epsilon A \vec{u} = \vec{0}$ donc $\phi'$ est un flot de $s$ à $t$ dans $G$.

impossible car $\phi_0'= \phi_0+\epsilon>\phi_0$ et $\phi_0$ maximum.

* (b) donc il existe un cocycle Noir Vert Incolore.

image hugo

On note $A$ l'ensemble des sommets qui contient $s$.
$\omega^{+}(A)$ est une coupe séparant $s$ et $t$.
$c(\omega^{+}(A)) = \sum_{u \in \omega^{+}(A)} c_u = \sum_{u \in \omega^{+}(A)} \phi_u$ car tous les arcs sont verts.

or $\sum_{u \in \omega^{-}(A)} \phi_u + \phi_0 = \sum_{u \in \omega^{+}(A)} \phi_u$, ici $\sum_{u \in \omega^{-}(A)} \phi_u = 0$ car tous les arcs sont noirs.

donc $\phi_0 = \sum_{u \in \omega^{+}(A)} \phi_u = \sum_{u \in \omega^{+}(A)} c_u$

donc $\phi_0$ est égal à la capacité d'une coupe séparant $s$ et $t$ donc $\phi_0$ est maximum et la capacité est minimale.


## 3 - Algorithme de Ford et Fulkerson

Soit $\phi = (\phi_1, \phi_2, \dots, \phi_M)$ un flot de $s$ à $t$ dans $G$ compatible avec les capacités $c_u$.
On ajoute l'arc de retour $\phi_0$.
On associe aux arcs la couleur suivante:
- l'arc $(t,s)$ est Noir
- un arc $u$ tq $\phi_u = 0$ est Noir
- un arc $u$ tq $\phi_u = c_u$ est Vert
- un arc $u$ tq $0 < \phi_u < c_u$ est Rouge

* (a) rechercher dans $G^0$ un cycle $\mu$ Noir Rouge Vert avec $u_0 = (t,s)$, **si** $\mu$ n'existe pas **alors** STOP $\phi$ est maximum.
* (b) calculer $\epsilon$, capacité résiduelle du cycle $\epsilon = \min(\epsilon_1, \epsilon_2)$ avec $\epsilon_1 = \min_{u \in \mu^{+}} (c_u - \phi_u)$ et $\epsilon_2 = \min_{u \in \mu^{-}} \phi_u$. On pose $\phi' = \phi + \epsilon \vec{\mu}$. Retour en (a)

image exemple hugo


