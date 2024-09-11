---
layout: page
title: Chapter 6 Product Measure
description: Product Measures, Tonelli's Theorem, Fubini's Theorem.
importance: 1
category: ST552 Probability and Mathematical Statistics I
related_publications: false
pseudocode: true
---

******

Let $(\Omega_1,\mathcal{F}_1)$ and $(\Omega_2,\mathcal{F}_2)$ be two measurable spaces. Consider $\Omega:=\Omega_1\times\Omega_2$

Coordinate maps:

$$
\begin{aligned}
\rho_1((\omega_1,\omega_2))&=\omega_1\\
\rho_2((\omega_1,\omega_2))&=\omega_2
\end{aligned}
$$

Define $\mathcal{F}:=\sigma(\rho_1,\rho_2)$, which is the "product $\sigma$-algebra". Notation: $\mathcal{F}:=\mathcal{F_1}\times\mathcal{F}_2$.

$$
\begin{aligned}
\rho_1^{-1}(B_1)&=B_1\times\Omega_2,\qquad B_1\in\mathcal{F}_1\\
\rho_2^{-1}(B_2)&=B_2\times\Omega_1,\qquad B_2\in\mathcal{F}_2\\
\end{aligned}
$$

$$
\rho_1^{-1}(B_1)\cap\rho_2^{-1}(B_2)=B_1\times B_2
$$

Moreover, 

$$
\mathcal{I}:=\{B_1\times B_2:B_i\in\mathcal{F}_i\}
$$

is a $\pi$-system generating $\mathcal{F}$.

## Lemma 1

Let $\mathcal{H}$ be the class of functions $h:\Omega\to\mathbb{R}\text{ s.t. }h\in b\mathcal{F}$, which is bounded and measuable, and that

1. $\forall\omega_1\in\Omega_1$, the map $\omega_2\to h(\omega_1,\omega_2)\in\mathcal{F}_2$
2. $\forall\omega_2\in\Omega_2$, the map $\omega_1\to h(\omega_1,\omega_2)\in\mathcal{F}_1$

Then $\mathcal{H}=b\mathcal{F}$.

### Proof of Lemma 1

$$
A\in\mathcal{I}\implies\mathbb{1}_A\in\mathcal{H}
$$

1. Constant functions are in $\mathcal{H}$
2. $h_n\geq0,h_n\leq h_{n+1}<K<\infty,h=\sup h_n,h_n\in\mathcal{H},h(\omega_1,\omega_2)=\sup h_n(\omega_1,\omega_2)\implies h\in\mathcal{H}$. $\mathcal{H}$ is a monotone class, therefore $\mathcal{H}$ contains all bounded $\sigma(\mathcal{I})$-measurable functions. But $\sigma(\mathcal{I})=\mathcal{F}$.

## Lemma 2

Suppose $(\Omega_i,\mathcal{F}_i,\mu_i)$ are $\sigma$-finite. If $E\in\mathcal{F}$, then the functions

$$
f(\omega_1):=\mu_2(\{(\omega_1,\omega_2):(\omega_1,\omega_2)\in E\})\\
f(\omega_2):=\mu_1(\{(\omega_1,\omega_2):(\omega_1,\omega_2)\in E\})
$$

are measurable, and

$$
\int f\mathrm{d}\mu_1=\int g\mathrm{d}\mu_2
$$

### Proof of Lemma 2

Suppose $\mu_i$'s are finite.

$$
\mathcal{L}:=\{E\in\mathcal{F}:f\in\mathcal{F}_1\}
$$

1. $\mathcal{I}\subset\mathcal{F}$: If $E\in\mathcal{I},E=B_1\times B_2$, where $B_i\in\mathcal{F}_i$.

   $$
   f(\omega_1)=\mathbb{1}_{B_1}\mu_2(B_2)\in m\mathcal{F}_1
   $$

2. $\mathcal{L}$ is a $\lambda$-system (**Prove it!!**). By Dynkin's $\pi$-$\lambda$ Theorem, $\mathcal{L}\supset\sigma(\mathcal{I})=\mathcal{F}$. $f$ is $\mathcal{F}_1$-measurable $\forall E\in\mathcal{F}$, thus $g$ is $\mathcal{F}_1$-measurable $\forall E\in\mathcal{F}$.

