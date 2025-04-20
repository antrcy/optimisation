## Conditions d'optimalité des problèmes avec contraintes

### Contraintes d'égalité

On s'intéresse aux problèmes suivants :

$$
J : K \subset \mathbb{R}^n \to \mathbb{R} \text{, avec } K = \{x \in V \text{ t.q. } h(x) = 0_p \}
$$

et $h : \mathbb{R}^n \to \mathbb{R}^p$. 

**Remarque :** On suppose un instant que $K$ est un espace vectoriel, où $h_i(x) = \langle a_i , x \rangle$. $K$ est donc un espace convexe fermé (de $V$), et si $x^* \in K$ est un minimum local de $J$ différentiable, alors :

$$
\langle \nabla_{x^*} J, y - x^* \rangle \geq 0
$$

Pour tout $y$ dans $K$. C'est une propriété que l'on a appelé inéquation d'Euler dans le cours précédent. Cependant, puisque $K$ est un espace vectoriel, $w = x^* - y$ est aussi un élément de $K$, ce qui induit :

$$
\langle \nabla_{x^*} J, x^* - y \rangle \geq 0 \implies \langle \nabla_{x^*} J, y \rangle = 0
$$

On écrit alors que $\nabla _{x^*} J$ est orthogonal à $K$, et on peut montrer que $\nabla _{x^*} J \in K^{\perp} = \text{Vec}\{(a_i)_{i = 1 \dots p}\}$. On a finalement :


Soit $\bar x$ est minimum local de $J$ sur $K$, alors

$$

\nabla_{\bar x}f = \sum_{i = 1}^{p} \lambda_i a_i \text{ et } \bar x \in K

$$

ce qui prend généralement la forme d'un système. On suppose généralement que les $a_i$ forment une famille libre d'éléments. Le théorème des extremas liés généralise ce concept.

___

**Le théorème des extremas liés**

_Théorème_ : Soient $J : \mathbb{R}^n \to \mathbb{R}$ et $h_1, \dots h_p : \mathbb{R}^n \to \mathbb{R}$ toutes $\mathcal C^1$ sur $\mathbb{R}^n$. Si $J$ admet un minimum local sur $K = \{x \in \mathbb{R}^n, h_1(x) = \dots = h_p(x) = 0 \}$, et que $\{(\nabla_{\bar x} h_i)_{i = 1 \dots p}\}$ forment une famille libre, alors il existe un p-uplet $(\lambda_1, \dots \lambda_p)$ tel que 

$$
\nabla _{\bar x} f + \sum_{k = 1}^{p} \lambda_k \nabla _{\bar x}h_k = 0
$$

Ce que nous dit ce théorème, c'est que le gradient de la fonction $f$ en un minimiseur sous contrainte appartient à un certain espace vectoriel. Plus spécifiquement, il est colinéaire à un plan, engendré par les gradients des fonction dont les niveaux forment la contrainte.

_Demonstration_ : La première étape est de définir la notion de direction admissible. Formellement, une direction en $x^*$ notée $\vec d$ est dite admissible si $\exists \mu : [0, \tau[ \to V$ une application $\mathcal C^1$ telle que :

1) $\mu(t) \in K, \quad \forall t$

2) $\mu(0) = x^*$

3) $\mu'(0) = \vec d$

C'est une direction qui autorise un déplacement infinitésimal dans $K$. En un point, on va souvent d'intéresser au cône des directions admissibles, c'est-à-dire un espace quasi vectoriel uniquement stable par translation positive.

Ici, il est nécessaire de montrer que l'ensemble :

$$
K(x^*) = \bigcap_{k = 1}^p \text{Vect}(\nabla_{x^*}h_i)^{\perp}
$$

Il est important de remarquer que l'espace ci-dessus est un espace vectoriel en plus d'être un cône, et que donc sur ce dernier l'équation d'Euler est vérifiée en $x^*$. De manière générale, si $x^*$ est effectivement un minimum local, l'inégalité d'Euler est vérifiée sur le cône des directions admissibles en $x^*$.

est le cône des directions admissibles en $x^*$. Soit $\phi$ une application définie par :

$$
\phi : (t, y_1, \dots, y_p) \mapsto h(x^* + t\vec d + y_1 \nabla_{x^*}h_1 + \dots + y_p \nabla_{x^*}h_p)
$$

Cette application vérifie $\phi(0_{p+1}) = h(x^*) = 0$. Pour la suite, on va avoir besoin de rappeler un résultat essentiel d'analyse :

___

_Théorème_ (Fonctions Implicites) : Soient $E, F$ et $G$ trois espaces de Banach et $f \in \mathcal C^1(U)$ avec $U$ un ouvert de $E \times F$ et $f$ à valeurs dans $G$. Soit $(x, y) \in U$ tel que $f(x, y) = 0$ et $D_yf(x, y)$ soit inversible. Il existe donc $\phi \in C^1(V)$ avec $V \subset F$ un voisinage ouvert de $x$, ainsi que $\Omega$ un voisinage ouvert de $(x,y)$ dans $U$ tels que, pout tout $(x,y) \in E \times F$:

