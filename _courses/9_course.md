---
layout: page
title: Chapter 8 Weak Convergence
description: Weak Convergence, Tightness, Skorokhod Representation, Helly-Bray Lemma.
importance: 1
category: ST552 Probability and Mathematical Statistics I
related_publications: false
pseudocode: true
---

******

## Definition 1 (Characteristic Function)

Let $X\in\mathcal{F}$ on $(\Omega,\mathcal{F},\mathbb{P})$. The characteristic function $\varphi=\varphi_X$ is defined to be the map $\varphi:\mathbb{R}\to\mathbb{C}$, 

$$
\varphi(\theta)=\mathbb{E}[e^{i\theta X}]=\mathbb{E}[\cos(\theta X)+i\sin(\theta X)]=\mathbb{E}[\cos(\theta X)]+i\mathbb{E}[\sin(\theta X)]
$$

## Properties of Characteristic Function

1. $\varphi(0)=1$
2. $\lvert\varphi(\theta)\rvert\leq1$
3. $\theta\to\varphi(\theta)$ is continuous
4. $\varphi_{-X}(\theta)=\varphi_X(\theta)$
5. $\varphi_{aX+b}(\theta)=e^{ib\theta}\varphi_X(a\theta)$

## Theorem 1 (Levy's Inversion Formula)

Let $\varphi$ be the C.F. of a r.v. X with law $\mu$, and distribution function $F$. Then, for $a<b\in\mathbb{R}$, 

$$
\begin{aligned}
&\lim_{T\uparrow\infty}\int_{-T}^{T}\frac{e^{i\theta a}-e^{i\theta b}}{i\theta}\varphi(\theta)\mathrm{d}\theta\\
=&\frac{1}{2}[F(b)-F(b-)]-\frac{1}{2}[F(a)-F(a-)]\\
=&\frac{1}{2}(\mu(\{a\})+\mu(\{b\}))+\mu((a,b))
\end{aligned}
$$

**Notations**: 

- $\mathcal{P}(\mathbb{R})$: space of probability measures on $\mathbb{R}$
- $C_b(\mathbb{R})$: space of bounded and continuous functions on $\mathbb{R}$

## Definition 2 (Weak Convergence)

Let $(\mu_n)_{n\in\mathbb{N}}\subset\mathcal{P}(\mathbb{R}),\mu\in\mathcal{P}(\mathbb{R})$. $\mu_n$ converges to $\mu$ weakly $(\mu_n\Rightarrow\mu,\mu_n\xrightarrow{w}\mu)$ if $\mu_n(h)\rightarrow\mu(h),\forall h\in C_b(\mathbb{R})$, i.e. 

$$
\int h\mathrm{d}\mu_n\rightarrow\int h\mathrm{d}\mu
$$

If we use law of X to define weak convergence, then it is defined as the following way. If $\mu_n$ is the law of $X_n$ and $\mu$ is the law of $X$. $X_n\Rightarrow X$ (convergence in distribution) if $\mu_n\Rightarrow\mu$, i.e., 

$$
\mathbb{E}[h(X_n)]\rightarrow\mathbb{E}[h(X)],\qquad h\in C_b(\mathbb{R})
$$

## Theorem 2

Suppose $(X_n)\_{n\in\mathbb{N}}$ and $X$ are r.v.'s on $(\Omega,\mathcal{F},\mathbb{P})$. Then

1. $X_n\xrightarrow{\text{a.s.}} X$, then $X_n\Rightarrow X\ (F_{X_n}\Rightarrow F_X)$
2. $X_n\xrightarrow{p} X$, then $X_n\Rightarrow X$

### Proof of Theorem 2.1

Suppose $h\in C_b(\mathbb{R})$, 

$$
\lim\mathbb{E}[h(X_n)]\overset{\text{DOM}}{=}\mathbb{E}[\lim h(X_n)]\overset{\text{Continuity}}{=}\mathbb{E}[h(\lim X_n)]\overset{\text{a.s.}}{=}\mathbb{E}[h(X)]
$$

**Example**: Suppose $X_n=1/n,X=0$. Then, we have $\mathbb{E}[h(X_n)]\to\mathbb{E}[h(X)]$. But, 

$$
F_n(0)=\mathbb{P}(X_n\leq0)=0\ (\forall n\in\mathbb{N})\nrightarrow F(0)=\mathbb{P}(X\leq0)=1
$$

Since there is a jump at $X=0$, which is not continuous.

## Lemma 1

Let $(F_n)$ be a sequence of distribution functions. Then, $F_n\Rightarrow F$ iff $F_n(X)\to F(X)$ for every continuity point of $F$.

### Proof of Lemma 1

**"Only if "**: Suppose $F_n\Rightarrow F$, that is $\int h\mathrm{d}\mu_n\to\int h\mathrm{d}\mu$, and let $X$ be a continuity point of $F$. Define a continuous function

$$
h(y):=
\begin{aligned}
\begin{cases}
1,&y\leq x\\
1-\frac{1}{\delta}(y-x),\quad &x<y\leq x+\delta\\
0,&y>x+\delta
\end{cases}
\end{aligned}
$$

Since $\int h\mathrm{d}\mu_n\geq\int\mathbb{1}\_{\\{y\leq x\\}}\mathrm{d}\mu=F_n(x)$, and $\int h\mathrm{d}\mu\leq\int\mathbb{1}\_{\\{y<x+\delta\\}}\mathrm{d}\mu\leq\int\mathbb{1}\_{\\{y\leq x+\delta\\}}\mathrm{d}\mu=F(x+\delta)$, we have

