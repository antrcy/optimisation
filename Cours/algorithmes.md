## Méthodes Numériques

### Optimisation sans contrainte

On s'intéresse maintenant au développement et à l'étude de méthodes numériques d'approximation pour les problèmes de minimisation sans contraintes de la forme :

$$
\min_{x \in K} J
$$

Une méthode est dite convergente si :

$$
\lim_{k \to \infty} J(x_k) = \min J
$$

_Définition_ : (Ordre de convergence)
On dit qu'une méthode est d'ordre $\alpha > 0$ si $\alpha$ est le plus grand réel tel que $\exists c > 0$ tel que :

$$
\|x_k - \bar x \| \leq c \|x_k - \bar x\|^{\alpha}
$$

Avec $\bar x = \argmin J$.

#### Algorithmes sans gradients

On présente ici des algorithmes qui ne nécessitent pas la connaissance d'une différentielle.

1) _Algorithme de la Dichotomie_

On suppose une fonction $J : \mathbb{R} \to \mathbb{R}$, continue et uninominale. 

```
Données: J continue sur [a, b]

Tant que (b - a) > eps:
    x, y dans [a, b]
    
    Si J(x) <= J(y):
        b = y 
    Sinon:
        a = x

Renvoie a, b
```

Implémentation python :

```python
import numpy as np

def dichotomie(J, a, b, eps, maxiter):

    b_k, b_kp = b 

    while (b_k - a_k) => eps and it <= maxiter:
        x = np.random.uniform(a_k, b_k)
        y = np.random.uniform(x, b_k)

        if J(x) <= J(y):
            b_k = y
        else:
            a_k = x

    return a, b
```

Dans l'idéal, on aimerait que l'intervalle $a_k, b_k$ diminue d'une certaine propostion à chaque itération, de sorte que :

$$
b_{k+1} - a_{k+1} = \rho (b_k - a_k)
$$

Pour cela, on choisit $x$ et $y$ tels que :

$$
\begin{align}
    x_k &= a_k + (1 - \rho) (b_k - a_k) \\
    y_k &= a_k + \rho(b_k - a_k)
\end{align}
$$

avec $\rho \in ]1/2, 1[$.

_Suite dorée_ : L'algorithme présenté jusqu'ici nécessite deux évaluations de $J$ par itération. On aimerait se contenter d'une seule par itération, en recyclant une borne qui n'a pas été choisie. En effet, si on prend $b_{k+1} = y_k$, cela induit que le minimum recherché est entre $a_k$ et et $y_k$, et on souhaiterait que $y_{k+1} = x_k$. Cela revient à chercher $\rho$ tel que $\rho^2 + \rho - 1 = 0$, donc $\rho = \frac{-1 + \sqrt{5}}{2} \in ]1/2, 1[.$ On peut alors réécrire l'algorithme comme suit :

```
Données: J continue sur [a, b]

rho = (-1 + sqrt(5))/2

x = a + (1 - rho) * (b - a)
y = a + rho * (b - a)

Jx = J(x)
Jy = J(y)

Tant que (b - a) > eps :
    Si Jx <= Jy:
        b = y
        y = x
        x = a + (1 - rho) * (b - a)
        Jy = Jx
        Jx = J(x)
    Sinon:
        a = x
        x = y
        y = a + rho * (b - a)
        Jx = Jy
        Jy = J(y)

Renvoie b, a
```

#### Algorithmes de descente

On souhaite maintenant determiner des itérés de la forme :

$$
x_{k+1} = x_k + s_k d_k
$$

avec $d_k \in \mathbb{R}^n$ la direction, et $s_k$ le pas. On détermine alors $d_k$ de sorte que :

$$
\langle \nabla_{x_k}J , d_k \rangle \leq 0
$$

afin que pour $s_k$ suffisamment petit, $J(x_{k+1}) \leq J(x_k)$.

On esquisse une première version de l'algorithme :

```
Données: J continue, x0
x = x0

Tant que <critère d'arrêt>:
    Calculer dk, sk
    x = x + sk * dk
```

C'est l'algorithme de descente le plus rudimentaire. Les critères d'arrêt possibles sont les suivants :

1) Itérations maximales

2) $\|x_{k+1} - x_k\| \leq \epsilon (1 + \|x_k\|)$

3) $\|\nabla_{x_k}J\| \leq \epsilon$

