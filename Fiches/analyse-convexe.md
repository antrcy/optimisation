## Analyse convexe


### Rappels et premières propriétés 


_Definition_ : Soit $f : K \subset V \to \mathbb{R}$ avec $K$ un convexe non vide et $V$ un espace de Hilbert. On dit que $f$ est convexe si :

$$
\forall x, y \in K, \forall \lambda \in [0, 1], f(\lambda x + (1 - \lambda) y) \leq \lambda f(x) + (1 - \lambda) f(y)
$$

_Propriété_ : Si $f$ est convexe, alors $f$ est continue sur l'intérieur de $K$. Elle est aussi localement lipschitzienne sur l'intérieur de $K$.

_Théorème_ : (Rademacher) Soit $f : \mathbb{R}^n \to \mathbb{R}$ convexe. Alors $f$ est différentiable presque partout.

_Propriété_ : On appelle épigraphe de $f$ l'ensemble $\{(x, y) \in \mathbb{R}^n \times \mathbb{R} \mid y \geq f(x)\}$. Si $f$ est convexe, alors son épigraphe est convexe, et réciproquement.

_Propriété_ : On appelle sous-ensemble de niveaux de $f$ l'ensemble $\{x \in \mathbb{R}^n \mid f(x) \leq c\}$ pour un certain $c \in \mathbb{R}$. Si $f$ est convexe, alors ses sous-ensembles de niveaux sont convexes, et réciproquement.

Les deux résultats précédents se montrent facilement.

### Caractérisation des fonctions convexes différentiables

Soit $f:U\subset V \to \mathbb{R}$ de classe $C^1$ et $K \subset U$ convexe.

On a les équivalences suivantes :

1) f est convexe sur $K$

2) $\forall x,y \in K$ :

$$
f(x) + \langle \nabla _x f, y-x \rangle \leq f(y)
$$

On dit que $f$ est au dessus de ses plans tangents.

3) $\forall x,y \in K$ :

$$
0 \leq \langle \nabla_y f - \nabla_x f , y-x \rangle 
$$

La différentielle de $f$ est en quelque sorte croissante monotone.

Si $f$ est de classe $C^2$, on ajoute cette équivalence :

4) $\forall x \in K$ :

$$
\langle \nabla_x ^2 f (h) , h \rangle \geq 0
$$

On dit que la hessienne de $f$ est positive.

Dans le cas strictement convexe, les 3 premières équivalences tiennent toujours avec des inégalités strictes (pour $x \neq y$). Pour la dernière, on a :

$$
\langle \nabla_x ^2 f (h) , h \rangle > 0 \implies \text{ f est strictement convexe}
$$

La réciproque est en général fausse.


*Elements de preuve* :

$(1) \implies (2)$ en prenant $h = t(y-x)$ avec $f(x + h) - f(x)$.

$(2) \implies (1)$ en sommant deux inégalités bien choisies.

$(2) \implies (3)$ immédiat.

$(3) \implies (2)$ en mobilisant la monotonie d'une certaine fonction bien choisie et le théorème des accroissements finis.

$(2) \implies (4)$ via la formule de Taylor-Young.

$(4) \implies (3)$ en utilisant le théorème des accroissements finis.

Comme contre-exemple pour la réciproque de la dernière implication, on peut donner $x^4$. C'est une fonction strictement convexe en vertue du point $(3)$. Cependant, sa dérivée seconde s'annule en $0$.


**Cas particulier de la forme quadratique**

Supposons $f$ de la forme $f(x) = \frac{1}{2} \langle Ax, x \rangle + \langle b, x \rangle + c$.
Alors $f$ est strictement convexe si et seulement si $A$ est définie positive. On obtient la réciproque en utilisant le point $(3)$.

### Les fonctions fortement convexes

_Définition_ : On dit que $f$ est fortement convexe (notion plus restrictive que la stricte convexité) si il existe $\alpha > 0$ tel que :

$$
f((1-t)x + ty) \leq (1-t)f(x) + tf(y) - \frac{\alpha}{2} t(1-t) \|x-y\|^2
$$

Il est alors évident que :

$$
f \text{ est } \alpha \text{-convexe } \implies f \text{ est strictement convexe}
$$

Contre-exemple : $f(x) = \text{ln}(\frac{1}{x})$

On a la propriété suivante :

$$
f \text{ est } \alpha \text{-convexe } \iff g(x) = f(x) - \frac{\alpha}{2} \|x\|^2 \text{ est convexe}
$$

Ce dernier point se démontre assez péniblement (si on ne connaît pas d'identité sympathique), en développant les normes en produits scalaires.

**Caractérisation de l'alpha-convexité pour les fonctions différentiables**

On a les équivalences suivantes :

1) $f$ est $\alpha$-convexe sur $K$ convexe non-vide

2) $\forall x,y \in K$ :
$$
f(y) \geq f(x) + \langle \nabla f(x), y-x \rangle + \frac{\alpha}{2} \|y-x\|^2
$$
3) $\forall x,y \in K$ :

$$
\langle \nabla_y f- \nabla_x f , y - x \rangle \geq \alpha \|y-x\|^2
$$

Facile à montrer, si on utilise la propriété vue plus tôt.

Si on suppose que $f$ est deux fois différentiable, on a l'éqauivalence supplémentaire :

4) $\forall x \in K$ :
$$
\langle \nabla_x^2 f h, h \rangle \geq \alpha \|h\|^2
$$

Encore une fois, facile à montrer en utilisant la propriété vue plus tôt.

Dans le cas d'une fonction quadratique, on a la réciproque de l'implication vue précédemment :

$$
f \text{ est strictement convexe} \implies \exists \alpha > 0 \text{ tel que } f \text{ est } \alpha \text{-convexe}
$$

En effet, si $f$ est quadratique, alors sa stricte convexité engendre une Hessienne définie positive, dans ce cas particulier. Cela renvient à dire que ses valeurs propres sont strictement positives, et si on pose $\lambda_1 = \min \lambda_i$, alors on a bien $\langle \nabla_x^2 f h, h \rangle \geq \lambda_1 \|h\|^2$. On peut donc choisir $\alpha = \lambda_1$. On montre ce dernier résultat en se souvenant que la Hessienne est une matrice symétrique, et que ses valeurs propres sont réelles. Elle est donc diagonalisable dans une base orthonormée.
