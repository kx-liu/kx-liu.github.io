---
layout: page
title: Measure Sapce
description: sample space, σ-algebra, set function.
img:
importance: 1
category: ST552 Probability and Mathematical Statistics I
related_publications: false
---

# ST452 Probability and Mathematical Statistics

## Lecture 1 Measure Spaces

{% include math.html %}

Probability Space: $(\Omega, \mathscr{F}, \mathbb{P})$

- $\Omega$: Sample Space
- $\mathscr{F}$: "Information"
- $\mathbb{P}$: "Probability"

We start with defining an essential information structure in measure theory, that is algebra and $\sigma$-algebra.

### Definition 1 (Algebra)

A family of subsets of $\Omega$, $\mathscr{F}_0$, that satisfies to the following properties, is called an Algebra:

1) $\Omega \in \mathscr{F}_0$
2) $A \in \mathscr{F}_0 \implies A^c \in \mathscr{F}_0$
3) $A, B \in \mathscr{F}_0 \implies A \cup B \in \mathscr{F}_0$

Additionally, 2. and 3. $\implies A \cap B \in \mathscr{F}_0$ because of the De Morgan's laws.

#### Examples of Algebra

- "Power Set": $2^\Omega$
- "Trivial algebra": $\{\Omega, \emptyset\}$

$\sigma$-algebra allows us to "take the limit of a sequence of events", and the definition is as follows.

### Definition 2 ($\sigma$-algebra)

A family of subsets of $\Omega$, $\mathscr{F}$, that satisfies to the following properties, is called a $\sigma$-algebra:

1) $\Omega \in \mathscr{F}$
2) $A \in \mathscr{F} \implies A^c \in \mathscr{F}$
3) Let $(A_n)_{n \in \mathbb{N}}$ be a sequence of events, $\forall n \in \mathbb{N} : A_n \in \mathscr{F} \implies \bigcup_{n \in \mathbb{N}} A_n \in \mathscr{F}$

Same additionally, 2. and 3. $\implies \bigcap_{n \in \mathbb{N}} A_n \in \mathscr{F}$ because of the De Morgan's laws. Thus, a $\sigma$-algebra on $\Omega$ is a family of subsets of $\Omega$ "stable under any countable collection of set operations".

### Definition 3 (Set Functions on Algebras)

Let $\Omega$ be a set, let $\mathscr{F}_0$ be an algebra on $\Omega$, and let $\mu_0$ be a non-negative set function on $\mathscr{F}_0$, that is $\mu_0: \mathscr{F}_0 \rightarrow [0, \infty]$, if it satisfies the following properties:

1. $\mu_0(\emptyset) = 0$
2. "Finite Additivity": For a sequence of events $(A_n)_{n=1}^m$, $\forall n=1,...,m : A_n \in \mathscr{F}_0$, and $A_n$ are mutually disjoint,

   $$
   \mu_0(\bigcup_{n=1}^{m} A_n) = \sum_{n=1}^{m} \mu_0(A_n)
   $$

Furthermore, we call set functions on $\sigma$-algebras measures on $\sigma$-algebras.

### Definition 4 (Measure of $\sigma$-algebra)

Let $\Omega$ be a set, let $\mathscr{F}$ be a $\sigma$-algebra on $\Omega$, and let $\mu$ be a non-negative set function on $\mathscr{F}$, that is $\mu: \mathscr{F} \rightarrow [0, \infty]$, if it satisfies the following properties:

1. $\mu(\emptyset) = 0$
2. "Countable Additivity": For a sequence of events $(A_n)_{n \in \mathbb{N}}$, $\forall n \in \mathbb{N} : A_n \in \mathscr{F}$, and $A_n$ are mutually disjoint,

   $$
   \mu(\bigcup_{n=1}^{\infty} A_n) = \sum_{n=1}^{\infty} \mu(A_n)
   $$

### Definition 5 (Concerning Measures)

- Finite measure: $\mu(\Omega) < \infty$
- $\sigma$-finite measure: $\exists (A_n)_{n \in \mathbb{N}} : \Omega = \bigcup_{n=1}^{\infty} A_n \text{ and } \mu(A_n) < \infty (\forall n \in \mathbb{N})$
  - E.g., let $\Omega = \mathbb{N}$, let $\mathscr{F} = 2^{\Omega} = 2^{\mathbb{N}}$, and let $\mu(A) = |A|$ and $\mu(\Omega) = \infty$, but for $A_n = \{n\}, \mu(A_n) < \infty$, that is $\mu$ is $\sigma$-finite measure.
- Probability measure: $\mu(\Omega) = 1$. In fact, there's no intrinsic but only scaling difference. We denote probability measure as $\mathbb{P}$.