4) $\|\nabla_{x_k}J - \nabla_{x_{k+1}}J\| \leq \epsilon (1 + \|\nabla_{x_k}J\|)$

___

1) _Descente de gradients_ :

Un choix possible :

$$
d_k = -\nabla_{x_k}J
$$

et $s_k$ choisi de manière à minimiser $J(x_k + s d_k)$.

_Proposition_ : Si $J$ est $\alpha$-convexe et $\mathcal C^1$, alors la méthode de gradient à pas optimal converge nécessairement.

Dans le cas d'une fonctionnelle quadratique - nécessairement $\alpha$-convexe en dimension finie - le pas optimal peut être explicité :

$$
s_k = \frac{\|d_k\|^2}{\langle Ad_k, d_k \rangle}
$$

Sinon, un pas optimal peut être approché après quelques itérations de la méthode de dichotomie.

_Proposition_ : La méthode de gradient à pas constant converge si $J$ est $\alpha$-convexe, $\mathcal C^1$, avec $\nabla_x J$ $M$-Lipscitzienne, pour $s \in ]0, 2 \frac{\alpha}{M^2}$[.

_Démonstration_ : On remarque que sous ces hypothèses, Il suffit de montrer que 

$$
\|x_{k+1} - \bar x\|^2 \leq (1 - 2s_k \alpha + s_k^2M^2)\|x_k - \bar x\|^2
$$

avec $\nabla_{\bar x} J = 0$ (unique). 

2) _Gradients conjugués_ :

On considère la fonctionnelle $J : \mathbb{R}^n \to \mathbb{R}$ définie par $x \mapsto \frac{1}{2} \langle Ax, x \rangle - \langle x, b \rangle$. On considère la méthode itérative suivante :

$$
x_{k+1} = x_k + s_k d_k
$$

Avec $d_k = \nabla_{x_k}J + \beta_{k - 1} d_{k - 1}$ et $s_k = \frac{\langle d_k,  - \nabla_{x_k} J \rangle}{\langle d_k, Ad_k\rangle}$. On choisir $\beta_{k-1}$ tel que $\langle d_k, Ad_{k-1} \rangle = 0$. Il est possible de montrer que $\beta_k = \frac{\|\nabla_{x_{k+1}} J \|^2}{\|\nabla_{x_k} J\|^2}$.

_Proposition_ : Pout tout $k \leq n - 1$, $x_{k+1}$ minimise $J$ sur $\text{Vect}(d_0, \dots d_k)$, et les directions de descente $d_0, \dots d_{k+1}$ sont $A$-conjuguées, soit orthogonales pour le produit scalaire engendré par $A$. On en déduit que $\bar x = x_n$ : la méthode converge en au plus $n$-itérations.

3) _Algorithme de Newton_ : 

L'algorithme de Newton permet de résoudre une équation non linéaire de la forme $F(x) = 0$ avec $F : \mathbb{R}^n \to \mathbb{R}^n$, en supposant que $D_x F$ est inversible au voisinage du zéro. Chaque itéré est solution d'une équation linéaire où l'on a remplacé $F$ par son approximation linéaire autour de l'itéré précédent. Ainsi, $x_{k+1}$ est solution de :

$$
F(x_k) = D_{x_{k}} F (x - x_k) = 0
$$

Ainsi :

$$
x_{k+1} = x_k - D_{x_k} F^{-1} F(x_k)
$$

L'idée est en fait d'appliquer cet algorithme à la résolution de l'équation d'Euler $\nabla _x J = 0$. La méthode itérative devient donc :

$$
x_{k+1} = x_k + d_k \text{ avec } d_k = -\nabla_{x_k}^2J ^{-1} \nabla_{x_k}J
$$

_Remarques_ :

1) $x_{k+1}$ est le minimum de l'approximation quadratique locale de $J$ (développement de Taylor à l'ordre 2).

2) Si l'inverse de la Hessienne en $x_k$ est positive, $d_k$ est bien une direction de descente, au sens où :

$$
\langle d_k, \nabla_{x_k}J \rangle \leq 0
$$

_Proposition_ : On suppose $F$ de classe $\mathcal C^2$ et $\bar x$ un zéro régulier de $F$, tel que $F(\bar x) = 0$ et $D_{\bar x} F$ inversible. Alors, il existe un réel $\epsilon > 0$ tel que $\forall x_0 \in \mathbb{R}^d$, $\|\bar x - x_0 \| \leq \epsilon$, la méthode de Newton converge vers $\bar x$ et $\exists C > 0$ tel que :

