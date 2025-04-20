_"Analyse Numérique et Optimisation"_ - Grégoire Allaire


### Introduction : optimalité sur des convexes

On va s'intéresser à des conditions nécessaires d'optimalité sur des ensembles convexes pour commencer, puis sur des espaces définis par des contraintes (inégalité, égalité, mixte). Jusqu'à nouvel ordre, on suppose un ensemble $K$ fermé, non vide et $J$ une fonction continue sur un ouvert $U$ contenant $K$.

Les ensembles convexes offrent un cadre idéal pour étudier l'optimalité de ses points. L'idée clée est d'étudier le comportement de $J$ lorsque l'on se déplace dans des directions dites admissibles autour d'un certain point. Un outil fondamental qui nous servira à carctériser des extremas locaux de $J$ sur $K$ est l'inégalité d'Euler.


Pour $u \in K$ convexe, avec $J$ différentiable en $u$; si $u$ est un minimum local de $J$ sur $K$, alors :

$$
\langle \nabla_u J, v - u \rangle \geq  0, \quad \forall v \in K
$$

La réciproque est vérifiée si $J$ est également convexe. A noter que la preuve n'est pas fondamentalement différente si on remplace notre produit scalaire avec un gradient par simplement une différentielle (souvent le cas en dimension infinie).

Bon déjà, qu'est ce qu'on entend par minimum local de ? La définition la plus évidente est de faire correspondre à $u$ l'existence d'un voisinage ouvert sur lequel $u$ est un minimum global. Si on optimise par sur un ouvert, il faut choisir une partie de $K$ convexe intersectée avec notre voisinage d'intérêt.

Un cas d'égalité important est le cas où $K - u$ est un espace vectoriel ou si $u$ appartient à l'intérieur de $K$, que l'on suppose donc non vide. 

___

_Applications_ : 

**Algèbre** - 
L'inégalité d'Euler offre une caractérisation intéressante du projeté orthogonal dans un espace de Hilbert. Pour $K$ fermé non vide, on note $x_K$ le projeté orthogonal de $x$ sur $K$. Alors :

$$
\langle x_K - x , x_K - y \rangle \leq 0
$$

Pour tout $y$ dans $K$.


**Forme variationnelle** -
On s'intéresse au problème de minimisation de l'énergie :

$$
\inf_{H^1_0(\Omega)} J(v) = \frac{1}{2} \int_{\Omega} |\nabla v|^2 dx - \int_{\Omega} fvdx
$$

Il est possible de montrer que $J$ est coercive (inégalité de Poincarré), continue et convexe sur un fermé convexe. Elle admet donc un minimum. Les minimums locaux de $J$ sont donc caractérisés par l'égalité d'Euler :

$$
\nabla _{\bar v} J = 0
$$

Ce qui se réécrit :

$$
\int_{\Omega} \langle \nabla u, \nabla v \rangle dx = \int_{\Omega} fvdx 
$$

Et on sait par Lax-Milgram que ce problème admet une unique solution. Le problème de minimisation de l'énergie est donc analogue à la formulation variationnelle. En d'autres termes, la formulation variationnelle nous permet d'obtenir des solutions qui minimisent leur énergie.

___


On va s'intéresser maintenant à un cas particulier que nous généraliserons plus tard. Admettons que $K$ soit un cône convexe, c'est-à-dire que $\forall v \in K$, $\lambda v \in K$, pour tout scalaire $\lambda$ positif ou nul. Il est également convexe, ce qui en fait un cône plein. On suppose aussi qu'il est fermé (pas automatique). L'inéquation d'Euler devient :

$$
\langle \nabla_{\bar u} J , v - \bar u \rangle \geq 0
$$

pour tout $v \in K$. Mais puisque $\bar u \in K$, on a :

$$
\langle \nabla _{\bar u} J, \bar u \rangle = 0
$$

Ce qui est naturel si on se rappelle de la structure de $K$. C'est un cône qui part de 0 vers l'infini. Cela induit naturellement que :

$$
\langle \nabla _{\bar u} J, v \rangle \geq 0 
$$

Pour tout $v$ dans le cône $K$. Les problèmes d'optimisation nous amène à considérer des cônes particuliers de la forme :

$$
K = \{v \in V, \langle a_i, v \rangle \leq 0, i = 1 \dots M \}
$$

