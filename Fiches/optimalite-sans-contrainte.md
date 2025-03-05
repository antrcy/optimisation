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

Cette condition est nécessaire en général. Cependant, en imposant $f$ convexe, on a l'équivalence suivante :

$$
\bar x \text{ est un minimum local de } f \iff D_{\bar x} f = 0
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


### Applications et exemples

**Le cas des fonctions quadratiques**

On se souvient d'une équivalence utile sur les fonctions quadratiques en dimension finie :

Pour $f(x) = \frac{1}{2} \langle Ax , x \rangle - \langle b , x \rangle + c$ avec $A \in S_n(\mathbb{R})$ et $b \in \mathbb{R}^n$, on a :
$$
f \text{ est strictement convexe} \iff A \text{ est définie positive}
$$

On a en effet :

$\nabla _x f = Ax - b$

$\nabla _x^2 f = A$

_Cas 1 - $A$ est définie positive_ :

$A$ est définie positive donc $f$ est strictement convexe. En particulier, si $\bar x$ est un minimum local, c'est un minimum global unique. De plus, puisque $f$ est convexe, $\bar x$ est un minimum local $\iff$ $\nabla _{\bar x}f = 0$. Donc le minimum est unique solution du système $Ax = b$. 

_Cas 2 - $A$ est semi-définie positive_ :

$f$ est convexe, car sa Hessienne est semi-définie positive (on a d'ailleurs la réciproque). Ainsi, $\bar x$ est minimum $\iff$ $\nabla_{\bar x}f = 0$. Ici cependant, l'existence et l'unicité de la solution du système $Ax = b$ ne peut pas être établie. Si $b \in \text{Im}(A)$, alors le système admet une solution $x_0$. Or puisque $\text{Ker}(A) \neq \empty$, il existe $v \neq 0$ tel que $Av = 0$, donc $\forall \lambda \in \mathbb{R}$, $x_0 + \lambda v$ est une solution. La fonction est donc minimisée sur un espace affine, donc convexe, elle est donc constante sur cet espace. Enfin, si $b \notin \text{Im}(A)$, l'équation d'Euler n'admet aucune solution. On rappelle que $\text{Im}(A) = \text{Ker}(A^t)^{\perp}$. Soit $v \neq 0$ tel que $Av = 0$. Alors, $v$ ne peut pas être orthogonal à $b$, puisque cela signifierait que $b \in \text{Im}(A)$. Ainsi, quitte à prendre un vecteur colinéaire à $v$, on a : 

$$
f(v) = -\langle b, v \rangle + c < 0
$$

On a alors :

$$
\lim_{n \to \infty} f(v n) = -\infty
$$

_Cas 3 - A est négative_ :

Cela signifie que $A$ admet une valeur propre négative $\lambda_1$. On note $e_1$ le vecteur propre associé. On obtient alors :

$$
f(e_1) = \lambda_1 \|e_1\|^2 - \langle b, e_1 \rangle + c
$$

De la même manière :

$$
\lim_{n \to \infty} f(e_1n) = - \infty
$$

**Minimisation d'une fonctionnelle**

On rappelle le théorème de Lax-Milgram. Soit $a : V \times V \to \mathbb R$ bilinéaire, continue et coercive, avec $H$ de Hilbert. Soit également $l : V \to \mathbb{R}$ une forme linéaire continue. Soit $f$ telle que :

$$
f(u) = \frac{1}{2} a(u, u) - l(u)
$$

Alors la fonctionnelle $f$ admet un unique minimum $u$, solution de : 

$$
a(u, v) = l(v), \forall v \in V
$$

$a$ étant une forme bilinéaire coercive, elle est $\alpha$-convexe donc convexe. $f$ est également $\text{s.c.i}$ sur $V$ un fermé convexe. Alors, elle admet un minimum, et ce dernier est unique. $f$ étant convexe, ses minimums locaux sont caractérisés par l'équation d'Euler, c'est-à-dire que $\bar u$ est minimum local de $u \iff D_{\bar u}f = 0 \iff a(\bar u, h) = l(h), \forall h \in V$.

Mettons en pratique sur un exemple :

$$
f(u) = \frac{1}{2} \int_0^1u'(x)^2dx - \int_0^1f(x)u(x)dx
$$

avec $f \in L^2(0, 1)$ et $u \in H^1_0(0,1)$.

On identifie :

$a(u, v) = \int_0^1u'(x)v'(x)dx$

$l(v) = \int_0^1f(x)v(x)dx$

$l$ est continue :

$$
|l(v)| \leq \|f\|_{L^2}\|v\|_{L^2} \leq  \|f\|_{L^2} \|v\|_{H^1_0}
$$

$a$ est continue :

$$
|a(u,v)| = |\int_0^1 u'(x) v'(x) dx| \leq \|u'\|_{L^2} \|v'\|_{L^2} \leq \|u'\|_{H^1_0}\|v'\|_{H^1_0}
$$

$a$ est linéaire, et coercive :

$$
\|u\|_{L^1} \leq C \|u'\|_{L^2} = C |a(u,u)|
$$

par l'inégalité de Poincaré sur toutes les fonctions $u \in H^1_0(0,1)$.

On peut alors affirmer qu'il existe une unique solution $u\in H^1_0(0,1)$ au problème dit variationnel suivant :

$$
\int_0^1u'(x)v'(x)dx = \int_0^1f(x)v(x),  \forall v \in H^1_0(0,1)
$$

**Problème au moindre carré**

Soit $A \in \mathcal{M}_{n,m}(\mathbb R)$ et $b \in \mathbb{R}^n$. On peut voir la matrice $A$ comme un data-frame de $n$ observations pour $m$ features chacune. On souhaite résoudre le problème suivant :

$$
\argmin_{x \in \mathbb{R}^n} \|Ax - b\|
$$

Selon le rang et la forme de la matrice $A$, on va avoir plus ou moins de solutions.