$$
\|x_{k+1} - \bar x \| \leq C \|x_k - \bar x\|^2
$$

La méthode est d'ordre quadratique localement. 

3) _Algorithme de Quasi-Newton_ :

La matrice Hessienne peut être coûteuse à calculer, on même inconnue. On préfère donc utiliser une approximation, avec des itérés de la forme :

$$
x_{k+1} = x_k - s_k W_k \nabla_{x_k} J
$$

avec $W_k$ symétrique, qui consistue une approximation de la Hesienne :

$$
(*) \quad W_k (\nabla_{x_k} J - \nabla_{x_{k-1}}J)=x_k - x_{k-1}
$$

Il s'agit du développement limité au premier ordre du gradient autour de $x_{k-1}$ :

$$
\nabla_{x} J = \nabla_{x_{k-1}}J + \nabla^2_{x_{k-1}}J(x - x_{k-1}) + o(\|x - x_{k-1}\|)
$$

La méthode BFGS consiste à choisir pour $W_k$ la matrice qui minimise l'écart avec $W_{k-1}$ :

$$
W_{k} = \argmin_{W \in S_n, W(\delta _J) = \delta _x} \|W - W_k \|^2_F
$$

Avec $\delta _x = x_k - x_{k-1}$ et $\delta _J = \nabla_{x_k} - \nabla_{x_{k-1}}J$, c'est-à-dire $W$ vérifie $(*)$.

___

**Norme de Frobenius** : $A \in \mathcal M_n(\mathbb{R}^n)$,

$$
\|A\|_F = \text{Tr}(AA^T)
$$

___

On obtient l'expression suivante :

$$
W_k = AW_k A^T + \frac{\delta_x \otimes \delta_x}{\langle \delta_x, \delta_J \rangle}
$$

$$
A = \text{Id} - \frac{\delta_x \otimes \delta_J}{\langle \delta_x, \delta_J \rangle}
$$

Une propriété intéressante est que $W_k$ reste définie positive à chaque itération.


### Optimisation avec contraintes

On présente ici des méthodes d'optimisation numérique sous contraintes de type mixte. On remarquera qu'elles consistent en fait à se ramener à des problèmes sans contraintes.

1) _Algorithme de pénalisation_ :

On considère le problème sans contraintes suivante :

$$
\min J(x) + \frac{1}{\epsilon} \alpha(x)
$$

avec $\alpha : \mathbb{R}^n \to \mathbb{R}$ une fonction continue, positive, et nulle sur l'espace des contraintes. Typiquement, on considère les contraintes suivantes :

$$
\begin{align}
    \alpha (x) &= \|h(x)\|^2 \\
    \alpha (x) &= \|g^+(x)\|^2
\end{align}
$$

avec $\epsilon$ assez petit.

_Proposition_ : Soit $J$ continue coercive, $K$ fermé non vide. On a existence d'un minimum sur $K$. On suppose que $\alpha$ est continue, positive et nulle **uniquement** sur $K$. Alors :

- $\forall \epsilon > 0$, $J_{\epsilon}(x) = J(x) + \frac{1}{\epsilon} \alpha(x)$ admet au moins un minimum (toujours coervice continue) noté $x_{\epsilon}$.

- $(x_{\epsilon})$ est une suite bornée.

- Toute sous-suite convergente de $(x_{\epsilon})$ converge vers un minimum de $J$ sur $K$.

La preuve est sensiblement la même que la technique de pénalisation utilisée pour déterminer l'existence de multiplicteurs de Lagrange pour les problèmes à contraintes mixtes.

2) _Gradient projeté_ :

On suppose $K$ est un convexe fermé - en général une condition nécessaire à la bonne définition d'une projection. On se déplace dans la direction opposée au gradient, et on reprojette dans l'espace des contraintes :

$$
x_{k+1} = P_K (x_k - s_k \nabla_{x_k} f)
$$

$$
P_K(x) = \argmin_{y \in K} \|y - x\|
$$

On rappelle la charactérisation de la projection :

$$
P_K(x) \in K \text { et } \langle s - P_K(x), y - P_K(x) \rangle \leq 0, \quad \forall y \in K
$$

