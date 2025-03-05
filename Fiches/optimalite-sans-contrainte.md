## Conditions d'optimalité des problèmes sans contrainte

On va s'intéresser ici à des résultats d'unicité et d'existence de solution à des problèmes de minimisation pour des fonctions différentiables d'ordre 1 à 2.

### Conditions à l'ordre 1

La différentiabilité offre un cadre agréable pour étudier les extremas locaux et globaux, alors qu'avant on avait du mal à déterminer le comportement local des fonctions.

**Inéquation d'Euler** 

Soit $f : K \to \mathbb R$, avec $K \subset V$ un **convexe** inclus dans un espace de Hilbert et $f$ **différentiable** sur $K$. 

Soit $\bar x$ un minimum _local_ de $f$ sur $K$. Alors, $\forall y \in K$ :

$$
D_{\bar x}f(y-\bar x) \geq 0
$$

Si $f$ est convexe $\bar x$ est un minimum global.

On appelle l'équation l'inégalité d'Euler. C'est un résultat extrêmement puissant, surtout sachant qu'on est sur un espace de Hilbert. Intuitivement, l'inégalité exprime le fait que $f$ est croissante dans toutes les directions permises par $K$.

La démonstration de ce résultat repose essentiellement sur le fait que $K$ est convexe. On choisit alors un voisinage de $\bar x$ dans $K$, par exemple une boule telle qu'intersectée avec $K$ donne un voisinage sur lequel $\bar x$ est minimiseur local.

L'équation d'Euler est seulement nécessaire en général. En revanche, elle est suffisante pour $f$ en plus convexe. En effet, par convexité, $f(y) \geq f(\bar x) + D_{\bar x}f(y-\bar x)$, et ce pour tout $y$ de $K$.

_Proposition_ : (Minimisation sur un ouvert) Soit $f:K \subset V \to \mathbb R$. Si $f$ admet un minimum local en $\bar x \in \mathring K$, alors $D_{\bar x} f = 0$.

La démonstration est un petit peu astucieuse, mais finalement intuitive. Le fait d'avoir une boule nous permet de prendre un vecteur et son opposé, et donc d'obtenir une différentielle positive pour un vecteur et son opposé.

Cette condition est nécessaire en général. Cependant, en passant à la dimension finie et en imposant $f$ convexe, on a l'équivalence suivante :

$$
\bar x \text{ est un minimum local de } f \iff \nabla _{\bar x} f = 0
$$

Par convexité, $\bar x$ est en plus un minimum global.

Remarque en passant : pour beaucoup d'ensembles, notamment ceux qui n'ont aucune "marge de manoeuvre" dans une dimension, l'intérieur de $K$ sera vide. Les boules imposent en quelque sorte un "mapping" complet de l'espace. (GROS ABUS !)


### Conditions à l'ordre 2

On se place dans un cadre encore plus confortable qui nous permettra de nous affranchir de la convexité de $f$ en précisant la nature des points critiques. Pour cette partie, on se restraint à $\mathbb R^n$ ou tout autre $\mathbb R$-espace vectoriel de dimension finie.

Soit $f: K \subset V \to \mathbb R$ une fonction $\mathcal C^1$ et deux fois différentiable en $\bar x \in \mathring K$.

1) Si $f$ admet un minimum local en $\bar x$, alors, $\forall h \in V$ :

$$
\nabla _{\bar x}f = 0 \text{ et } \nabla^2 _{\bar x}f(h, h) \geq 0
$$

On dit que la Hessienne est positive ou semi-définie positive. Ce résultat se démontre facilement grâce à un développement de Taylor-Young à l'ordre 2.

_Réciproquement :_

2) Si $\nabla _{\bar x} f = 0$ et $\nabla^2 _{\bar x}f(h, h) \geq \alpha \|h\|^2$, alors $\bar x$ est un minimum local.

La condition sur la Hessienne est équivalente à dire qu'elle est définie positive, puisqu'on est en dimension finie. En effet, Schwartz nous donne sa symétrie, elle est donc diagonalisable dans une base orthonormée. On peut alors prendre $\alpha = \lambda_1 = \text{min}_i |\lambda_i|$.

3) Si $f$ est deux fois différentiable sur un voisinage de $\bar x$, que sa Hessienne est semi-définie positive sur ce voisinage, et que $\nabla _{\bar x} f = 0$, alors $\bar x$ est minimum local.

Le point 2 se démontre facilement. Pour le point 3, il suffit de remarquer qu'un voisinage comprend un voisinage convexe, et d'utiliser la caractérisation $\mathcal C^2$ des fonctions convexes.