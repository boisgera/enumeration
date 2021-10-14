% Enumeration
% Sébastien Boisgérault, MINES ParisTech

---
header-includes:
  - \DeclareMathOperator*{\seg}{seg}
  - \DeclareMathOperator*{\next}{next}
  - \DeclareMathOperator*{\graph}{graph}
---

### Introduction

**TODO:** transfinite (deep) enumeration, punch through the infinite and continue,
"deep" sequences, order type of a well-ordered set and length of a sequence,
(transfinite, deep) induction, or "proof by induction", "definition by induction"
(or "transfinite recursion"), etc.

**TODO:** 

  - Continuity on $[0,1]$ implies boundedness: "natural" / "constructive" 
proof: issue presentation, then back with the tools to make it work?
Anyway a GREAT example of the need for transfinite (deep) iteration,
"limits" to break through, etc.

  - Generation of say algebra (by induction); how it does not work for
    $\sigma$-algebra.



### Notations

  - $\varnothing$ is the empty set: $\forall x, \; x \not \in \varnothing$,

  - $A \subseteq B$: $A$ is included in $B$ ($\forall x \in A, x \in B$),

  - $A \subset B$: $A$ is strictly included in $B$ 
    ($A$ is included in $B$ but differs from it).

In a linearly ordered set $X$:

  - $0_X = \min X$ (if it exists), $1_X = \min X \setminus \{0\}$ (if it exists),
    etc. We drop the $X$ subscript when the context is clear.

  - Notations for the intervals apply as usual and combine with the previous
    convention. A $X$ subscript is added when necessary. For example,
    $\left[x, y\right[_X = \{z \in X \; | \; x \leq z < y\}$. Of particular
    interest:
    $$
    \left[0, x\right[ = \{y \in X \; | \; y < x\}.
    $$



### Well-ordered Sets

#### Initial segment
A subset $S$ of an ordered set $X$ is an *initial segment* of
$X$ if any element of $X$ less than or equal to some element of $S$
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
S = \left[0, x \right[ = \{s \in X \; | \; s < x\}. 
$$

This is not totally obvious at first sight, but this is equivalent to

#### Well-posed set
A linearly ordered set $X$ is *well-ordered* if for any proper initial
segment, there is a segment containing exactly one more point (or 
equivalently a "next" point).

**TODO.** proof.

**TODO.** Also think more about it and the formulation since
I feel that this stuff may be more intuitive than the formulation above:
the segments are the "progress bar" of the enumeration and as long as
we're not done, we can always extend the progress bar by "one tick".

OK, now from now on, our foundational definition of well-ordered set is
based on the concept of successor

#### Successor
Let $X$ be a linearly ordered set.
We define the *successor* of a subset $A$ of $X$ (whenever it exists) as
$$
\next(A) = \min \, \{x \in x \; | \; \forall \, a \in A, \, a < x\}.
$$

#### Note
Our terminology is a slight deviation of the norm, which actually
ends up being a generalization: successors are usually associated 
to elements of $X$, not subsets. We recover the classic definition 
by setting (as you may 
expect!)
$$
\next(x) := \next(\{x\}).
$$

(Nice slot to display an example why the notion attached to subset is richer
than the one attached to elements: consider the successor of $\left[0, 1\right[$
in $\mathbb{R}$; there is no way to define this concept from the "classic"
successor, we need to consider all elements of the set "at once" to be able
to go beyond $\left[0, 1\right[$).

And then:

#### Well-ordered Set
A linearly ordered set $X$ is *well-ordered* if and only if every proper initial
segment has a successor.

Which can handily be reformulated as (the totally equivalent and often handy):

#### Well-ordered Set
A linearly ordered set $X$ is *well-ordered* if and only if for any subset
$S$ of $X$
$$
\mbox{$S$ is an initial proper segment}
\; \longleftrightarrow \;
\exists \, x \in X, \; S = \left[0, x\right[.
$$

(every set $\left[0, x\right[$ is a proper initial segment, that's the 
reverse implication which is interesting.)

We still have a couple more alternate characterization of well-ordered sets.
Another version is obtained by "dualization", and each of the two equivalent
statement gives birth to another one by generalization. The dualized + generalized
statement ends up being the modern, orthodox, definition of well-ordered set.

#### Final Segment
A subset $S$ of an ordered set $X$ is a *final segment* of
$X$ if any element of $X$ greater than or equal to some element of $S$
belongs to $S$:
$$
\forall x \in X, \forall s \in S, \; (x \geq s \rightarrow x \in S)
$$
(or for short $x \geq s \in S \rightarrow x \in S$). 
The final segment $S$ is *proper* if $S \subset X$.

(Equivalently, $S$ is a final segment iff it is an initial segment for
$X$ endowed with $\geq$ instead of $\leq$.)

#### Well-posed set (Dualization)
A linearly ordered set $X$ is *well-ordered* if and only if every non-empty 
final segment has a minimum.

The "issue" with this formalization is that it's more distant from the use
case of TI. The advantage is that it does require the new concept of $\next$
in our order theory toolkit, $\min$ can be used directly instead. We notice
here the markers of dualization in every concept used: 
initial/final, $\leq$/$\geq$, proper/non-empty, etc. 

#### Proof
Given that the set of strict upper bounds of any subset of $X$ is a final 
segment of $X$, the dualized version of well-orderedness clearly implies 
the initial one. 
Conversely, if $S$ is a non-empty final segment of $X$, 
the set $T$ of of strict lower bounds of $S$ is a proper initial segment of $X$.
Now, since the set of strict upper bounds of $T$ is equal to $S$, 
the successor of $T$ is the minimum of $S$.

Now, we can generalize both versions.

#### Well-posed set (Generalization)
A linearly ordered set $X$ is well-ordered if and only if every set with
a strict upper bound has a successor.

#### Proof
Since it's an obvious generalization, we only need to prove that the original
definition implies this property. The sketch of the process is the following:
associate to the original set $A$ the set $S$ of $s$ such that there is a $a \in A$
with $s \leq a$. This is a proper initial segment of $X$ and its set of
strict upper bounds is the same as the one of $A$; thus $A$ has a successor.
$\blacksquare$

#### Well-posed set (Dualization + Generalization)
A linearly ordered set $X$ is well-ordered if and only if every non-empty set 
has a minimum.

#### Proof
Since it's an obvious generalization, we only need to prove that the original
definition implies this property. The sketch of the process is the following:
associate to the original set $A$ the set $S$ of $s$ such that there is a $a \in A$
with $a \leq s$. This is a non-empty final segment of $X$ and its set of
lower bounds is the same as the one of $A$; thus $A$ has a minimum.
$\blacksquare$


**TODO.** Clean-up the sequel (I guess remove mostly).

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

### Woset definition, new thoughts

AFAICT, we could define a woset as a set where every proper initial segment
$S$ has a "successor" (generalizes the notion of successor for a single
element, that's nice; we just have to promote the element to singletion; 
notation operator "next" ?) defined as an element which is 
larger (strict) than every element of the initial segment and such that there
is no smaller element with this property.

If we do that, we can do two things from here: we can **generalize** and 
we can **dualize**.

If we dualize, we end up with the property that every non-empty final segment 
of the set has a min; but that's it. There is no other incentive to dualize
since it makes things harder for the proof of transfinite recursion for
example. If we generalize from here, we get the classic definition
for woset.

If we generalize first, we end up with: every set that does not contain the
maximum of the woset (if it exists) has a successor.

**TODO.** Do we need the generalisation to prove the transfinite recursion
principle (we don't need the dualization AFAICT). Can we prove that the
set of elements where the property holds is an initial segment beforehand?
Or extract from the set where it works the largest initial segment?
Yeah, that would totally work since the union of such sets is an initial
segment. So we don't even need the generalization (even if it's nice to
know that it exists and it's quite pretty since it is symmetric wrt the
dualized version).

So my preffered exposition would be so far: woset if every proper initial
segment has a succesor and then show that the union is also an initial
segment. And then explain transfinite recursion principle in connexion
with this definition (maybe FIRST, to SHOW that we need the woset character.
YEAH, absolutely). The definition fucking DISAPPEARS: it is obvious that we
need to work in such structure for the TRP to have a chance to work.
And probably show later for practical purposes that this property is equivalent 
to the fact that every proper initial segment can be written $["0", x[$ ?

**NOTA.** Set with a succesor to each elements are **inductive**. This is
not strong enough *in general* to have some stronger recursion principle
beyond $\mathbb{N}$. We could show that on the "double" $\mathbb{N}$
(that "simple" induction does not break through the first wall).

# Transfinite Induction

#### Initial Segments and Successors

A set $S$ is an *initial segment* of linearly ordered set $X$ if and only if
$$
\forall \, x, y \in X, \, (y \in S) \wedge (x \leq y) \to x \in S.
$$
It is *proper* if $S \neq X$ (i.e. $S \subset X$). We define the *successor*
of an initial segment $S$ (whenever it exists) as
$$
\next(S) = \min \, \{w \in W \; | \; \forall \, s \in S, \, s < w\}.
$$

(Note that this specific definition of the successor is appropriate for **any** 
subset $S$ of $X$ and not merely initial segments; but we don't care. For
initial segments -- but only initial segments -- we could also use the
definition $\next(S) := \min X \setminus S$.)

**TODO:**

  - Lemma union of init segments is a init segment,

  - Lemma equal or one included in the other,

  - Lemma if next exist, union of seg and next is a segment
    (the smaller larger than the initial one)

(Note that if the successor exists, $S \cup \{\next(S)\}$ is also an initial
segment of $W$, so we could also consider/define the successor of an initial
segment as an initial segment.)


#### Well-Ordered Set
A linearly ordered set is *well-ordered* if any proper initial segment has
a successor.

#### Proper Initial Segments and Intervals
For every element $x$ of a linearly ordered set $X$,
the interval $\left[0, x\right[$ is a proper initial segment of $X$.
The set $X$ is well-ordered if and only if the converse is true:
$$
\mbox{$S$ is a proper initial segment of $X$} 
\, \to \,
\exists \, x \in X, \, S = \left[0, x\right[.
$$

#### Proof 
If $x \in X$, $y \in \left[0, x\right[$ and $z \leq y$, then
$z \leq y < x$, thus $z < x$ and $z \in \left[0, x\right[$. 
Hence, $\left[0, x\right[$ is an initial segment of $X$. 
Since $x \not \in \left[0, x\right[$, it is also proper.

Conversely, if every proper initial segment $S$ has a successor $x := \next(S)$,
since $x = \min \{y \in X \; | \; \forall \, s \in S, \, s < y\}$,
we have $S \subseteq \left[0, x\right[$. If the inclusion was strict, there
would be a $y < x$ such that $y \not \in S$; since $S$ is an initial segment,
no element greater than $y$ could belong to $S$ and thus we would have
$s < y$ for every $s \in S$, a contradiction with the fact that $x$ is the
minimum among those elements. $\blacksquare$

#### Transfinite Induction
Let $X$ be a linearly ordered set and let $A \subseteq X$. 
If for every proper initial segment $S$ of $X$ there is a 
successor $\next(S)$ and if
$S \subseteq A$ implies $\next(S) \in A$ then $A = X$.

#### Terminology
A linearly ordered set where every proper initial segment has a successor
is said to be *well-ordered*. The property that $S \subseteq A$ is called
the *induction hypothesis* and the proof that the induction hypothesis
implies $\next(S) \in A$ is called the *induction step*.

#### Proof (Transfinite Induction) 
Let $S$ be the union of all initial segments of $X$ included in $A$. 
As a union of initial segments, $S$ is an initial segment; 
as a union of subsets of $A$, it is included in $A$.
Thus, it is the largest initial segment included in $A$.
Now, if $S$ was proper, $\next(S)$ would exist and $S \cup \{\next(S)\}$ 
would also be initial segment of $X$.
Moreover, since by the induction step $\next(S) \in A$, 
$S \cup \{\next(S)\}$ would also be included in $A$.
The set $S$ would therefore not be the largest initial segment of $X$ included in $A$ and
we would have a contradiction. Hence, $S$ is not proper but $S=X \subset A$. 
$\blacksquare$

#### Alternate[^alt-proof-TI-note] Proof (Transfinite Induction) {#alt-proof-TI}
Assume that $A \subset X$.
Let $B$ be the set of all $b \in X$ for which there is a 
$x \in X \setminus A$ such that $x \leq b$. This set if a non-empty final 
segment of $X$; its minimum exists iff the minimum of 
$X \setminus A$ exists and then they are the same[^details]. 
The set $S$ composed of all strict lower bounds of $B$ is a 
proper initial subset of $X$; by the induction step, its successor is in $A$.
But since this set of strict upper bounds of $S$ is $B$, its successor is the 
minimum of $B$, and thus the minimum of $X\setminus A$ and 
we end up with a contradiction. Hence, the initial assumption is false and
$A = X$.
$\blacksquare$

[^details]: The set $B$ is included in $X\setminus A$
and every element $b$ of $B$ that does not belong to $X \setminus A$ satisfies 
$x < b$ for some $b \in B$, so no such $b$ can be a minimum of $B$.

[^alt-proof-TI-note]: the alternate proof is arguably more complex, 
but this version also works when transfinite induction is performed 
on well-ordered *classes*, not merely sets. It is actually made of the
expansion of the proof that the existence of a successor for every proper 
initial segment implies the existence of a minimum for any empty set, followed
by the classic one-liner proof of transfinite induction for well-ordered classes.

**TODO:** mention "proof by induction" and properties as a corollary. Here?


## Transfinite Induction on Classes

(This is a digression, not required at this stage, but heavily related to
the statement we have just made. TI on classes is genuinely useful when we
don't know how "deep" we need to go on to build some stuff).



### About Classes (redux)

**TODO.** define "class" (notation "$x \in C$" to mean $\phi(x)$ ; see what
operations are legit with this purely syntactic construct ; also need
"class term" i.e. parametrized class? Dunno.) My redux so far: classes
are a handy syntactic constructs for predicates. If $\phi$ is predicate
with a single free variable $x$, we may instead decide to write
"$x \in \Phi$" to mean that $\phi(x)$ holds. This "abuse" leads use to
extend other notations to classes, for example $x \in \Phi \cup \Psi$
means $\phi(x) \vee \psi(x)$ and so on. Some things cannot be done:
$\Phi \in \Psi$ means nothing in general; classes cannot *a priori* be
considered elements of sets (or classes). But $\Phi \subset \Psi$ is a
non-issue: it's true iff $\phi(x) \to \psi(x)$

(Nota: capital greek letters may be a great notation for classes, 
with the corresponding small letter for the associated predicate.)

Another notation: the class-builder:
$$
\Phi = \{x \; | \; \phi(x)\}
$$

Now the thing is that some classes are not sets since (unbounded) comprehensions
as issues. Remember that only separation (or bounded comprehension) is safe:
for any set $A$, the set-builder notation defines a (unique) set:
$$
\{x \in A \; | \; \phi(x)\}
$$
So, OK, some classes "are not" (do not define) sets. They are called "proper 
classes". At this stage with our definition of classes, we would also have
the converse issues: some sets would not be classes. And this is not something
we are ready to accept, so we need to generalize a bit. The problem at the
moment is that our classes are *definable*, associated to sentences of the
language and this language has a countable numbe of terms, so we cannot
mechanically describe say all real numbers! What we could do at this stage
is describe definable sets, which are not all sets. So to solve this,
we *parametrize* our classes with arbitrary set variables:
we accept any predicate with some distinguished free variable (say $x$)
and $n$ extra slots. Then for any sets $A_1, A_2, \dots, A_n$, we 
can define the (parametrized) class $\Phi$ with
$$
\mbox{"$x \in \Phi$"}
\; \leftrightarrow \;
\phi(x, A_1, \dots, A_n).
$$
As an obvious consequence: every set "is" not a class: pick any set $A$ and
consider the class associated to the predicate $x \in A$. That's it!


#### Transfinite Induction
Let $X$ be a linearly ordered class and let $A \subseteq X$. 
If for every proper initial segment $S$ of $X$ there is a 
successor $\next(S)$ and if
$S \subseteq A$ implies $\next(S) \in A$ then $A = X$.

#### Proof
See [the (alternate) proof for sets](#alt-proof-TI), which works verbatim here.

### Discussion (OBSOLETE)

First let's make sure that the statement make sense. The order $\leq$ shall
be interpreted as a subclass of $X \times X$ which satisfies the three axioms
of order. Everything here can be translated to predicates, this is fine.
The well-ordering property on $X$ and the definition of $\next$ are also 
non-issues.

Now, is it true? I know for a fact that it works in the special (important) case 
$X = \mbox{Ord}$ [@Jec03, p. 21] but I'd like to delay the introduction of 
ordinals at least in the statement of results (in proofs, that would be less
of an issue), so even if the statement for ordinals is probably enough for
every practical use case, its generalisation (to arbitrary well-ordered classes)
would paradoxically be simpler.

So far, I don't know. Possible leads:

  - Use the existing result for ordinals somehow (???),

  - Use the axiom of foundation and the traces of $X$, $A$, etc. on $V_{\alpha}$
    to get sets instead of classes and use the result for well-ordered sets?
    Doesn't seem to work when I detail the approch, because the $\next$ in 
    $X$ has no reason to stay in the same $X_{\alpha}$.

  - Adapt the proof used for sets. Here we quickly run into a problem since
    defining the initial segment $S$ requires that we would use an existential
    quantifier over some segments of $X$ that may be proper classes and
    we are not allowed to do that (note that if the class is $\mbox{Ord}$,
    all its proper initial segments are sets; but does it hold in general?
    Not obvious at all! No, it does not: just add at the end of $\mbox{Ord}$ 
    a "new" element and then $\mbox{Ord}$ is a proper initial segment of this
    well-ordered class. Mmm therefore $\mbox{Ord}$ is the "minimal" well-ordered
    proper class somehow).

    **TODO.** Revisit with the classic proof, maybe this is an artifact of
    my specific (segment-based) proof. Nota: does it mean that my definition
    of well-ordered and the classic one are not equivalent on classes?
    See Jech proof of TI on ordinals.

**TODO.** Search for "well-ordered classes"? Leads:

  - <http://jdh.hamkins.org/transfinite-recursion-as-a-fundamental-principle-in-set-theory/>

  - <https://math.stackexchange.com/questions/2156812/why-doesnt-it-work-for-well-ordered-proper-classes>

Note that if in the induction step, we limit ourseves to initial segments that
are sets, then the transfinite induction fails for classes "larger" than
$\mbox{Ord}$ (say ordinals plus one extra point). Soooo, since we are not
here to fuck with classes for the pleasure, but only to have a version of the
TI that allows us to enumerate stuff at some arbitrary (unknown) depth,
we would naturally limit ourselves to the segments that are sets.
And thus this "hybrid" version fails for general well-ordered classes.
I still don't know if the relaxed/generalized version holds, but this is
less of a practical issue, I can forget about it (avoid yak shaving).

To summarize: we are not really interested in the TI result for 
well-ordered classes, but merely in the "limit" case of TI for sets.

**Note.** The transfinite induction on classes would not solve the other issue
that we have that we need a reference well-ordered "class" that is large 
enough to contain a copy of every other well-ordered set as a proper initial
segment.

**Update.** OK, the general result works AFAICT, with totally elementary
methods. The pb was an artifact of our proof, but if instead we prove that 
"well-ordered in terms of s.i.p." implies "classically well-ordered" 
(by dualization then generalization, which only involves "one class at a type"), 
then the classic demonstration (used for woset, for the class of ordinals in @Jec03)
works without any issue AFAICT.

So we have a general induction principle for woclasses, nice :)

## Definition by Induction: Transfinite Recursion

**TODO.** Consider general class version on woclasses? Not merely ordinal
(which works)? Would it work? Would it be interesting/simpler to state?

(aka transfinite *recursion*). Merely an application of transfinite induction
that establishes existence and uniquemeness of a mathematical object, i.e. two
proofs by induction[^cTRTI]. Nevertheless, if this is our final goal, we can shortcut 
a lot of things directly, without even a formal definition of well-ordered set!

[^cTRTI]: Conversely if we have the transfinite recursion theorem, it's pretty
easy to prove the transfinite induction: the induction hypothesis proves that
the property we are interested in has a single valid value everywhere: true.
That's another argument that justifies the rush for the TR result: the "other
good things" can be derived from it easily.

#### Transfinite Recursion
Let $W$ be a linearly ordered set, let $X$ be a set and let $F$ be a function 
that associates to any function of $S \to X$ 
-- where $S$ is a proper initial segment of $W$ -- an element of $X$. 
Then, if for every proper initial segment $S$ of $W$ there is a successor
$\next(S)$, 
there is a unique function $f: W \to X$ such that for every proper 
initial segment of $W$,
$$
f(\next(S)) = F(f|_S).
$$

#### Proof 

When $W$ has a successor for any proper initial segment and $\infty$ is an
element greater than any $w \in W$, the set $W \cup \{\infty\}$ has the
same property.
We will prove by transfinite induction that for every $w \in W \cup \{\infty\}$,
the transfinite recursion theorem holds on $\left[0, w\right[$; 
since $W = \left[0, \infty \right[$, that will demonstrate the theorem.

Let $S$ be a proper initial segment of $W \cup \{\infty\}$ 
such that the transfinite recursion theorem holds on $\left[0, v\right[$
when $v \in S$.
Since $S = \left[0, w\right[$ with $w := \next(S)$,
the transfinite recursion theorem holds on $\left[0, v\right[$ whenever $v < w$.
Let $f_{v}$ be the corresponding function from $\left[0, v\right[$ to $X$.

Assume that there is a function $f_w: \left[0, w\right[ \to X$ defined
by $f_w(\next(T)) = F(f_w|_T)$ for any proper initial segment $T$ of 
$\left[0, w\right[$.

If $w =\next(\left[0, v\right[)$ for some $v < w$, then the proper initial
segments of $\left[0, w\right[$ are either proper initial segments of 
$\left[0, v\right[$ or $\left[0, v\right[$ itself.
Thus we necessarily have $f_w|_{\left[0,v\right[} = f_v$ and
$f_w(v) = F(f_w|_{\left[0,v\right[}) = F(f_v)$.
Thus, since $\left[0, w\right[ = [0, v]$, $f_w$ is uniquely determined.
We have actually checked the recursion equations for all proper initial 
segments of $\left[0, w\right[$, so it is effectively the unique 
solution to the recursion theorem on $\left[0, w\right[$.

Otherwise we necessarily have
$\left[0, w\right[ = \bigcup_{v < w} \left[0, v\right[$. 
In this case, every proper initial segment of $\left[0, w\right[$ is a
proper initial segment of $\left[0, v\right[$ for some $v < w$.
The function $f_w$ is uniquely determined by $f_w|_{\left[0, v\right[} = f_v$
(we can easily check that this set of constraints is consistent: 
when $v'<v''$, $f_{v''}|_{\left[0, v'\right[} = f_{v'}$);
Conversely, this function is a solution to all required recursion equations 
ans is thus the unique solution to the transfinite recursion theorem
on $\left[0, w\right[$.

The induction hypothesis holds in every case, thus our proof is complete. 
$\blacksquare$


### Transfinite Recursion (classic)
Let $W$ be a well-ordered set, let $X$ be a set and let $F$ be a function 
that associates to any function $\left[0, w\right[ \to X$ 
-- where $w \in W$ -- an element of $X$. 
Then, here is a unique function $f: W \to X$ such that for every 
$w \in W$,
$$
f(w) = F(f|_{\left[0, w\right[}).
$$

This is shorter, but it's (slightly) less obvious why we need the well-ordered
set concept; it would be far less obvious if we had adopted the classic definition
of well-ordered set.

### "Constructive" definition of ordinals

**TODO.** By TR: for any well-ordered set $W$, define the corresponding length
$\alpha$ recursively; show that $W$ and $\alpha$ are isomorphic and that
isomorphic well-posed sets have the same length. Define ordinals as the set of
possible length, and THEN, prove their properties.

### Sets vs Classes

The "general" transfinite recursion statement can use a class function $F$
defined on sequences of length $\alpha$ for any ordinal $\alpha$ (or any
well-ordered class I guess ...) and does not require that the range of $F$ 
is included in any set. And it produces
a class function $f$ defined for every ordinal. The second restriction
(the range of $F$ not being prescribed) could easily be lifted in the 
set version of the result (direct application of replacement). For the
first one, what we could do is apply repeatedly the result for every
$F|_{\alpha}$ where $\alpha$ is an ordinal, check that the corresponding
$f|_{\alpha}$ are consistent with each other ($f|_{\alpha} = (f|_{\beta})|_{\alpha}$
if $\alpha \leq \beta$) and thus we have the existence and uniqueness of the class
function $f$. So, the class version of the TR result can easily be obtained from
the set version if required.

What is great in the class version of the TR theorem, when it is applied to
the construction of a (bounded) sequence of increasing sets (or decreasing sets)
is that the "stationary principle" (application of the axiom of replacement
and the fact that the union of a set of ordinals is an ordinal).

**TODO:** state / prove stationary principle.

How would we find a "large enough" well-posed set that works for the
construction of the set (and not the class) of a generated $\sigma$-algebra ?
The study of countable well-posed sets may be tricky[^iR]; can we leverage a
well-ordering of $\mathbb{R}$ instead (provided by the axiom of choice AND the
principle of transfinite induction, applied to ordinals ! Nota: there is a nice
idea here that no set is so large that it can't be (transfinitely) enumerated.
Let me restate this: **every set can be enumerated** (don't think of it as
a well-order, but as the existence of a sequence of length $\alpha$ -- an
ordinal -- into $X$ such that every member is a value of the sequence exactly
once)) ? 
And prove that the sequence is stationary
at the first uncountable initial segment it encounters (that probably amounts
to show that the union of a countable collection of countable initial segments
of $\mathbb{R}$ is a countable initial segment of $\mathbb{R}$, which is
trivial ! Actually what we could do here is consider the smallest initial segment
in $\mathbb{R}$ -- well-ordered -- which is uncoutable. Call it $\omega_1$ and
that's it, show that the sequence is stationary from this point on. Probably
ok, yes) ?

[^iR]: despite the embedding of countable ordinals as well-ordered subsets of
$\mathbb{R}$, **with the usual order** (!) provided in <https://www.dpmms.cam.ac.uk/~wtg10/ordinals.html> which is a very nice trick. NB: the reference doesn't prove that all 
countable ordinals can be represented like that. But it provides a proof that
there is an uncoutable ordinal if someone needs something less heavy than the
abstract invocation of the existence of a well-order for any set.

# Stationary Principle

#### Every set of ordinals is bounded
If $X$ is a set of ordinals, there is a $\beta  \in \mathrm{Ord}$ such that
for any $\alpha \in X$, $\alpha \leq \beta$.

#### Proof
The ordinal $\beta := \cup X +1$ is an upper bound of $X$.

#### Stationary Principle
Any non-decreasing and bounded sequence of sets indexed by the class of ordinals 
is eventually constant:
let $\left<A_{\alpha} \; | \; \alpha \in \mathrm{Ord}\right>$ 
be such that $A_{\alpha} \subseteq A_{\beta}$ whenever $\alpha \leq \beta$ 
and assume the existence of a set $A$ such that $A_{\alpha} \subseteq A$ 
for any $\alpha$; then there is a $\alpha \in \mathrm{Ord}$ such that 
$A_{\beta} = A_{\alpha}$ for any $\beta \geq \alpha$.  

#### Remark
The non-decreasing property of the sequence $A_{\alpha}$ is typically inferred
from the structure of a transfinite recursion that defines it. For example,
it is non-decreasing if
$$
A_{\beta} = G\left(\bigcup_{\alpha < \beta} A_{\alpha}\right)
\; \mbox{ where } \; \forall X \in \mathrm{V}, \; X \subseteq G(X).
$$

#### Proof
Let $\mathcal{D}$ be the class of subsets of $A$ defined by
$$
\mathcal{D} :=
\left\{A_{\beta} \setminus \cup_{\alpha < \beta} A_{\alpha} \in \mathcal{P}(A) 
\; | \; 
\beta \in \mathrm{Ord}\right\} \setminus \{\varnothing\}.
$$
By the axiom of separation, $\mathcal{D}$ is a set.
Since $\left<A_{\alpha} \; | \; \alpha \in \mathrm{Ord}\right>$ is non-decreasing, 
for every $D \in \mathcal{D}$ there is a unique $\beta \in \mathrm{Ord}$ 
such that $D = A_{\beta} \setminus \cup_{\alpha < \beta} A_{\alpha}$.
Since the image of $\mathcal{D}$ by this (class) function is exactly the class of
ordinals
$$
X = \{\beta \in \mathrm{Ord} \; | \; \cup_{\alpha < \beta} A_{\alpha} \subset A_{\beta} \; \},
$$
by the axiom of replacement, $X$ is actually a set. Let $\alpha$ be the successor
of this set (the smallest ordinal larger than any ordinal in $X$; it's either
$\cup X$ or $\cup X +1$);
now, for any ordinal $\gamma$ larger than $\alpha$ we necessarily 
have $A_{\gamma} = \cup_{\beta < \gamma} A_{\beta}$ which by transfinite 
induction proves that $A_{\gamma} = A_{\alpha}$ whenever $\gamma \geq \alpha$.
$\blacksquare$

**TODO.** Some applications, such as the proof that $\mathrm{V} = \cup_{\alpha} V_{\alpha}$
and / or that the iterative construction of a $\sigma$-algebra "converges"
(has a fixed-point).

**TODO.** Mention non-increasing sequence ?

**TODO.** Quote the Baire-Cantor stationary principle (see <https://math.stackexchange.com/questions/1103509/uses-of-ordinals>), where I got the name from ?

# Countable ordinals

Sources: [@Gow], [@RE]


**TODO.** Prove by transfinite induction that the countable ordinals are 
**exactly** isomorphic to the well-ordered subsets of $\mathbb{R}$, with 
the usual order?
(Deprecated ? See <https://www.dpmms.cam.ac.uk/~wtg10/ordinals.html> 
nevertheless, it's interesting).
**UPDATE.** Not by induction, but its true nonetheless, see <https://risingentropy.com/ordinals-embedded-in-%E2%84%9A-and-%E2%84%9D/>

**NOTA.** To use transfinite recursion in usual cases any not countable
woset would probably work, so $\mathbb{R}$ with such an order (via Zorn lemma)
would work ? Without the need for ordinals ? Investigate this.

**TODO.** implicit "countable" in the sequel (?). Good enough for our use cases
(**TODO** Cantor-Bendixon, generated measure, etc.)

#### Embedding of Well-Ordered Sets in the Real Line
A well-order set is countable if and only if it is isomorphic to a well-ordered
subset of $\mathbb{R}$ (endowed with its usual order).

#### Proof
Let $\left<q_n \; | \; n\in \mathbb{N} \right>$ be an enumeration of
the rationals i.e. a bijective mapping between $\mathbb{N}$ and $\mathbb{Q}$;
for example the sequence $$\left<0, -1, 1, -2, -1.5, -0.5, 0.5, 1.5, 2.0,
-3, -8/3, -7/3, -5/3, -4/3, -2/3,  \dots\right>$$

Let $W$ be a countable set, well-ordered by $\preceq$ and enumerated by
the sequence $\left<w_n \; | \; n \in \mathbb{N}\right>$. Let $r_0 = q_0$; 
we define for any $n \in \mathbb{N}$ the sets
$$
A_n = \{r_i \; | \; i\leq n \, \wedge \, w_i \prec w_{n+1} \}, \;
B_n = \{r_i \; | \; i\leq n \, \wedge \, w_{n+1} \prec w_i \}, \;
$$
and the real number
$$
r_{n+1} = q_m \; \mbox{ where } \;
m = \min \; \{p \in \mathbb{N} \; | \; 
\forall \, a \in A_n, \, \forall \, b \in B_n, 
a \prec q_p \prec b
\}.
$$
This choice is possible at each step since by construction 
$A_n$ and $B_n$ are disjoint and finite and for any $i \leq n$ and $j \leq n$,
we have $r_i < r_j$ if and only if $w_i \prec w_j$.
By induction, the subset $R = \{r_n \; | \; n \in \mathbb{N}\}$ of $\mathbb{R}$
is a well-ordered subset of $\mathbb{R}$ which is isomorphic to $W$.

Conversely, if $R$ is a countable well-ordered subset of $\mathbb{R}$,
we may associate to any $r \in R$ the first rational $q$ of the sequence
$\left<q_n \; | \; n \in \mathbb{N} \right>$ such that
$r < q < \next_R(\left[0_R, r\right[)$. Since the mapping is one-to-one,
the set $W$ is necessarily countable.

(Mostly) Descriptive Approach to Deep Enumeration
================================================================================

**Idea:** postulate the existence of a class of ordinals, with the minimum 
number of ppties that we need to effectively work (be able to prove TI, TR, etc.).
This EXCLUDES an explicit representation of ordinals and the fact that $<$
is $\subset$ for example; we should NOT have to worry about the vertigo induced
by the nesting of ordinals. So there will be some things we won't be "able" to
state: for example (set/proper) initial segments of the class of ordinals
won't "be" ordinals (we won't *know* that) and as a consequence we can merely
state that any well-ordered set is isomorphic to a proper initial segment of
the ordinals and not to an ordinal. And that's a good thing, less
things to consider and we never *need* that. I believe that the nesting of
ordinals is (very) hard to understand and almost entirely irrelevant for
the application of ordinals. But that requires little unorthodox 
twists to define things such as the order type, etc.

Nota: actually we can explicit the class of ordinals, as "hereditarly transitive
sets", and explain the abuse of notation $\alpha \in \mathrm{Ord}$ and then
state the ppties we need. Just, we won't prove it and we don't encourage the
reader to look into this part. 

Nota: we could also "build" the ordinals after the fact (by TR) if we postulate 
that such a class exists.


### Definition of ordinal numbers

#### Note

We present here the definition due to Von Neumann of the ordinals.
This explicit construction does not matter in the least; all that
matters is the descriptive definition of the ordinals given
[in the next section][Properties of ordinal numbers]. 
We won't prove that the definition of ordinals given here satisfy 
these properties.

#### Definitions
A set $x$ is *transitive* if the following property holds:
$$
T(x) := \forall \, y \, \forall \, z \, ((z \in y \, \wedge \, y \in x) \to z \in x)
$$
It is *hereditarily transitive* if the following property holds:
$$
\mathrm{Ord}(x) := T(x) \, \wedge \, \forall \, y \, (y \in x \to T(y)).
$$

We also use the notation $\mathrm{Ord}$ to denote the collection (technically, 
defined by a property and thus a *class*) of sets $\alpha$ which are hereditarily 
transitive. In other words, we (ab)use the notation "$\alpha \in \mathrm{Ord}$" 
as syntaxic sugar for the formula "$\mathrm{Ord}(\alpha)$". But this is only a notation; 
we can prove that the collection $\mathrm{Ord}$ is not a set in ZFC (it is a 
*proper* class). The adoption of this notation for classes gives some extended
meaning to some usual set predicates and operations such as $\subseteq$, $\cup$, 
$\setminus$, etc. which are now relevant for classes and not merely sets.

We endow $\mathrm{Ord}$ with a relation $\leq$ defined by 
$$
\alpha \leq \beta \; \leftrightarrow \; \alpha \in \beta \, \vee \, \alpha = \beta.
$$

### Descriptive properties of ordinal numbers

At this stage I postulate that this is all we need to accept/know about ordinals
to get all the operational tools we need:

> The structure $(\mathrm{Ord}, \leq)$ of ordinals is a well-ordered proper class
where every proper initial segment is a set: it is linearly ordered by $\leq$
and every proper initial segment is a set which has a successor.

### TODO:

What is the laudry list that we have to do now? Check that we can prove:

  - transfinite induction

  - transfinite recursion

  - every well-ordered set is isomorphic to one (unique) ordinal 

  - stationary principle (?)

### Transfinite induction

#### Transfinite induction on ordinals
Let $A \subseteq \mathrm{Ord}$ be a class of ordinals. 
If for every proper initial segment $S$ of $\mathrm{Ord}$,
$S \subseteq A$ implies $\next(S) \in A$, then $A = \mathrm{Ord}$.

#### Proof
Let
$$
S = \{
  \alpha \in \mathrm{Ord} 
  \; | \; 
  \forall \, \beta \in \mathrm{Ord} \setminus A, \, \alpha < \beta 
\}.
$$
It is clear that $S$ is an initial segment of $\mathrm{Ord}$ which is also a subclass of $A$.
If $S$ was proper, by assumption $\next(S)$ would belong to $A$, but then it would also
satisfy the property $\forall \, \beta \in \mathrm{Ord} \setminus A, \, \next(S) < \beta$
and therefore would belong to $S$, yielding a contradiction. Thus, the initial segment $S$ is not proper: 
$S=\mathrm{Ord}$ and hence $A = \mathrm{Ord}$. $\blacksquare$

### Transfinite recursion (TODO)

Let $V$ denote the class of all sets. When $A$ and $B$ are classes, a 
(class) function 
$f:A \to B$ is a class of pairs $(a, b)$ such that $a\in A$ and $b\in B$.

#### Transfinite recursion
Let $F: V \to V$. There is a unique function $f: \mathrm{Ord} \to V$ such that
for any proper initial segment $S$ of $\mathrm{Ord}$,
$$
f(\next(S)) = F(f|_S).
$$

#### Technicality
Since any proper initial segment $S$ of $\mathrm{Ord}$ is a set, by the axiom
of replacement $f|_S$ is a set (and not merely a class). Thus for any candidate
(class) function $f$, $f|_S$ is a (set) function, belongs to $V$ and the 
statement of the theorem makes sense.

#### Proof
Let $A \subseteq \mathrm{Ord}$ be the class of ordinals $\alpha$ such that
the transfinite recursion holds on $[0, \alpha]$:
there is a unique function $f_{\alpha}: \left[0, \alpha\right] \to V$ such that
for any proper initial segment $S$ of $\left[0, \alpha \right]$, 
$f(\next(S)) = F(f|_S)$. 

Let $T \subset A$ be a proper initial segment of $\mathrm{Ord}$.

 1. If $T = \varnothing$, then $\next(T) = 0$. There is a unique proper initial
    segment $S$ of $[0, 0]$: $S=\varnothing$. Since for any function $f$, 
    $f|_{\varnothing} = \varnothing$, $f_0: [0, 0] \to V$ is a solution of the 
    transfinite recursion problem on $[0, 0]$ if and only if
    $f_0(0) = F(f_0|_{\varnothing}) = F(\varnothing)$; this equation defines $f_0$ 
    uniquely.

 2. If $T = [0, \alpha]$ for some $\alpha$, then $\next(T) = \beta + 1$. 
    An proper initial segment $S$ of $T$ is either a proper initial segment
    of $[0, \alpha]$ or $[0,\alpha]$ itself. In the former case, we have 
    necessarily $f_{\alpha+1}|_{[0, \alpha]} = f_{\alpha}$; in the latter,
    $f_{\alpha+1}(\alpha+1) = F(f_{\alpha+1}|_{[0, \alpha]}) = F(f_{\alpha})$.
    This uniquely defines the function $f_{\alpha+1}$.
 
 3. Otherwise, $T = \left[0, \alpha\right[$ for some $\alpha$ and 
    $T = \cup_{\beta < \alpha} [0, \beta]$. We thus necessarily have
    $f_{\alpha}|_{\left[0,\alpha\right[} = \cup_{\beta < \alpha} f_{\beta}$;
    this sequence of sets is increasing and defines a unique function
    which meets the conditions of transfinite recursion for all initial 
    segments of $\left[0, \alpha\right[$. Combining this definition 
    with the (necessary) $f_{\alpha}(\alpha) = 
    F(f_{\alpha}|_{\left[0,\alpha\right[})$ yields a unique $f_{\alpha}$
    which satisfies transfinite recursion equations on $[0,\alpha]$.

Finally, since for any $\alpha$ a function $f:\mathrm{Ord} \to V$ solution
of the transfinite recursion equation on $\mathrm{Ord}$ needs to satisfy
$f|_{[0, \alpha]} = f_{\alpha}$, we have to define $f$ by $f(\alpha)
= f_{\alpha}(\alpha)$; this definition provides $f|_{[0,\alpha]} = f_{\alpha}$.
Since for any proper initial segment $S=\left[0,\alpha \right[$
of $\mathrm{Ord}$ we have
$f(\alpha) = f_{\alpha}(\alpha) = 
F(f_{\alpha}|_{\left[0,\alpha\right[}) = F(f|_{\left[0,\alpha\right[})$,
$f$ is a solution to the transfinite recursion on $\mathrm{Ord}$.
$\blacksquare$

### Isomorphism

The concept of isomorphism relevant for well-ordered sets is: bijective and
strictly increasing function.

#### Isomorphism and order-type
Every well-ordered set $W$ is isomorphic to a unique proper initial segment 
$\left[0,\alpha\right[$ of the ordinals. The ordinal $\alpha$ is denoted
$\mathrm{ord}(W)$ and called *order type* of *W*:
$$
W \simeq \left[0, \mathrm{ord}(W)\right[
$$

#### Proof
Uniqueness is a consequence of the property that no well-ordered set is 
isomorphic to one of its proper initial segment, which is itself a consequence
of the "non-compression lemma" which state that any strictly increasing 
function $f$ between well-ordered sets satisfies $f(x) \geq x$ for any $x$.

To prove the existence, we leverage transfinite recursion. Let $W$ be a 
well-ordered set. We add a new element denoted $\infty$ at the end of $W$
(for example $\infty := \{W\}$ since we know that $W \not \in W$), define 
$f: \mathrm{Ord} \to W \cup \{\infty\}$ by
$$
f(\alpha) = \left|
\begin{array}{rl}
\next f(\left[0, \alpha \right[) & \mbox{if it exists,} \\
\infty & \mbox{otherwise.}
\end{array}
\right.
$$
and $S:= \{\alpha \in \mathrm{Ord} \; | \; f(\alpha) < \infty\}$. 
We assert that $S$ is a proper initial segment of the ordinals and that
$f|_S$ is an isomorphism from $S$ to $W$. The steps are:

 1. for every ordinal $\alpha$, $f(\left[0, \alpha \right[)$ is a segment
    of $W \cup \{\infty\}$. Proof by transfinite induction with the usual
    disjunction of cases; we leverage that the empty set is an initial segment,
    the union of an initial segment with its successor is an initial segment
    and that a union of initial segments is an initial segment.

 2. the function $f$ is non-decreasing; by construction.

 3. if $f(\alpha) < \infty$ and $\alpha < \beta$, then $f(\alpha) < f(\beta)$;
    also a direct consequence of the definition of $f$.

 4. there is a (smallest) ordinal $\alpha^*$ such that $f(\alpha^*) = \infty$.
    "Smallest" results from the fact that the set of $\alpha$ such that
    $f(\alpha)< \infty$ is a segment of the ordinals since $f$ is non-decreasing.
    The existence if proven by contradiction: if there is no such $\alpha^*$,
    $f:\mathrm{Ord} \to W$ is into (by point 3) and therefore we can define the 
    class function $g: W \to \mathrm{Ord}$ by $g(w) = f^{-1}(w)$ if $w\in f(\mathrm{Ord})$
    or $g(w) = 0$ otherwise. But then $\mathrm{Ord}$ would be the image of a set
    by a class function and thus by the axiom of replacement would be as set,
    which is a contradition. 

  5. $S:= \{\alpha \in \mathrm{Ord} \; | \; f(\alpha) < \infty\} 
     = \left[0,\alpha^*\right[$ and thus $f(S)= W$ (it is an initial segment
     of $W$ which has no successor in $W$, thus is $W$). Since $f$ is strictly
     increasing on $S$, $f|_S$ is an isomorphism.

### Boundedness and Stationarity

#### Boundedness
If $A \subset \mathrm{Ord}$ is a set of ordinals, 
there is a $\beta \in \mathrm{Ord}$ 
such that for any $\alpha \in A$, $\alpha \leq \beta$.

#### Proof
Associate to $A$ the initial segment $S$ given by
$$
S := \{
  \gamma \in \mathrm{Ord} 
  \; | \; 
  \exists \, \alpha \in A, \, \gamma \leq \alpha 
\;\}
=
\bigcup_{\alpha \in A} [0, \alpha].
$$
Since by construction $S$ is a set, there is a $\beta \in \mathrm{Ord}$ such
that $S = \left[0, \beta \right[$; this ordinal $\beta$ satisfies the
statement of the theorem (and even $\alpha < \beta$).


#### Stationary Principle
Any non-decreasing and bounded sequence of sets indexed by the class of ordinals 
is eventually constant:
let $\left<A_{\alpha} \; | \; \alpha \in \mathrm{Ord}\right>$ 
be such that $A_{\alpha} \subseteq A_{\beta}$ whenever $\alpha \leq \beta$ 
and assume the existence of a set $A$ such that $A_{\alpha} \subseteq A$ 
for any $\alpha$; then there is a $\alpha \in \mathrm{Ord}$ such that 
$A_{\beta} = A_{\alpha}$ for any $\beta \geq \alpha$.  

#### Remark
The non-decreasing property of the sequence $A_{\alpha}$ is typically inferred
from the structure of a transfinite recursion that defines it. For example,
it is non-decreasing if
$$
A_{\beta} = G\left(\bigcup_{\alpha < \beta} A_{\alpha}\right)
\; \mbox{ where } \; \forall X, \; X \subseteq G(X).
$$

#### Proof (**TODO: reread**)
Let $\mathcal{D}$ be the class of subsets of $A$ defined by
$$
\mathcal{D} :=
\left\{A_{\beta} \setminus \cup_{\alpha < \beta} A_{\alpha} \in \mathcal{P}(A) 
\; | \; 
\beta \in \mathrm{Ord}\right\} \setminus \{\varnothing\}.
$$
By the axiom of separation, $\mathcal{D}$ is a set.
Since $\left<A_{\alpha} \; | \; \alpha \in \mathrm{Ord}\right>$ is non-decreasing, 
for every $D \in \mathcal{D}$ there is a unique $\beta \in \mathrm{Ord}$ 
such that $D = A_{\beta} \setminus \cup_{\alpha < \beta} A_{\alpha}$.
Since the image of $\mathcal{D}$ by this (class) function is exactly the class of
ordinals
$$
X = \{\beta \in \mathrm{Ord} \; | \; \cup_{\alpha < \beta} A_{\alpha} \subset A_{\beta} \; \},
$$
by the axiom of replacement, $X$ is actually a set. Let $\alpha$ be the successor
of this set (the smallest ordinal larger than any ordinal in $X$; it's either
$\cup X$ or $\cup X +1$);
now, for any ordinal $\gamma$ larger than $\alpha$ we necessarily 
have $A_{\gamma} = \cup_{\beta < \gamma} A_{\beta}$ which by transfinite 
induction proves that $A_{\gamma} = A_{\alpha}$ whenever $\gamma \geq \alpha$.
$\blacksquare$

Misc. / Unsorted
================================================================================

Enumeration
--------------------------------------------------------------------------------

Préciser le concept, équivalent à la donnée d'un bon ordre sur un ensemble :
une "suite" (généralisée) à valeurs dans un ensemble X, indexée par un ordinal
(ou un woset ...) tel que tout élement de X est présent une fois et une seule
dans les valeurs de la suite.

C'est *presque* trivialement équivalent à la donnée d'un well-order, mais
l'image mentale est très différente.

Probablement mieux d'indexer sur un ordinal (sur un "segment initial de
nombres entiers généralisés"), ça étend plus naturellement la notion de "suite"
qu'on a en tête (indexée par des entiers).


--------------------------------------------------------------------------------

Many well-ordered sets have the same structure; for example $\{0,1,2\}$ and
$\{1,2,3\}$, $\mathbb{N}$ and $2\mathbb{N} =
\{2n\; | \; n \in N\}$, etc. Among every collection of the well-ordered sets 
having the same structure, we would like to distinguish a canonical one.

But to begin with, let's formalize the concept of well-ordered sets 
"having the same structure":

#### Isomorphism of well-orders
Two well-ordered sets are *isomorphic* if there exist an increasing
bijection between them.

**TODO:** (finite and strictly countable) ordinals as equivalence classes
of subsets of $\mathcal{\mathcal{P}(\mathbb{N} \times \mathbb{N})}$, 
with the induced (well-)order. 
As a "canonical" well-ordered set associated to any countable well-posed set.

Any relation $R$ on a subset $X$ of $\mathbb{N}$ can be ordered.

# Bibliography