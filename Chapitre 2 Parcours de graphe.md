## I - Parcours

Un parcours de graphe est un algorithme qui consiste à explorer les sommets du graphe de proche de proche en proche, à partir d'un sommet initial.

### 1 - Parcours en profondeur

On l'implémente à l'aide d'une pile LIFO (Last In First Out).

Parcours_profondeur(S)
Empiler(S)
Marquer(S)
**tantque** la pile n'est pas vide **faire**
    Dépiler(j)
    Marquer(j)
    **Pour** tout voisin k de j  **faire**
        **Si** k n'est pas marqué **alors**
            Empiler(k)
        **FinSi**
    **FinPour**
**FinTantque**

### 2 - Parcours en largeur

On l'implémente à l'aide d'une file FIFO (First In First Out).

Parcours_largeur(S)
Mettre S dans la file
Marquer(S)
**Tantque** la file n'est pas vide **faire**
    Retirer j le 1er de la file
    Marquer(j)
    **Pour** tout voisin k de j  **faire**
        **Si** k n'est pas marqué **alors**
            Mettre k dans la file
        **FinSi**
    **FinPour**
**FinTantque**

On peut implémenter ces algorithmes de façon récursive.

## II - Applications

### 1 - Connexité

${G=[X,U]}$ est connexe ssi ${\forall (i,j) \in X^{2}}$ , il existe une chaîne reliant ${i}$ et ${j}$.

On définit la relation i ${\mathbb{R}}$ j ${\Leftrightarrow}$ ${\begin{cases} i = j \\ \text{ou }\\ \text{il existe une chaîne reliant} i \text{ et } j\\ \end{cases} }$

Cette relation est :

- réflexive ? Oui, i ${\mathbb{R}}$ i
- symétrique ? Oui, si i ${\mathbb{R}}$ j , alors j ${\mathbb{R}}$ i
- transitive ? Oui, si i ${\mathbb{R}}$ j et j ${\mathbb{R}}$ k , alors i ${\mathbb{R}}$ k
une relation d'équivalence.

Les classes d'équivalence induites sur ${X}$ forment une partition en ${X_{1}, X_{2}, ..., X_{p}}$.

Image Emilio

p est appelé le nombre de connexité du graphe.

**Définition**
${G=[X,U]}$ un graphe, ${Y \subseteq X}$. Le sous-graphe ${H = [Y, U']}$ de G relativement à Y a pour sommet les sommets de Y et pour arcs ceux de V ayant leurs deux extrémités dans Y.

Les sous-graphes engendrés par les ensembles ${X_{1}, X_{2}, ..., X_{p}}$ sont appelés les composantes connexes de G.

Calcul_du_nombre_de_connexité(G)
**Début**
    Marque[j] = 0 ${\forall j \in X}$
    NbConnexité = 0
    **TantQue** min(Marque) = 0 **Faire**
        j = indice du 1er sommet tel que Marque[j] = 0
        NbConnexité = NbConnexité + 1
        Empiler(j)
        **Tantque** la pile n'est pas vide **faire**
            Dépiler(j)
            Marque[j] = NbConnexité
            **Pour** tout voisin k de j  **faire**
                **Si** Marque[k] = 0 **alors**
                    Empiler(k)
                **FinSi**
            **FinPour**
        **FinTantque**
    **FinTantQue**
**Fin**

### 2 - Existance d'un cycle