On montre facilement que $K$ est un cône convexe. $\bar u \in K$ est donc un minimum local de $J$ sur $K$ si :

$$
\langle \nabla _{\bar u} J, v \rangle \geq 0 \quad \forall v \in K
$$

Le lemme de Farkas, que nous expliciterons plus tard, nous permettra d'affirmer l'existence de **multiplicateurs de Lagrange** $\lambda_i$ tels que :

$$
\nabla_{\bar u} J + \sum_{i = 1}^M \lambda_i a_i = 0
$$

avec comme corollaire $\lambda_i \langle a_i , \bar u \rangle = 0$.

### Les multiplicateurs de Lagrange

Dans la suite, $K$ n'est plus forcément convexe. On lui attribut dependant une structure particulière : il est défini par des contraintes d'égalités, d'inégalités, ou même les deux. C'est embêtant : il devient difficile d'évaluer l'optimalité d'un point sur $K$, puisqu'on ne peut plus se déplacer vers aucun point de $K$. Pour pallier à cela, on va définir un nouvel objet qui nous permettra de retrouver un semblant de convexité là où on avait arrêté d'espérer.

Soit $v \in K$; On appelle cône des directions admissibles le cône définir par :

$$
K(v) = \{w \in V : \exists v_n \in K^{\mathbb N} , \exists \epsilon_n > 0 \text{ tel que } \lim v_n = v \text { et } \lim \epsilon_n = 0 \text{ et } \lim \frac{v_n - v}{\epsilon _n} = w\}
$$

Un vecteur de $K(v)$ est donc un vecteur de $K$ qui autorise un déplacement infinitésimal depuis $v$ de sorte à rester dans $K$. Il s'agit du cône des directions tangentes à $K$ en $v$. On montre facilement qu'il s'agit d'un cône.

On obtient alors une version plus générale de l'inégalité de d'Euler sur des cônes de direction admissible. Soit $\bar u$ un minimum local sur $K$ de $J$ différentiable en $\bar u$. Alors :

$$
\langle \nabla _{\bar u} J, w \rangle \geq 0 \quad \forall w \in K(\bar u)
$$

Les cônes admissibles sont des ensembles difficiles à expliciter, comme on l'a vu. On va chercher à les caractériser dans des cas spécifiques : $K$ est définie par des contraintes d'inégalité ou d'égalité.

**Contraintes d'égalité :**

On suppose que :

$$
K = \{v \in V \text{ tel que } F(v) = 0\}
$$

Avec $F$ différentiable sur un ouvert contenant $K$ à valeurs dans $\mathbb{R^d}$. On suppose que les vecteurs $(\nabla_{\bar u} F_i)_i$ sont linéairement indépendants. Si $\bar u$ est un minimum local de $J$ sur $K$, alors il existe des multiplicateurs de Lagrange $\lambda_i$ tels que :

$$
\nabla _{\bar u} J + \sum_{i = 1}^d \lambda_i F_i = 0
$$

L'indépendance linéaire des gradients permet d'établir par le théorème des fonctions implicites que le cône des directions admissibles en $\bar u$ est donné par :


$$
K(\bar u) = \{w \in V \quad \langle \nabla_{\bar u} F_i, w \rangle = 0\} = \bigcap_{i = 1}^d (\nabla_u F_i)^{\perp}
$$

Il est donc possible de se déplacer dans le plan orthogonal à l'espace engendré par les gradients $F_i$. Quand on sait que $K$ est un ensemble de niveau, et que les gradients sont orthogonaux aux lignes de niveau, ce n'est pas si surprenant.

**Contraintes d'inégalité**

$$
K = \{v \in V \text{ tel que } F_i(v) \leq 0\}
$$

On se doute qu'il va être significativement plus compliqué de caractériser le cône des directions admissibles. $K$ n'a plus la tête d'un ensemble de niveau, mais plus l'aspect de l'intersection de sous ensembles de niveaux, qui peut s'avérer convexe si les $F_i$ le sont. Mais dans le cas général, il est compliqué de savoir dans quelle direction on peut se déplacer.

On suppose $\bar u$, on veut déterminer le cône. Si $F_i(\bar u) < 0$ c'est simple : on peut se déplacer dans toutes les directions. Mais si $F_i(\bar u) = 0$, le critère risque de ne plus être très général.