$$
(x, y) \in \Omega \text { et } f(x, y) = 0 \iff x \in V \text{ et } y = \phi(x)
$$

En des termes plus profanes, si un point appartient à une ligne de niveau de $f$ et qu'en ce point la différentielle de $f$ soit inversible dans l'une des directions, alors on peut déterminer une voisinage ouvert sur lequel la même ligne de niveau peut s'exprimer comme fonction de la première direction vers la seconde.

___

On détermine alors que :

$$
D_y \phi(0) = (D_{x^*} h)(D_{x^*} h)^t
$$

Or $D_{x^*} h = (\nabla _{x^*} h_1, \dots, \nabla _{x^*} h_p)$ linéairement indépendant par hypothèse. Le produit matriciel plus ci dessus est donc inversible. D'après le théorème des fonctions implicites, $\exists O_1 \times O_2$ voisinage de $0$ et $rho \in \mathcal C^1(O_1)$ tel que :

$$
(t, y) \in O_1 \times O_2 \text { et } \phi(t, y) = 0 \iff t \in O_1 \text{ et } y = \rho(t)
$$

On note $\rho(t) = y(t)$ pour faire simple. Posons alors $\mu(t) = \phi(t, y(t))$. L'application qui précède vérifie les trois hypothèses de la direction admissible. Puisque $K(x^*)$ est bien le cône des directions admissibles, et que $\langle \nabla_{x^*} J, K(x^*) \rangle = 0$ par l'équation d'Euler, $\nabla_{x^*} J \in K(x^*)^{\perp}$.

### Contraintes d'inégalité

On s'intéresse aux problèmes d'optimisation de la forme suivante :

$$
\inf_{x \in K} J(x)
$$

$$
K = \{x \in \mathbb{R}^n, h_1 (x) = \dots h_p(x) = 0 \text{ et } g(x_1) \leq 0, \dots , g_q(x) \leq 0\}
$$

_Théorème_ : On suppose $J, g_i, h_i \in \mathcal C^1$. Si $J$ admet un minimum local sur $K$ noté $\bar x \in K$, alors il existe $\lambda_0, \lambda_1, \dots , \lambda_p \in \mathbb{R}$ et $\mu_1 \dots \mu_q \geq 0$, non tous nuls, tels que :

$$
\lambda_0 \nabla _{\bar x} J + \sum_{i = 1}^p \lambda _i \nabla_{\bar x}h_i + \sum_{i = 1}^q \mu _i \nabla_{\bar x} g_i
$$

On a également que : $\forall i \in \{1, \dots, q\}, \mu_i g_i(\bar x) = 0$.

_Démonstration_ : Le théorème est également appelé condition d'optimalité nécessaire de Fritz-John. Ce résultat et sa démonstration sont relativement récents, car très insipirés de techniques algorithmiques. Afin de le démontrer, on commence par poser les fonctions suivantes :

$$
g_i^{+}(x) = \max\{0, g_i(x)\}
$$

telles que $g_i^{+}(x)^2$ sont différentiables. On procède par pénalisation, en posant les problèmes de minimisation intermédiaires sur les fonctions :

$$
J^k(x) = J(x) + \frac{k}{2} \sum_{i = 1}^p (h_i(x))^2 + \frac{k}{2} \sum_{i = 1}^q (g_i^{+}(x))^2 + \frac{1}{2} \|x - x^*\|^2
$$

On pose $x_k$ le minimum de $J^k$ sur $S = \{x, \quad \|x - x^*\| \leq \epsilon\}$, tel que $J(x^*) \leq J(x)$ sur $S$. On montre ensuite que toutes valeurs d'adhérences de la suite bornée $x_k$ sont égales à $x^*$, ce qui permet d'affirmer que $\lim_{k \to \infty} x_k = x^*$. Il existe donc un rang à partir duquel ces minimums sont à l'intérieur de $S$, ce qui permet d'affirmer que, pour tout $k$ supérieurs à ce rang :

$$
0 = \nabla_{x_k} J^k
$$

On extrait alors les coefficients suivants :

$$
\lambda_0^k = \frac{1}{\sqrt{1 + \sum kh_i(x_k)^2 + \sum kg_i^{+}(x_k)^2}}
$$

$$
\lambda_i^k = \lambda_0^k h_i(x_k)k
$$

$$
\mu_i^k = \lambda_0^k g_i^{+}(x_k)k
$$

En les rangeant dans un vecteur, on obtient une suite bornée de norme 1 donc convergente, ce qui, en passant à la limite, nous permet de retrouver le résultat voulu.

