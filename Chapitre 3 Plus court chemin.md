Problème centrale de l'ordonnancement.

## I - Définitions

Soit ${G=[X,U]}$ un graphe. On associe à chaque arc u de U un nombre l(u) appelé longueur de l'arc u.

On dit que G est un graphe valué.

La longueur d'un chemin ${\mu(s,t)}$ de s à t dans G est définie par :

$L(\mu(s,t)) = \sum\limits_{i=1}^{k} l(u_{i})$

Le problème du plus court chemin entre 2 sommets s et t consiste à trouver le chemin qui minimise $L(\mu(s,t))$.

**exemple:**

photo emilio

Quel est le plus court chemini de 0 à 3 ?

Que se passe-t-il si l(3,1) = -90

**Condition d'existance**

Soit $\mu(s,t)$ un chemin de s à t dans G. Supposons que $\mu(s,t)$ contient un circuit $\omega$.

Image emilio

On note $\mu'(s,t)$ le chemin $\mu(s,t)$ privé du circuit $\omega$.

Si l($\omega$)$ >= 0$ alors $L(\mu(s,t)) >= L(\mu'(s,t))$ et donc il est inutile de considérer $\mu$, on se contente de considérer $\mu'$.

Si l($\omega$) $< 0$ alors on peut passer une infinité de fois dans le circuit $\omega$. Dans ce cas, on dit que le plus court chemin n'existe pas.

Le problème change selon la nature du graphe et selon ce que l'on cherche. On distingue les graphes :
    - sans circuit / quelconques
    - longueurs positives / longueurs quelconques

On peut chercher le plus court chemin:
    - entre 2 sommets (one to one)
    - entre 1 sommet et tous les autres (one to all)
    - entre toutes les paires de sommets (all to all)

Les algorithmes associent aux sommets des étiquettes ou labels ou potentiels, qui représentent le plus court chemin jusqu'au sommet.

## II - Algorithmes de plus court chemin

### 1 - Graphe sans circuit longueurs quelconques one to all

Image emilio

Quand le graphe est sans circuit, on peut représenter les sommets dans un ordre topologique (de sorte que les arcs vont toujours de la gauche vers la droite).

Image emilio

On associe à chaque sommet j un nombre entier positif r(j) appelé le rang de j, défini par :

$r(j) = \left( \max_{i \in \Gamma^{-1}_j} r(i) \right) + 1$

Pour calculer le rang, on regarde les listes des prédécesseurs.

Calcul_du_rang(G)
rg = 0
**Début**
&emsp;&emsp;**TantQue** tous les sommets n'ont pas un rang **Faire**
&emsp;&emsp;&emsp;attribuer le rang rg à tous les sommets sans prédécesseur qui n'ont pas de rang
&emsp;&emsp;&emsp;retirer tou les sommets de rang rg des listes des prédécesseurs
&emsp;&emsp;&emsp;rg = rg + 1
&emsp;&emsp;**FinTantQue**
**Fin**

**exemple:**

Image emilio (tableau des rangs)

**exemple:**

Image emilio

Image emilio (tableau des rangs)

Image emilio

**Algorithme de Ford (1956)**

$\pi(s) = 0$
**Début**
&emsp;&emsp;**PourTout** j dans X \ {s}  dans l'ordre des rangs croissants **Faire**
&emsp;&emsp;&emsp;$\pi(j) = \min_{i \in \Gamma^{-1}_j} [\pi(i) + l(i,j)]$
&emsp;&emsp;**FinPourTout**
**Fin**

Image emilio

Image emilio (tableau des rangs)

### 2 - Graphe quelconque longueurs quelconques one to all

On note $\pi_j^{(k)}$ le potentiel du sommet j à l'itération k.

**Algorithme de Bellman-Ford (1958)**

$\pi_s^{(0)} = 0$
$\pi_j^{(0)} = +\infty$ ${\forall j \neq s}$
k = 0
**Début**
&emsp;&emsp;**Répéter**
&emsp;&emsp;&emsp;k = k + 1
&emsp;&emsp;&emsp;**PourTout** j dans X **Faire**
&emsp;&emsp;&emsp;&emsp;$\pi_j^{(k)} = \min_{i \in \Gamma^{-1}_j} [\pi_i^{(k-1)} + l(i,j)]$
&emsp;&emsp;&emsp;**FinPourTout**
&emsp;&emsp;**Jusqu'à** k = N ou ($\pi_j^{(k)} = \pi_j^{(k-1)}$ ${\forall j}$)
&emsp;&emsp;**Si** k = N **alors**
&emsp;&emsp;&emsp;Il existe un circuit < 0
&emsp;&emsp;**FinSi**
**Fin**

**exemple:**

Image emilio

Image emilio (tableau des rangs)

### 3 - Graphe quelconque longueurs positives one to all

A chaque itération on attribut un potentiel "définitif" (qui ne sera pas modifié).
On note $\overline{S}$ l'ensemble des sommets qui n'ont pas de potentiel définitif.

**Algorithme de Dijkstra (1959)**
$\pi_s = 0$
$\overline{S}$ = X \ {S}
$\pi_j =
\begin{cases}
    l(s,j) & \text{si } (s,j) \in U \\
    \infty & \text{sinon}
\end{cases}$
**TantQue** $\overline{S} \neq \emptyset$ **Faire**
&emsp;&emsp;Sélectionner j dans $\overline{S}$ \ tel que $\pi_j = \min_{j \in \overline{S}} [\pi_i]$
&emsp;&emsp;$\overline{S} = \overline{S} \backslash \{j\}$
&emsp;&emsp;**PourTout** k dans $\Gamma_j$ **Faire**
&emsp;&emsp;&emsp;$\pi_k = \min [\pi_k , \pi_j + l(j,k)]$
&emsp;&emsp;**FinPourTout**
**FinTantQue**

**exemple 1:**

Image emilio

Image emilio (tableau des rangs)

**exemple 2:**

Image emilio

Image emilio (tableau des rangs)

Pourquoi Djikstra fonctionne ?

On doit montrer qu'à chaque itération l'étiquette finale attribuée à un sommet est bien le plus court chemin jusqu'à ce sommet.

Image emilio

Tous les potentiels sont calculés à partir des sommets de S.
S'il y avait un plus court chemin pour atteindre j, il devrait passer par $\overline{S}$.
C'est impossible car $\pi_j$ est le plus petit des potentiels de $\overline{S}$ et toutes les longueurs sont positives.

### 4 - Graphe quelconque longueurs quelconques all to all

**Algorithme de Roy-Floyd-Warshall**

Pas vu cette année.

## III - Problème central de l'ordonnancement

Un problème d'ordonnancement consiste à déterminer la date de début d'une tâche, tout en rejectant un ensemble de contraintes, afin d'optimiser une fonction objectif.

Un projet (construction d'une maison, développement logiciel, ...) est un ensemble de tâches reliés entre elles par des contraintes de précédence, et dont on connait la durée.

Le problème central de l'ordonnancement consiste à déterminer les dates de début des tâches d'un projet, sans prendre en compte les contraintes de ressources, de sorte à terminer le plus tôt possible.

Contrainte de précédence :
i précède j si j ne peut pas commencer avant la fin de i.

On représente un projet par un graphe.

### 1 - Le graphe potentiels-tâches (Roy 1960)

On construit $G = [X,U]$ un graphe de la façon suivante :
    - X : ensemble des tâches du projet + un sommet début $\alpha$ + un sommet fin $\beta$
    - U :
        - un arc (i, j) si i précède j dans le projet et l(i, j) = $d_i$
        - durée de la tâche i
    - un arc ($\alpha$, i) de $\alpha$ vers toute tâche sans précésseur, de longueur l($\alpha$, i) = 0
    - un arc (i, $\beta$) de toute tâche i sans successeur vers $\beta$, de longueur l(i, $\beta$) = $d_i$

**exemple :**

On considère le projet suivant :

Image emilio
