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

On appelle l'équation l'inégalité d'Euler. C'est un résultat extrêmement puissant, surtout sachant qu'on est sur un espace de Hilbert. Intuitivement, l'inégalité exprime le fait que $f$ est croissante dans toutes les directions permises par $K$. C'est notamment intéressant si on s'intéresse à des minimas au bord d'un fermé par exemple.

La démonstration de ce résultat repose essentiellement sur le fait que $K$ est convexe. On choisit alors un voisinage de $\bar x$ dans $K$, par exemple une boule telle qu'intersectée avec $K$ donne un voisinage sur lequel $\bar x$ est minimiseur local.

L'équation d'Euler est seulement nécessaire en général. En revanche, elle est suffisante pour $f$ en plus convexe. En effet, par convexité, $f(y) \geq f(\bar x) + D_{\bar x}f(y-\bar x)$, et ce pour tout $y$ de $K$.

_Proposition_ : (Minimisation sur un ouvert) Soit $f:K \subset V \to \mathbb R$. Si $f$ admet un minimum local en $\bar x \in \mathring K$, alors $D_{\bar x} f = 0$.

La démonstration est un petit peu astucieuse, mais finalement intuitive. Le fait d'avoir une boule nous permet de prendre un vecteur et son opposé, et donc d'obtenir une différentielle positive pour un vecteur et son opposé.

Cette condition est nécessaire en général. Cependant, en imposant $f$ convexe, on a l'équivalence suivante :

$$
\bar x \text{ est un minimum local de } f \iff D_{\bar x} f = 0
$$

Par convexité, $\bar x$ est en plus un minimum global. Attention, pour cela $\mathring K$ doit être convexe. Sinon déjà la démonstration serait différente, et aussi parce que l'on peut imaginer en dimension 1 des fonctions convexes sur un ouvert, différentiables sur cet ouvert, mais dont les minimum locaux ne font pas forcément globaux. En effet, la non convexité de l'ouvert permet d'imaginer des intervalles ouverts disjoints, sur lesquels $f$ pourrait être constante sur le premier, puis être une hyperbole centrée sur le second.  

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