_Définition_ : Pour les contraintes d'inégalités, de la forme :

$$
K = \{x \in \mathbb{R}^n, g_i(x) \leq 0, \quad \text{pour } 1 \leq i \leq M \}
$$

On dit que l'ensemble $\mathcal I(x) = \{i \in \{1, \dots, M\},\quad g_i(x) = 0\}$ est l'ensemble des indices actifs en $x$. En un point, les contraintes actives rendent la vérification de l'optimalité compliquée, due à la difficulté d'établir un cône de directions admissibles.

**Qualification des contraintes**

On doit donc rajouter des conditions supplémentaires sur nos contraintes pour correctement vérifier l'optimalité d'un point.

_Définition_ : Les contraintes associées au problème de minimisation mixte sont dites qualifiées en $\bar x \in K$ si :

1) $(\nabla_{\bar x} h_i)_i$ sont linéairement indépendants

2) $\exists d \in \mathbb{R}^n$ tel que :
    - $\langle \nabla_{\bar x} h_i , d \rangle = 0$ pour tout $i$;
    - $\langle \nabla_{\bar x} g_j , d \rangle < 0$ pour tout $j \in \mathcal I(\bar x)$ ou $ = 0$ si $g_i$ affine;

Naturellement, $d$ est différent de $0$.

_Propriété_ : Un condition suffisante (mais pas nécessaire) à la qualification est que :

$$
\{\nabla _{\bar x}h_i(x)\}_{1 \leq i \leq p} \cup \{\nabla _{\bar x}g_j\}_{j \in \mathcal I(\bar x)}
$$

est une famille libre. Pour démontrer cela, on range nos vecteurs dans une matrice, on complète la base et on construit un endomorphisme.

_Théorème_ (K.K.T) : Soient $J, h_i, g_j \in \mathcal C^1$. Si $J$ admet admet un minimum local en $\bar x \in K$, défini par :

$$
K = \{x \in \mathbb{R}^n, g_i(x) \leq 0, \quad \text{pour } 1 \leq i \leq M \}
$$

et que les contraintes sont qualifiées, alors $\exists \lambda_1 \dots \lambda_p \in \mathbb{R}$ et $\mu_1, \dots \mu_q \geq 0$ non tous nuls tels que :

$$
\nabla _{\bar x} J + \sum_{i = 1}^p \lambda_i \nabla_{\bar x}h_i + \sum_{i = 1}^q \mu_i \nabla_{\bar x}g_i = 0
$$

et $\mu_j g_j(\bar x) = 0$.

_Démonstration_ : On démontre ce résultat en utilisant le crtière d'optimalité de Fritz-John. Il suffit de montrer que $\lambda_0 \neq 0$. La qualification des contraintes impose l'existence d'un vecteur $\vec d$ tel que $\langle \nabla_{\bar x} h_i, \vec d \rangle = 0$ et $\langle \nabla_{\bar x} g_i, \vec d \rangle < 0$. Donc $\langle \sum_{i = 1}^q \mu_i \nabla_{\bar x}g_i, \vec d \rangle = 0 \implies \mu _i = 0,\quad \forall i \implies \sum_{i = 1}^p \lambda_i \nabla_{\bar x}h_i = 0$ ce qui vient contre-dire le critère d'indépendance.

Si toutes les contraintes sont affines, alors soit tous les multiplicateurs de Lagrange sont nuls ce qui n'est pas possible, soit le problème est mal posé et des contraintes sont redondantes.

**Autres critères de qualification**

1) _Linéarité_ : Si toutes les contraintes sont issues de fonctions affines, les contraintes sont qualifiées en tout point. En effet, les contraintes d'égalité sont soit toutes indépendantes soit redondantes, et il suffit de prendre $d = 0$ pour conclure. 

2) _Convexité_ : Si, en $\bar x$, la famille $(\nabla_{\bar x}h_i)_i$ est libre, et que les fonctions $g_j$ sont convexes, alors les contraintes sont qualifiées s'il existe $v \in \mathbb{R}^n$ tel que :
    - $g_j(v) < 0$;
    -  OU : $g_j(v)$ = 0 et $g_j$ affine.

Ce, pout tout $j$, donc pas que pour les contraintes actives. Cette dernière condition implique en fait la condition de qualification vue plus tôt. Puisque $g_j$ sont convexes, les contraintes d'inégalité se ramènent à l'optimisation sur un convexe, car les sous ensembles de niveau de fonctions convexes sont des espaces convexes. On a alors :

$$
0 > g_j(v) \geq g_j(x^*) + \langle \nabla_{x^*} g, v - x^* \rangle \geq \langle \nabla_{x^*} g, v - x^* \rangle
$$

Et on prend $\vec d = v - x^*$. On remarque que $v$ est un élément de l'intérieur, il n'est pas suprenant qu'une direction admissible soit donc sa destination.