$$
\lim\sup F_n(x)\leq\lim\int h\mathrm{d}\mu_n=\int h\mathrm{d}\mu\leq F(x+\delta)
$$

Therefore, $\lim\sup F_n(x)\leq F(x)$ by right-continuity of $F$. Similarly, define $g(y):=h(y+\delta)$. Since $\int g\mathrm{d}\mu_n\leq\int\mathbb{1}\_{\\{y+\delta<x+\delta\\}}\mathrm{d}\mu_n\leq F_n(x)$, and $\int g\mathrm{d}\mu\geq\int\mathbb{1}_{\\{y+\delta\leq x\\}}\mathrm{d}\mu=F(x-\delta)$, we have 

$$
\lim\inf F_n(x)\geq F(x-\delta)
$$

Hence, $\lim\inf F_n(x)\geq F(x-)=F(x)$ by the existence of left hand limit. 

**"If"**: The "If" part follows from the following theorem.

## Theorem 3 (Skorokhod Representation)

Suppose that $(F_n)_{n\in\mathbb{N}}$ is a sequence of distribution functions on $\mathbb{R}$, that $F$ is a distribution function on $\mathbb{R}$ and that $F_n(x)\to F(x)$ at every point $x$ of continuity of $F$. Then, there exists a probability triple $(\Omega,\mathcal{F},\mathbb{P})$ carrying a sequence $(X_n)$ of r.v.'s and also a r.v. X, such that

$$
F_n=F_{X_n},\quad F=F_X,
$$

and, 

$$
X_n\to X\quad\text{a.s.}
$$

### Proof of Skorokhod Representation

Take $([0,1],\mathcal{B}[0,1],\text{Leb})$, and define

$$
\begin{aligned}
X^+(\omega)&:=\inf\{z:F(z)>\omega\}\\
X^-(\omega)&:=\inf\{z:F(z)\geq\omega\}
\end{aligned}
$$

and define $X_n^+,X_n^-$ similarly. We know that $\mathbb{P}(X^+=X^-)=1$. Fix $\omega$. Let $z$ be a non-atom (continuous point) of $F$ with $z>X^+(\omega)$. Then $F(z)>\omega$, and hence, for large $n$, $F_n(z)>\omega$, so that $X_n^+(\omega)\leq z$. So $\lim\sup_nX_n^+(\omega)\leq z$. But (since non-atoms are dense), we can choose $z\downarrow X^+(\omega)$. Hence, 

$$
\lim\sup X_n^+(\omega)\leq X^+(\omega)
$$

and, by similar arguments, 

$$
\lim\inf X_n^-(\omega)\geq X^-(\omega)
$$

Since $X_n^-\leq X_n^+$ and $\mathbb{P}(X^+=X^-)=1$, the result follows.

## Lemma 2 (Helly-Bray, Sequential Compactness for $\mathcal{P}(\bar{\mathbb{R}})$)

Let $(F_n)\_{n\in\mathbb{N}}$ be any sequence of distribution functions on $\mathbb{R}$. Then, there exists a right continuous, non-decreasing function $F$ on $\mathbb{R}$, such that $0\leq F\leq 1$ and a subsequence $(F_{n_k})$, such that 

$$
\lim_{k\to\infty}F_{n_k}(x)=F(x),\quad\text{for every continuity point of }F
$$

**Remark**: $F$ is not necessary DF, since $F(-\infty)$ is not necessary 0 and $F(\infty)$ is not necessary 1.

### Proof of Helly-Bray Lemma

Take a countable dense set $C$ of $\mathbb{R}$ and label it:

$$
C=\{c_1,c_2,c_3,\cdots\}
$$

Since $(F_n(c_1))\_{n\in\mathbb{N}}$ is a bounded sequence, it contains a convergent subsequence $(F_{n(1,j)}(c_1))$:

$$
F_{n(1,j)}(c_1)\to H(c_1)\quad \text{as }j\to\infty
$$

In some subsequence of this subsequence, we shall have

$$
F_{n(2,j)}(c_2)\to H(c_2)\quad\text{as }j\to\infty
$$

and so on. If we put $n_i=n(i,i)$, then we shall have:

$$
h(c):=\lim F_{n_i}(c)\text{ exists for every }c\text{ in }C.
$$

Obviously, $0\leq H\leq 1$, and $H$ is non-decreasing on $C$. For $x\in\mathbb{R}$, define

$$
F(x):=\lim_{c\downarrow\downarrow x}H(c)
$$

Where $\downarrow\downarrow$ signifying that $c$ decreases strictly to $x$ through $C$. (In particular, $F(c)$ need not equal $H(c)$ for $c$ in $C$.)

## Definition 3 (Tightness)

A sequence $(F_n)$ of distribution functions is called tight if,$\forall\epsilon>0,\exists K>0$, s.t.

$$
\mu_n[-K,K]=F(K)-F(-K-)>1-\epsilon
$$

The idea is that tightness stops mass being pushed out to $+\infty$ or $-\infty$.

## Lemma 3

Suppose that $(F_n)$ is a sequence of distribution functions.

1. If $F_n\xrightarrow{w}F$ for some distribution function $F$, then $(F_n)$ is tight.
2. If $(F_n)$ is tight, then there exists a subsequence $(F_{n_i})$ and a distribution function $F$ such that $F_{n_i}\xrightarrow{w}F$.