3. Define $\Pi_i$ on $(\Omega,\mathcal{F})$ by

   $$
   \Pi_1(E)=\int f\mathrm{d}\mu_1,\qquad\Pi_2(E)=\int g\mathrm{d}\mu_2
   $$

   $\Pi_1(\Omega)=\int_{\Omega_1}\mu_2(\Omega_2)\mathrm{d}\mu_1=\mu_2(\Omega_2)\mu_1(\Omega_1)$, and $\Pi_2(\Omega)=\mu_1(\Omega_1)\mu_2(\Omega_2)$, which are two set functions agreeing on $\Omega$.

4. $\Pi_i$'s are countably additive set functions (**Prove it!!**). 

5. If $A\in\mathcal{I},\Pi_1(A)=\int\mathbb{1}_{B_1}\mu_2(B_2)\mathrm{d}\mu_1=\mu_1(B_1)\mu_2(B_2)$, and $\Pi_1(A)=\mu_1(B_1)\mu_2(B_2)$.

6. $\Pi_1$ and $\Pi_2$ can be extended uniquely to $\mathcal{F}$ to define the product measure $\Pi$.

For the $\sigma$-finite case: $\Omega_1=\bigcup_{n\geq1}B_{1n},\mu_1(B_{1n})<\infty$, and $\Omega_2=\bigcup_{n\geq1}B_{2n},\mu_2(B_{2n})<\infty$. On each $\mathcal{F}\_i$, define $\mu_{in}(E_i):=\mu_i(E_i\cap B_{in})$. Analogously define $\Pi_{1n}$ and $\Pi_{2n}$ and conclude by MCT and the result prove for the finite measure case.

We have in fact defined our product measure!

$$
\Pi(E)=\int f\mathrm{d}\mu_1=\int g\mathrm{d}\mu_2.
$$

## Theorem 1 (Tonelli's Theorem)

$(\Omega_i,\mathcal{F}_i,\mu_i)$ are $\sigma$-finite, $f\in (m\mathcal{F})^+$. Then, 

$$
\begin{aligned}
g_1(\omega_1)&=\int f(\omega_1,\omega_2)\mu_2(\mathrm{d}\omega_2)\in m\mathcal{F}_1\\
g_2(\omega_2)&=\int f(\omega_1,\omega_2)\mu_1(\mathrm{d}\omega_1)\in m\mathcal{F}_2\\
\end{aligned}
$$

$$
\int_{\Omega}f\mathrm{d}\Pi=\int_{\Omega_1}f_1\mathrm{d}\mu_1=\int_{\Omega_2}f_2\mathrm{d}\mu_2
$$

### Proof of Tonelli's Theorem

If $f=\mathbb{1}_E,E\in\mathcal{F}$, the result follows from Lemma 2. By the linearity of integrals, it tolds for all non-negative simple measurable functions, MCT yields the claim for all non-negative measurable functions.

## Theorem 2 (Fubini's Theorem)

The conclusion of the above holds if $f\in m\mathcal{F}$, and $\int\lvert f\rvert\mathrm{d}\Pi<\infty$.

**Warning**: $\sigma$-finiteness is crucial. E.g.: $\Omega_i=[0,1],\mathcal{F}_i=\mathcal{B}[0,1],\mu_1=Leb,\mu_2$ is the counting measure. $E=\\{(x,y):x=y\\}\in\mathcal{F}$, 

$$
\begin{aligned}
\int\int\mathbb{1}_{\{x=y\}}\mu_2(\mathrm{d}y)\mu_1(\mathrm{d}x)=\int\mu_1(\mathrm{d}x)=1\\
\int\int\mathbb{1}_{\{x=y\}}\mu_1(\mathrm{d}x)\mu_2(\mathrm{d}y)=\int0\mu_2(\mathrm{d}y)=0
\end{aligned}
$$

**Remark**: Product measures are handy when it comes to joint laws of r.v.'s. 
