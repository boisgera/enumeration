% Enumeration
% Sébastien Boisgérault, MINES ParisTech

---
header-includes:
  - \DeclareMathOperator*{\seg}{seg}
---


#### Notations

  - $A \subseteq B$: $A$ is included in $B$ ($\forall x \in A, x \in B$),

  - $A \subset B$: $A$ is strictly included in $B$ 
    ($A$ is included in $B$ but differs from it).



#### Initial segment
A subset $S$ of an ordered set $X$ is an *initial segment* of
$X$ if any element of $X$ less than some element of $S$
belongs to $S$:
$$
\forall x \in X, \forall s \in S, \; (x \leq s \rightarrow x \in S)
$$
(or for short $x \leq s \in S \rightarrow x \in S$). 
The initial segment $S$ is *proper* if $S \subset X$.

#### Initial segments of $\mathbb{R}$
For example, for any $x\in\mathbb{R}$, $\left]-\infty, x\right[$ 
and $\left]-\infty, x\right]$ as well as $\varnothing$ and $\mathbb{R}$ 
are initial segments of $\mathbb{R}$. 
They actually are the only ones: 
for any proper initial segment $S$, let $x=\sup S \in \left[-\infty, +\infty\right]$;
if $y < x$, $y$ is not an upper bound of $S$ thus there is a $s \in S$
such that $y < s$, which yields $y \in S$; consequently, 
$S=\left]-\infty, x\right]$ if $x$ belongs to $S$ and 
$S=\left]-\infty, x\right[$ otherwise.


#### Well-posed set
A linearly ordered set $X$ is *well-ordered* if for every proper initial
segment $S$ of $W$, there is a $x \in X$ such that
$$
S = S_x := \{s \in X \; | \; s < x\}. 
$$

#### Well-posed set -- Alternate characterization
An ordered set $X$ is well-posed if and only if any non-empty subset
$Y$ of $X$ has a least element:
$$
\varnothing \subset Y \subseteq X \rightarrow \exists x \in Y, 
\; \forall y \in Y, \; x \leq y.
$$

#### Proof
Assume that every non-empty subset of $X$ has a least element and let $S$ be
a proper initial segment of $X$. Then $X\setminus S$ is non-empty and hence
has a least element $x$. If $s < x$, since $x$ is the least
element of $X\setminus S$, $s \not \in X \setminus S$, hence $s \in S$. 
Now, assume that $s \in S$ ; if $s \geq x$, since $S$ is an initial segment,
$x \in S$, which is absurd; thus, $s < x$. Consequently, $S = S_x$.

Conversely, assume that every proper initial segment $S$ of $X$ is equal to
$S_x$ for some $x \in X$. Let $A$ be a non-empty subset of $X$ and let $S$ 
be the set of all $s \in X$ which are less than every element $a$ of $A$. 
The set $S$ is a proper initial segment of $X$: indeed if $x \leq s \in S$, 
then for every $a \in A$, $x \leq s < a$, hence $x < a$ and thus
$x \in S$. Let $x \in X$ such that $S = S_x$. Since by construction 
$S\cap A =\varnothing$, $x \in A$ ; if $y < x$, then $y \in S_x= S$, 
thus $y \not \in A$: $x$ is the least element of $A$.
$\blacksquare$