$f$ est convexe, car sa Hessienne est semi-définie positive (on a d'ailleurs la réciproque). Ainsi, $\bar x$ est minimum $\iff$ $\nabla_{\bar x}f = 0$. Ici cependant, l'existence et l'unicité de la solution du système $Ax = b$ ne peut pas être établie. Si $b \in \text{Im}(A)$, alors le système admet une solution $x_0$. Or puisque $\text{Ker}(A) \neq \{0\}$, il existe $v \neq 0$ tel que $Av = 0$, donc $\forall \lambda \in \mathbb{R}$, $x_0 + \lambda v$ est une solution. La fonction est donc minimisée sur un espace affine, donc convexe, elle est donc constante sur cet espace. Enfin, si $b \notin \text{Im}(A)$, l'équation d'Euler n'admet aucune solution. On rappelle que $\text{Im}(A) = \text{Ker}(A^t)^{\perp}$. Soit $v \neq 0$ tel que $Av = 0$. Alors, $v$ ne peut pas être orthogonal à $b$, puisque cela signifierait que $b \in \text{Im}(A)$ : un sous espace vectoriel et son orthogonal sont en somme directe. Ainsi, quitte à prendre un vecteur colinéaire à $v$, on a : 

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

On rappelle le théorème de Lax-Milgram. Soit $a : V \times V \to \mathbb R$ bilinéaire, continue et coercive, avec $V$ de Hilbert. Soit également $l : V \to \mathbb{R}$ une forme linéaire continue. Soit $f$ telle que :

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
J(u) = \frac{1}{2} \int_0^1u'(x)^2dx - \int_0^1f(x)u(x)dx
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
\|u\|_{L^2} \leq C \|u'\|_{L^2} = C |a(u,u)|
$$

par l'inégalité de Poincaré sur toutes les fonctions $u \in H^1_0(0,1)$.

On peut alors affirmer qu'il existe une unique solution $u\in H^1_0(0,1)$ au problème dit variationnel suivant :

$$
\int_0^1u'(x)v'(x)dx = \int_0^1f(x)v(x),  \forall v \in H^1_0(0,1)
$$

**Problème au moindre carré**

Soit $A \in \mathcal{M}_{m,n}(\mathbb R)$ et $b \in \mathbb{R}^m$. On peut voir la matrice $A$ comme un data-frame de $n$ observations pour $m$ features chacune. On souhaite résoudre le problème suivant :

$$
\text{arg} \min_{x \in \mathbb{R}^n} \|Ax - b\|^2
$$

Selon le rang et la forme de la matrice $A$, on va avoir plus ou moins de solutions. On commence par étudier l'existence d'une solution à ce problème.

Une solution $\bar x$ peut être vue comme le projeté de $b$ sur $\text{Im}(A)$. On peut alors poser $g(y) = \|y - b\|^2$ définie sur $\text{Im}(A)$, continue et coercive sur un fermé. Elle admet donc un minimiseur $y_0 \in \text{Im}(A)$, et donc il existe $x_0 \in \mathbb{R}^n$ tel que $Ax_0 = y$ solution.

On montre également que :

$$
\langle \nabla_x^2f(h), h \rangle = 2\|Ah\|^2 \geq 0
$$ 

Donc $J$ est convexe. Puisque $J$ est convexe sur un ouvert, ses minimum locaux sont caractérisés par l'équation d'Euler :

$$
\bar x \text{ un minimum local de } J \iff A^t A \bar x = A^t b
$$

$A^tA$ est inversible si et seulement si le rang de $A$ est égal à $n$, c'est-à-dire que ses colonnes sont linéairement indépendantes. En effet, $A^tA \in \mathcal{M}_{n,n}$. Donc $A^tA$ est inversible si et seulement si $\text{Ker}(A^tA) = \{0\}$, c'est-à-dire $\text{Ker}(A) = \{0\}$ et $\text{Im}(A) \cap \text{Ker}(A^t) = \{0\}$. Or le dernier point est toujours vérifié, car les deux sous espaces sont orthogonaux. Finalement $\text{Ker}(A) = \{0\} \iff \dim(\text{Im}(A)) = n$ (_Théorème du rang_).

On peut discuter de l'unicité et de la forme des solutions selon les dimensions du problème.

_Cas 1_ :

$$A = 
\begin{pmatrix}
  * & * & * & * & * & *\\
  * & * & * & * & * & *\\
  * & * & * & * & * & *
\end{pmatrix}
$$

On a moins d'observations que de features. Il est impossible d'avoir un rang égal à $n$. On aura forcément une infinité de minimiseurs, sur tout un espace affine de solutions $x_0 + \text{Ker}(A)$. Dans le cas où $b \in \text{Im}(A)$, on aura même interpolation (overfitting), c'est-à-dire qu'un minimieur sera solution de $Ax = b$.

_Cas 2_ :
$$A = 
\begin{pmatrix}
  * & * & * \\
  * & * & * \\
  * & * & *
\end{pmatrix}
$$

Il est possible que le rang soit égal à $n$, mais auquel cas le minimiseur (unique) interpollera encore les données. Si le rang est inférieur à $n$, il faut que $b$ soit dans l'image de $A$ pour qu'il y ait interpolation. Sinon, on aura encore un espace affine de solutions du problème de minimisation.

_Cas 3_ :
$$A = 
\begin{pmatrix}
  * & * & * \\
  * & * & * \\
  * & * & * \\
  * & * & * \\
  * & * & * \\
  * & * & *
\end{pmatrix}
$$

Même discours qu'avant. Il est encore possible d'obtenir des solutions interpolantes, mais ici le rang est plus atteignable en pratique.
