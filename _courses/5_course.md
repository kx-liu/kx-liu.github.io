---
layout: page
title: Chapter 4 Integration
description: Simple functions, Integration, Monotone Convergence Theorem, Fatou's Lemma, Dominated Convergence Theorem.
importance: 1
category: ST552 Probability and Mathematical Statistics I
related_publications: false
pseudocode: true
---

******

Let $(\Omega,\mathcal{F},\mu)$ be a measure space.

Aim: Give a meaning to, for $f\in\mathcal{F}$, 

$$
\mu(f):=\int_{\Omega}f(\omega)\mu(\mathrm{d}\omega)=\int_\Omega f\mathrm{d}\mu
$$

We start with simple functions.

## Definition 1 (Simple function)

$f\in(m\mathcal{F})^+$ is called simple, if

$$
f=\sum_{k=1}^m a_k\mathbb{1}_{A_k},\quad A_k\in\mathcal{F},a_k\in[0,\infty],m<\infty
$$

## Theorem 1

If $f$ is simple, then it has a unique standard representation as follows:

$$
f=\sum_{k=1}^nc_k\mathbb{1}_{B_k},\quad c_k\in[0,\infty],B_k\in\mathcal{F}\text{ s.t. }B_i\cap B_j=\emptyset,c_i\neq c_j (\forall i\neq j),\bigcup B_i=\Omega
$$

So, the integration of simple function can be defined now. Let $f$ be simple with standard representation above. Then

$$
\mu(f):=\int_\Omega f\mathrm{d}\mu=\sum_{k=1}^nc_k\mu(B_k)
$$

[Convention: $\infty\cdot0=0$, for the case when $c_k=\infty$ and $\mu(B_k)=0$.]

## Lemma 1 (Properties of integration of simple functions)

If $f$ and $g$ are simple, and $\alpha\geq0$, then

1. $\mu(\alpha f)=\alpha\mu(f)$
2. $\mu(f+g)=\mu(f)+\mu(g)$

### Proof of Lemma 1

1. If $\alpha=0$, nothing to show. $\mu(\alpha f)=0$, due to the convention. Assume $\alpha>0$:

   $$
   \alpha f=\sum_{k=1}^n\alpha c_k\mathbb{1}_{B_k}\implies\mu(\alpha f)=\sum_{k=1}^n\alpha c_k\mu(B_k)=\alpha\mu(f)
   $$

2. Suppose $g=\sum_{k=1}^{m}a_k\mathbb{1}\_{E_k}$, $f=\sum_{i=1}^nc_i\mathbb{1}\_{B_i}$. Thus, 

   $$
   f+g=\sum_{i=1}^n\sum_{k=1}^m(a_k+c_i)\mathbb{1}_{E_k\cap B_i}
   $$

   $(E_k\cap B_i)_{k,i}$ are disjoint. The problem is that $a_k+c_i$ are not distinct. Define $d_j,j=1,\dots,p$ are distinct values that $(a_k+c_i)$ can take. Let $G_j=\bigcup E_k\cap B_i$ such that $a_k+c_i=d_j$ (Let $I$ denote it). 

   $$
   \mu(G_j)=\sum_{I}\mu(E_k\cap B_i)
   $$

   Thus, $f+g=\sum_{j=1}^p d_j\mathbb{1}_{G_j}$, and

   $$
   \begin{aligned}
   \mu(f+g)&=\sum_{j=1}^pd_j\mu(G_j)\\
   &=\sum_{j=1}^pd_j\sum_{I}\mu(E_k\cap B_i)\\
   &=\sum_{i=1}^n\sum_{k=1}^m(a_k+c_j)\mu(E_k\cap B_i)\\
   &=\sum_{i=1}^nc_i\sum_{k=1}^m\mu(E_k\cap B_i)+\sum_{k=1}^ma_k\sum_{i=1}^n\mu(E_k\cap B_i)\\
   &=\sum_{i=1}^nc_i\mu(B_i\cap(\cup_k E_k))+\sum_{k=1}^ma_k\mu(E_k\cap(\cup_i B_i))\\
   &=\mu(f)+\mu(g)
   \end{aligned}
   $$