Cela nécessite de connaître l'opérateur de projection. Pour un pavé de la forme $[a_1, b_1] \times \dots \times [a_n, b_n]$ :

$$
P_K(x) = \max\{a_i, \min \{b_i, x\}\}
$$

_Proposition_ : Si $J$ est convexe, $\mathcal C^1$ et $\nabla J$ est $M$-Lipschitzien, alors en prenant le pas $s \in ] 0, 2 \alpha / M^2 [$, la méthode de gradient projeté converge linéairement.

_Démonstration_ : Laissée en exercice. Pas évidente.

3) _Algorithme d'Uzawa_ :

L'algorithme d'Uzawa consisite à déterminer un point selle du Lagrangien. Défini sur un ouvert, un point selle du Lagrangien correspond à un minimum global de $J$. Pour cela, on considère les problèmes accessoires suivants :


$$
\begin{cases}
    \text{P1} : \min_{x \in \mathbb{R}^n} \mathcal{J(x)} \text { avec } \mathcal J(x) = \max_{(\lambda, \mu) \in \mathbb{R}^p \times \mathbb{R}_+^q} L(x, \lambda, \mu) \\

    \text{P2} : \max_{(\lambda, \mu) \in \mathbb{R}^p \times \mathbb{R}_+^q} \mathcal{G} (\lambda, \mu) \text{ avec } \mathcal{G}(\lambda, \mu) = \min_{x \in \mathbb{R}^n} L(x, \lambda, \mu)
\end{cases}
$$

La solution du problème dual $(\text{P2})$ est toujours plus petite que celle du problème primal $(\text{P1})$. En effet :

$$
\max_{(\lambda, \mu) \in \mathbb{R}^p \times \mathbb{R}_+^q} \mathcal{G} (\lambda, \mu) = \max_{(\lambda, \mu) \in \mathbb{R}^p \times \mathbb{R}_+^q} \min_{x \in \mathbb{R}^n} L(x, \lambda, \mu) \leq \min_{x \in \mathbb{R}^n} \max_{(\lambda, \mu) \in \mathbb{R}^p \times \mathbb{R}_+^q} L(x, \lambda, \mu) = \min_{x \in\mathbb{R}^n} \mathcal J(x)
$$

_Théorème_ : Soit $(\bar x, \bar \lambda, \bar \mu)$ un point selle si et seulement si $\bar x$ est solution du problème dual et $(\bar \lambda, \bar \mu)$ est solution du problème dual, et $\mathcal G(\bar \lambda, \bar \mu) = J(\bar x)$.

Le principe d'Uzawa consiste à résoudre le problème dual sous contraintes puis primal sans contraintes, et ce simultanément.

**Problème dual**:

On peut faire une descente de gradient classique dans la direction non contrainte :

$$
\lambda_{k+1} = \lambda_k + s\nabla_{\lambda} \mathcal G (\lambda_k, \mu_k)
$$

Et une descente de gradient projetée dans la direction contrainte :

$$
\mu_{k+1} = P_{\mathbb{R}^q_+}(\mu_k + s \nabla_{\mu} \mathcal{G}(\lambda_k, \mu_k))
$$

Avec pour finir quelques itérations pour déterminer l'itéré en $x$ :

$$
x_{k+1} = \argmin_{x \in \mathbb{R}^n} L(x, \lambda_{k+1}, \mu_{k+1})
$$

Comment calculer $\nabla_{\lambda, \mu} \mathcal G $ au juste ?

$$
\partial_{\lambda_i}\mathcal G(\lambda, \mu) = \partial_{\lambda_i} \min_{x \in\mathbb{R}^n} L(x, \lambda, \mu) = \partial_{\lambda_i} L(x_{\lambda, \mu}, \lambda, \mu)
$$

$$
= \nabla_x L(x_{\lambda, \mu}, \lambda, \mu)^T \partial_{\lambda_i} x_{\lambda, \mu} + \partial_{\lambda_i} L(x_{\lambda, \mu}, \lambda, \mu) = h_i(x_{\lambda, \mu})
$$

L'autre direction se calcule de la même manière. 

_Théorème_ : Soit $J$ $\alpha$-convexe, différentiable, avec $h_i$ affine, $g_i$ convexe $C$-Lipschitzienne. Si un point selle existe, alors l'algorithme d'Uzawa converge vers ce dernier si $s \in ]0, 2 \alpha / C^2[$.