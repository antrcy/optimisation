## Infimum et suite minimisante

La formulation classique d'un problème d'optimisation :
$$
\text{Inf}_{x \in K} J(x)
$$

Avec $J$ scalaire, et $K \subset V$. Ce problème à toujours une solution. De plus, il existe toujours une suite $(x_n)_n$ dite minimisante telle que :

$$
J(x_n) = y_n \rightarrow \text{Inf}_{x \in K} J(x)
$$

Une question générale est de savoir si une telle suite converge ou encore si on peut l'expliciter.

## Rappels de calcul différentiel

_Definition_ : Soit $f : U \subset E \rightarrow F$ une fonction scalaire. On dit que $f$ est différentiable en $x$ si :

$$
\exists L \in \mathcal{L}(E, F) \text{ tel que } \lim_{h \rightarrow 0} \frac{f(x+h) - f(x) - L(h)}{\|h\|} = 0
$$

On écrit aussi que :

$$
|f(x + h) - f(x) - L(h)| = o(\|h\|)
$$

L'application qui à $x$ associe $L$ la différentielle de $f$ en $x$ est notée $\text{df}$ telle que :

$$
\text{df}: x \mapsto D_x f \in \mathcal{L}(E, F)
$$

_Definition_ : Soit $v$ un vecteur de $U$, on appelle la dérivée directionnelle de $f$ en $x$ dans la direction $v$ :

$$
\frac{\partial f}{\partial v} = \text{lim}_{t \rightarrow 0} \frac{f(x + tv) - f(x)}{t} = D_x f(v)
$$

**Implications**

$$
f \in \mathcal{C}^1 \implies f \text{ est différentiable} \implies \frac{\partial f}{\partial v} \text{ existe pour tout } v \in E
$$

_Definition_ : On dit que $f$ est deux fois différentiable si la différentielle de $f$ est différentiable, c'est-à-dire si il existe $D^2 _x f \in \mathcal{L}(E, \mathcal{L}(E, F))$ telle que :
$$
\text{df}(x + h) = \text{df}(x) + D^2 _x f(h) + o(||h||)
$$

On note aussi :

$$
D_{x+h} f = D_x f + D^2 _x f(h) + o(||h||)
$$

Que l'on peut évaluer en $k$ un vecteur de $U$:

$$
D_{x+h} f(k) = D_x f(k) + D^2 _x f(h)(k) + o(||h||)
$$

On a donc 
$$
D^2 _x f(h)(k) = \frac{\partial^2 f}{\partial h \partial k}(x)
$$

___

**Formule de Taylor-Young généralisée** : Si $f$ est deux fois différentiable, alors :
$$
f(x+h) = f(x) + D_xf(h) + \frac{1}{2} D^2 _x f(h)(h) + o(||h||^2)
$$

**Rappels de continuité**

1) $l:E \rightarrow F$ linéaire est continue si $\exists M > 0$ tel que :

$$
||l(x)|| \leq M||x|| \quad \forall x \in E
$$

2. $l:E \times E \rightarrow F$ bilinéaire est continue si $\exists M > 0$ tel que :

$$
||l(x,y) \leq ||x|| \cdot ||y|| \quad \forall x,y \in E
$$


### Cas spécifique des fonctions scalaires


On suppose désormais $f:V \rightarrow \mathbb{R}$ et $V$ un espace de Hilbert. D'après le théorème de Riesz, il existe un unique $g \in V$ tel que :
$$
D_x f(h) = \langle g,h \rangle \in \mathcal{L}(V,\mathbb{R})
$$
On peut alors écrire :
$$
f(x+h) = f(x) + \langle g,h \rangle + o(||h||)
$$
On peut alors définir le gradient de $f$ en $x$ comme étant $g$ :
$$
\nabla f(x) = g
$$
On peut alors réécrire le développement de Taylor au premier ordre:
$$
f(x+h) = f(x) + \langle \nabla f(x),h \rangle + o(||h||)
$$

_Notation_ : On note $\mathcal{L}(V, \mathbb{R}) = V'$ le dual topologique de $V$, c'est-à-dire l'ensemble des formes linéaires **continues** sur $V$.

### Détour par la dimension finie 

On se restreint maintenant à la dimension finie avec des applications $f : \mathbb{R}^n \to \mathbb{R}$. Puisqu'on est en dimension finie, on peut identifier une base pour $\mathbb{R}^n$ de vecteurs $e_i$.

On note :
$$
\frac{\partial f}{\partial x_i}(x) = \lim_{h \to 0} \frac{f(x + he_i) - f(x)}{h}
$$

la dérivée partielle de $f$ par rapport à la variable $x_i$. Si ces dérivées partielles existent, alors $f$ admet des dérivées directionnelles en $x$ dans toutes les directions, et vice-versa. On peut alors définir le gradient de $f$ en $x$ par :
$$
\nabla f(x) = \left( \frac{\partial f}{\partial x_1}(x), \ldots, \frac{\partial f}{\partial x_n}(x) \right)
$$
On peut alors montrer que, si $f$ est différentiable, alors :
$$
Df(x)(v) = \langle \nabla f(x) \cdot v \rangle
$$
pour tout vecteur $v$.

De plus, on a que $f$ est $\mathcal{C}^k$ si et seulement si toutes ses dérivées partielles sont $\mathcal{C}^{k-1}$.

### Formulaire :

**1) Formule de Taylor avec reste intégral**

Supposons $f$ de classe $\mathcal{C}^2$ dans un ouvert $U$ de $\mathbb{R}^n$ à valeurs dans $\mathbb{R}$. Si le segement $[a, a+h]$ est contenu dans $U$, alors :
$$
f(a+h) = f(a) + \nabla_a f(h) + \int_0^1 (1-t) \nabla^2_{a+th} f(h, h) dt
$$

**2) Formule de Taylor avec reste de Lagrange**

Supposons $f$ de classe $\mathcal{C}^1$ et deux fois différentiable dans un ouvert $U$ de $\mathbb{R}^n$ à valeurs dans $\mathbb{R}$. Si le segement $[a, a+h]$ est contenu dans $U$, alors il existe $\theta \in (0,1)$ tel que :
$$
f(a+h) = f(a) + \nabla_a f(h) + \frac{1}{2} \nabla^2_{a+\theta h} f(h, h)
$$

Si $f$ n'est que simplement différentiable, on a :


$$
f(a+h) = f(a) + D_{a+\theta h} f(h)
$$

Cette dernière propriété rappelle le TAF :

Pour $[a,b]$ un segment réel et $f$ dérivable sur $(a,b)$, il existe $c \in (a,b)$ tel que 

$$
\frac{f(b) - f(a)}{b - a} = f'(c)
$$