## Definition 2 (Integral)

Let $f\in(m\mathcal{F})^+$. Then, the integral of $f$ is as follows:

$$
\mu(f):=\sup\{\mu(\varphi),0\leq\varphi\leq f,\varphi\text{ is simple}\}
$$

## Lemma 2

If $f,g\in(m\mathcal{F})^+$and $f\leq g$, then $\mu(f)\leq\mu(g)$.

## Theorem 2 (Monotone Convergence Theorem, MCT)

If $(f_n)\_{n\in\mathbb{N}}\in(m\mathcal{F})^+$, such that $f_n(\omega)\leq f_{n+1}(\omega),\forall\omega\in\Omega,\forall n\in\mathbb{N}$ , and $f_n\uparrow f$, 

$$
\int f\mathrm{d}\mu=\int\lim_{n\to\infty}f_n\mathrm{d}\mu=\lim_{n\to\infty}\int f_n\mathrm{d}\mu.
$$

### Proof of MCT

Notice that $f\geq0,f\in\mathcal{F}$. 

$$
\int f_n\mathrm{d}\mu\leq\int f_{n+1}\mathrm{d}\mu\leq\int f\mathrm{d}\mu
$$

Take limits on both sides,

$$
\lim\int f_n\mathrm{d}\mu\leq\int f\mathrm{d}\mu
$$

Let $\alpha\in(0,1)$, and $\varphi$ simple, such that $\varphi\leq f$. Let $A_n:=\\{\omega:f_n(\omega)\geq\alpha\varphi(\omega)\\}\in\mathcal{F}$, $A_n\subset A_{n+1}$, $\Omega=\bigcup A_n$. We have

$$
\int_{A_n}\varphi\mathrm{d}\mu=\int_{\Omega}\varphi\mathbb{1}_{A_n}\mathrm{d}\mu\leq\int_{\Omega}\frac{f_n}{\alpha}\mathbb{1}_{A_n}\mathrm{d}\mu=\frac{1}{\alpha}\int_{\Omega}f_n\mathbb{1}_{A_n}\mathrm{d}\mu\leq\frac{1}{\alpha}\int_{\Omega}f_n\mathrm{d}\mu
$$

For $E\in\mathcal{F},\lambda(E)=\int_E\varphi\mathrm{d}\mu$. $\lambda$ is a measure on $\Omega$. (**Prove it!!**)

$$
\lambda(A_n)\leq\frac{1}{\alpha}\int_\Omega f_n\mathrm{d}\mu
$$

And we also have

$$
\lambda(\Omega)\leq\int_\Omega \varphi\mathrm{d}\mu\leq\int_\Omega f\mathrm{d}\mu
$$

By Monotone Convergence from below of Measures,

$$
\sup_\varphi\lambda(\Omega)=\int_{\Omega}f\mathrm{d}\mu\leq\frac{1}{\alpha}\lim\int_\Omega f_n\mathrm{d}\mu
$$

Let $\alpha\to1$, we have

$$
\int_{\Omega}f\mathrm{d}\mu\leq\lim\int_\Omega f_n\mathrm{d}\mu
$$

## Corollary

If $f,g\in(m\mathcal{F})^+$ and $\alpha\geq0$, then $\mu(\alpha f)=\alpha\mu(f)$, and $\mu(f+g)=\mu(f)+\mu(g)$.

## Lemma 3

If $f\in(m\mathcal{F})^+$, $\exists(\varphi_n)_{n\geq1}$, such that $\varphi_n$'s are simple, and $\varphi_n\uparrow f$.

## Theorem 3 (Fatou's Lemma)

If $(f_n)_{n\geq1}\in(m\mathcal{F})^+$, 