On note $I(\bar u)$ l'ensemble des indices des contraintes actives de $\bar u$, c'est-à-dire sur le bord. Les contraintes actives n'ont pas forcément une direction commune dans laquelle on peut se déplacer. On va donc introduire la notion de contrainte qualifiée :

On dit que les contraintes sont qualifiées en $\bar u$ si :
$$
\exists \bar w \in V \text{ t.q. } \forall i \in I(\bar u) :
$$

$$
\langle \nabla_{\bar u} F_i , \bar w \rangle < 0
$$

OU :

$$
\langle \nabla_{\bar u} F_i , \bar w \rangle = 0  
$$

Si $F_i$ est affine. Ainsi, si toutes les $F_i$ sont affines, le dernier cas devient trivial et il suffit de prendre $\bar w = 0$ pour conclure que les contraintes sont toujours qualifiées. Ce n'est pas très compliqué à voir si on s'imagine l'intersection de demi-plans.

_Théorème :_ Soient $J, F_i$ différentiables en $\bar u$ et à contraintes qualifiées en $\bar u$. Si $\bar u$ est un minimum local de $J$ sur $K$, alors il existe des multiplicateurs de Lagrange $\lambda_i \geq 0$ tels que :

$$
\nabla _{\bar u} J + \sum_{i = 1}^d \lambda_i \nabla _{\bar u}F_i = 0
$$

avec $\lambda_i F_i(\bar u) = 0$.

**Remarques** :

- Le fait que les multiplicateurs soient positifs devrait rappeler la définition d'un cône. Si on prend le cône formé par tous les gradients $F_i$, le gradient de $J$ doit y appartenir.

- Le dernier point est appelé conditions de complémentarité des contraintes. Il exprime le fait que si $F_i(\bar u) < 0$, alors le gradient de $J$ s'annule dans cette direction. C'est analogue à l'égalité d'Euler, et on voit bien que si tous les $\lambda_i$ sont nuls, alors le gradient s'annule parce qu'on est sur un ouvert.

On va détailler ici le schéma de la preuve, très formatrice. On commense par poser :

$$
\tilde{K}(v) = \{w \in V : \langle \nabla_{\bar u} F_i, w \rangle \leq 0, \forall i \in I(\bar u)\}
$$

Il s'agit d'un cône, sans trop de suspense. Posons $\bar w$ un vecteur qui satisfait la condition de qualification des contraintes, et soit $w$ un vecteur de $\tilde{K}$. On va montrer que pour tout $\delta > 0$ :

$$
\bar u + \epsilon (w + \delta \bar w) \in K
$$

et ce pour tout $\epsilon$ suffisamment petit. Cela revient à discuter les différents cas de $F_i$ (active ou non, affine). L'espace $\{\bar u + \delta \bar w + \tilde{K}(\bar u)\}$ devient alors un cône de directions admissibles partant de $\bar u \delta \bar w$, et ce pour tout $\delta > 0$. On sait par l'inégalité d'Euler généralisée que :

$$
\langle \nabla_{\bar u}J, \bar u + \delta \bar w + w - \bar u \rangle = \langle \nabla_{\bar u}J, \delta \bar w + w \rangle \geq 0
$$

pour tout $w \in \tilde{K}(\bar u)$. Par continuité du produit scalaire, ceci induit que :

$$
\langle \nabla_{\bar u}J, w \rangle \geq 0
$$

pour tout $w \in \tilde{K}(\bar u)$. L'astuce ici était de commencer par faire un déplacement d'amplitude arbitraire dans la direction de "désactivage", de sorte à ce que nos contraintes soient inactives. De là, en partant de $\tilde{K}(\bar u)$ on pouvait définir un cône convexe translaté dans l'ensemble des contraintes actives.

On conclue la preuve en appliquant le lemme de Farkas :

$a_1, \dots , a_M \in V$;

$K = \{v \in V : \langle a_i, v \rangle \leq 0\}$

$\hat K = \{v \in V : \exists \lambda_i \geq 0 \quad v = - \sum_{i = 1}^M \lambda_i a_i\}$

Alors, $\forall p \in V$, 

$$
\langle p , w \rangle \geq 0 \quad  \forall w \in K \implies p \in \hat K
$$

Ce que nous dit le lemme de Farkas, c'est que si un vecteur pointe dans la même direction qu'un ensemble de vecteur qui pointe dans la direction opposée aux vecteurs $a_i$, alors il est combinaison linéaire des vecteurs $a_i$ dans leur orientation d'origine.