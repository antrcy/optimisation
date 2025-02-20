## Résultats d'existence et d'unicité

### Existence d'un minimum

C'est-à-dire d'une borne inférieure atteinte.

_Théorème_ : (Weierstrass) Soit $J : K \subset V \to \mathbb{R}$, avec $K$ et $V$ de Hilbert. Alors $J$ admet un minimum sur $K$.


_Définition_ : Une fonction $f$ est dite sous-continue inférieure ($\text{s.c.i}$) en $x_0 \in K$ si :

$$
\text{lim}_{x \to x_0} \text{ inf}\{f(x)\} \geq f(x_0)
$$

Un exemple classique d'une fonction $\text{s.c.i}$ est la marche.

_Proposition_ : $f$ est $\text{s.c.i}$ $\iff$ les sous ensembles de niveaux de $f$ sont fermés.

Maintenant la notion introduite on peut maintenant étendre le résultat attribué à Weierstrass :

_Théorème_ : (Weiestrass bis) Soit $J : K \subset V \to \mathbb{R}$ $\text{s.c.i}$ sur $K$ un compact. Alors $J$ admet un minimum sur $K$. 

On sent bien que la démonstration utilisera probablement la caractérisation séquentielle d'un fermé.

___

**Résultats supplémentaires en dimension finie**

On suppose désormais que $V$ n'est plus de Hilbert, mais euclidien.

_Définition_ : Soit $J : K \subset V \to \mathbb{R}$ est dite coercie si, pour $K$ fermé et $\forall (x_n)_{n \in \mathbb N} \subset K$ :

$$
\|x_n\| \to +\infty \implies J(x_n) \to +\infty
$$

_Théorème_ : Soit $J : K \subset V \to \mathbb{R}$ continue et coercie, alors $J$ admet un minimum sur $K$ fermé.

_Propriété_ : Soit $K \subset V$ un convexe et fermé, avec $J$ continue sur $K$. Si $J$ est $\alpha$-convexe, alors $J$ est coercive.

___

**Résultats supplémentaires en dimension infinie**

On retourne sur les espaces de Hilbert. En dimension infinie, les choses ne sont pas aisément bornables, et les compacts et convexes ne se comportent pas de manière systématique. On doit donc introduire une topologie plus restrictive, plus contraignante, mais qui permettra de retomber sur des resultats analogues à la dimension finie.


_Définition_ : Soit $(x_n)_n$ une suite dans $V$ de Hilbert, sur lequel on a posé un produit scalaire $\langle \cdot , \cdot \rangle$. On dit que $x_n$ converge faiblement vers $x^*$ si, $\forall y \in V$ :

$$
\langle y, x_n \rangle \to \langle y, x^*\rangle 
$$

Cela défini une nouvelle topologie sur $V$ dite topologie faible. Pour cette topologie, les applications de la forme :

$$
L_y : x \to \langle x, y \rangle
$$

sont continues. On peut alors définir de manière minimaliste les ouverts et les fermés de cette topologie, comme les images réciproques des ouverts et fermés de $\mathbb R$ par ces applications.

_Propositions_ :

1) Tout convexe fermé de la topologie forte est fermé pour la topologie faible.

2) Si $J$ est convexe $\text{s.c.i}$ pour la topologie forte, alors elle est $\text{s.c.i}$ pour la topologie faible.

Le premier point se démontre en utilisant une variante géométrique du théorème de Hahn-Banach. Le deuxième point se démontre en utilisant la caractérisation par les sous-ensembles de niveaux de $J$ des fonctions $\text{s.c.i}$.

_Ex_ : L'application norme associée au produit scalaire sur $V$ est continue et convexe donc $\text{s.c.i}$ pour la topologie forte. Elle est donc $\text{s.c.i}$ pour la topologie faible. Cepedant, elle n'est pas continue pour la topologie faible. Un exemple classique est la fonction $\exp({2in\pi})$ qui converge vers $0$ pour la topologie faible mais donc la norme est constante évaluée à $1$.

_Propriété_ : Si $x_n \to x$ pour la topologie forte, alors $x_n \to x$ pour la topologie faible.

_Théorème_ : (Compacité séquentielle) Si $(x_n)$ est une suite bornée de $V$ de Hilbert, on peut en extraire une sous suite convergente au sens faible.

_Théorème_ : Soit $J : K \subset V \to \mathbb{R}$ une fonction $\text{s.c.i}$ convexe sur $K$ un convexe fermé. Si $K$ est borné, ou si $J$ est coercive, alors $J$ admet un minimum sur $K$.

Ce résultat se démontre comme suit : on détermine une suite minimisante nécessairement bornée, soit car $K$ est borné, soit car $J$ est coercive. On utilise le résultat précédent pour extraire une sous suite convergente pour la topologie faible. Etant donnée que $K$ est convexe fermé, c'est un fermé pour la topologie faible. De plus, $J$ est convexe $\text{s.c.i}$ pour la topologie faible, elle est donc $\text{s.c.i}$ pour la topologie faible. On a donc :

$$
\text{liminf}J(x_{n_k}) \geq J(x^*) \geq \text{inf}_KJ
$$

On rappelle que la première inégalité découle du fait que la suite des $\text{inf}$ est toujours décroissante. Puisque $x_{n_k}$ est convergente :

$$
\text{liminf}J(x_{n_k}) = \text{lim} J(x_{n_k})\geq J(x^*) \geq \text{inf}_KJ
$$

Or puisque $\text{lim} J(x_{n_k}) = \text{inf}_KJ$, on en déduit que $J(x^*) = \text{inf}_KJ$

$\square$


### Unicité d'un minimum

_Propriétés_ : Soit $J:K\in V \to \mathbb R$;

1) Si $J$ est convexe, tout minimum local est minimum global. De plus, l'ensemble des minimiseurs forme un ensemble convexe.

2) Si $J$ est strictement convexe, et que $K$ est convexe, alors il y a au plus un minimiseur.