$$
\int\lim\inf f_n\mathrm{d}\mu\leq\lim\inf\int f_n\mathrm{d}\mu
$$

### Proof of Fatou's Lemma

$\lim\inf f_n=\lim_k g_k$, where $g_k=\inf_{n\geq k}f_n$. We have $\mu(g_k)\leq\inf_{n\geq k}\mu(f_n)$. Using the MCT, 

$$
\lim\mu(g_k)=\mu(\lim_k g_k)=\mu(\lim\inf f_n)
$$

Therefore, $\lim\inf\mu(f_n)\geq\mu(\lim\inf f_n)$.

## Definition 3 ($\mu$-integrable functions)

Let $f\in\mathcal{F}$ and define $f^{+}(\omega)=\max\\{0,f(\omega)\\},f^{-}(\omega)=\max\\{0,-f(\omega)\\}$. Thus $f=f^{+}-f^{-}$ and $\lvert f\rvert=f^{+}+f^{-}$. $\mu(\lvert f\rvert)=\mu(f^{+})+\mu(f^{-})$. We say $f$ is integrable if $\mu(\lvert f\rvert )<\infty$. In this case, we can define $\mu(f)=\mu(f^{+})-\mu(f^{-})<\infty$.

The set $\mu$-integrable functions are denoted by $L^1(\Omega,\mathcal{F},\mu)$.

## Theorem 4 (Dominated Convergence Theorem, DCT)

If $(f_n)\_{n\geq1}\in(m\mathcal{F})^{+}$, $f_n\to f$, and that $\exists g\in L^1(\Omega,\mathcal{F},\mu),\text{s.t. }\lvert f_n\rvert \leq g,\forall n\geq 1$, then $f\in L^1(\Omega,\mathcal{F},\mu)$ and $\mu(f)=\lim_n\mu(f_n)$.

### Proof of DCT

$\lvert f\rvert \leq g\implies\mu(\lvert f\rvert )\leq\mu(g)<\infty$. Since $g+f_n\geq0$, Fatou's Lemma yields that

$$
\int(g+f)\mathrm{d}\mu\leq\lim\inf\int(g+f_n)\mathrm{d}\mu=\lim\inf\left(\int g\mathrm{d}\mu+\int f_n\mathrm{d}\mu\right)=\int g\mathrm{d}\mu+\lim\inf\int f_n\mathrm{d}\mu.
$$

Thus, 

$$
\int f\mathrm{d}\mu\leq\lim\inf\int f_n\mathrm{d}\mu.
$$

On the other side, which is $g-f_n\geq0$. Use Fatou's Lemma again, 

$$
-\int f\mathrm{d}\mu\leq\lim\inf\int-f_n\mathrm{d}\mu=-\lim\sup\int f_n\mathrm{d}\mu.
$$

Therefore, 

$$
\int f\mathrm{d}\mu\geq\lim\sup\int f_n\mathrm{d}\mu.
$$

We have

$$
\int f\mathrm{d}\mu=\lim\sup\int f_n\mathrm{d}\mu=\lim\inf\int f_n\mathrm{d}\mu=\lim\int f_n\mathrm{d}\mu.
$$

**Remark**, in both MCT and DCT, convergence of $f_n$'s to $f$ can be relaxed to a.e. convergence, that is:

$$
\mu(\{\omega:f_n(\omega)\nrightarrow f(\omega)\})=0.
$$

Moreover, in DCT we can instead assume $\lvert f_n\rvert \leq g,\mu\text{-a.e.}$ This is due to the fact that if $\varphi=0,\text{a.e.}$, then $\mu(\varphi)=0$. (**Prove it!!**)

## Definition 4 (Expectation)

Let $X$ be a r.v. on $(\Omega,\mathcal{F},\mathbb{P})$. If $X\in L^1(\Omega,\mathcal{F},\mathbb{P})$, then

$$
\mathbb{E}[X]=\int_\Omega X\mathrm{d}\mathbb{P}.
$$
