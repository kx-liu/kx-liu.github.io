---
layout: page
title: Chapter 5 Lᵖ Space
description: $L^p$ Spaces, Important inequalities, Orthogonal Projection Theorem.
importance: 1
category: ST552 Probability and Mathematical Statistics I
related_publications: false
pseudocode: true
---

******

## Jensen's Inequality

Let $\varphi:\mathcal{G}\to\mathbb{R}$, $\mathcal{G}\subset\mathbb{R}$ is an open interval, $\varphi$ is convex. Then if $X,\varphi(X)\in L^1(\Omega,\mathcal{F},\mathbb{P})$, then

$$
\mathbb{E}(\varphi(X))\geq\varphi(\mathbb{E}(X))
$$

provided $\mathbb{P}(X\in\mathcal{G})=1$.

## Definition 1 ($L^p$ norm)

If $X\in L^p(\Omega,\mathcal{F},\mathbb{P})$, that is $\mathbb{E}[\lvert X\rvert^p]<\infty$, then

$$
\lVert X \rVert_p=\left\{\mathbb{E}(\lvert X\rvert^p)\right\}^{\frac{1}{p}}
$$

## Proposition

For $1\leq p\leq r<\infty$, if $Y\in L^r$, then $Y\in L^p$ and $\lVert Y \rVert_p \leq \lVert Y \rVert_r$

### Proof of proposition

Let $(\lvert Y\rvert \wedge n):=\min\\{\lvert Y\rvert, n\\}$. Define $X_n:=(\lvert Y\rvert \wedge n)^p,\forall n$, which is a bounded r.v.. Therefore, $X_n,X_n^{r/p}\in L^1$. $\varphi(X)=X^{r/p}$ is a convex function. Using the Jensen's inequality, 

$$
[\mathbb{E}(X_n)]^{\frac{r}{p}}\leq\mathbb{E}[X_n^{\frac{r}{p}}]\leq\mathbb{E}[\lvert Y\rvert^r]
$$

Using MCT, 

$$
[\mathbb{E}(\lim X_n)]^{\frac{r}{p}}=\mathbb{E}[\lvert Y\rvert^p]\leq\mathbb{E}[\lvert Y\rvert^r]
$$

## Holder's Inequality

If $p>1,f\in L^p,g\in L^q,\frac{1}{p}+\frac{1}{q}=1$, then

$$
\lVert f\cdot g \rVert_1\leq\lVert f \rVert_p \lVert g \rVert_q
$$

### Proof of Holder's Inequality

Let $(\Omega,\mathcal{F})$, assume $f,g\geq0$, 

$$
\mathbb{Q}(A):=\frac{\mathbb{E}[f^p\mathbb{1}_A]}{\lVert f \rVert_p^p}
$$

is a probability measure (**Prove it!!**).  Suppose

$$
u:=\frac{g}{f^{p-1}}\mathbb{1}_{\{f>0\}}
$$

Since $q>1$, Jensen's inequality yields

$$
\frac{\mathbb{E}\left[\frac{g^q}{f^{q(p-1)}}\mathbb{1}_{\{f>0\}}f^p\right]}{\lVert f \rVert_p^p}
\geq\frac{\left(\mathbb{E}[\frac{g}{f^{p-1}}\mathbb{1}_{\{f>0\}}f^p]\right)^q}{\lVert f \rVert_p^{pq}}
$$

Noticing $\frac{1}{p}+\frac{1}{q}=1\implies p+q=pq\implies p+q-pq=0$, we have

$$
\mathbb{E}[g^q]\cdot\lVert f \rVert_p^q\geq (\mathbb{E}[g\cdot f])^q
$$

## Corollary

If $f,g\in L^p$, then

$$
\lVert f\cdot g \rVert_1\leq\lVert f \rVert_2 \lVert g \rVert_2
$$

## Minkowski's Inequality

If $f,g\in L^p$, then $\lVert f+g \rVert_p\leq\lVert f \rVert_p+\lVert g \rVert_p$.

### Proof of Minkowski's Inequality

If $p=1$, obvious.

If $p>1$, $\lvert f+g\rvert^p=\lvert f+g\rvert \lvert f+g\rvert^{p-1}\leq\lvert f+g\rvert^{p-1}(\lvert f\rvert+\lvert g\rvert)$. Set $q:\frac{1}{p}+\frac{1}{q}=1$, 

$$
\begin{aligned}
\lVert f+g \rVert_p^p&=\int \lvert f+g\rvert^p\mathrm{d}\mathbb{P}\\
&\leq\lVert f \rVert_p\left(\int \lvert f+g\rvert^{(p-1)q}\mathrm{d}\mathbb{P}\right)^\frac{1}{q}+\lVert g \rVert_p\left(\int \lvert f+g\rvert^{(p-1)q}\mathrm{d}\mathbb{P}\right)^\frac{1}{q}\\
&=\left(\lVert f \rVert_p+\lVert g \rVert_p\right)\left(\int \lvert f+g\rvert^{p}\mathrm{d}\mathbb{P}\right)^\frac{1}{q}\\
&=\left(\lVert f \rVert_p+\lVert g \rVert_p\right)\lVert f+g \rVert_p^{p/q}
\end{aligned}
$$

Remark: Minkowski's inequality shows that $\lVert \cdot \rVert_p$ is a norm:

1. $\lVert \alpha f \rVert_p=\alpha\lVert f \rVert_p,\alpha\in\mathbb{R}$
2. $\lVert f \rVert=0\implies f=0,\text{a.s.}$

$\lVert \cdot \rVert_p$ is a norm on the equivalence classes of $L^p(\Omega,\mathcal{F},\mathbb{P})$. We say $f$ and $g$ belong to the same equivalence class if $f=g,\text{a.s.}$

## Definition 2 (Cauchy Sequence)

$(f_n)\subset L^p(\Omega,\mathcal{F},\mathbb{P})$ is a Cauchy sequence if $\forall\epsilon>0,\exists M,\text{s.t. }\forall n,m\geq M,\lVert f_n-f_m \rVert_p\leq\epsilon$

## Theorem 1

If $1\leq p<\infty,L^p(\Omega,\mathcal{F},\mathbb{P})$ is a complete normed space; in particular, this means that it is Banach space.

## Theorem 2 (Orthogonal Projection Theorem)

Let $\mathcal{K}\subset L^2(\Omega,\mathcal{F},\mathbb{P})$ be a closed subspace of $L^p(\Omega,\mathcal{F},\mathbb{P})$; i.e. if $f,g\in\mathcal{K}\implies\alpha f\in\mathcal{K},\forall \alpha\in\mathbb{R}$, and if $(f_n)\subset\mathcal{K},f_n\to f$ in $L^2$, then $f\in\mathcal{K}$. Then given $X\in L^2(\Omega,\mathcal{F},\mathbb{P}),\exists Y\in\mathcal{K},\text{s.t.}$:

1. $\lVert X-Y \rVert_2:=\Delta:=\inf\\{\lVert X-W \rVert:W\in\mathcal{K}\\}$
2. $X-Y\perp Z\ (\forall Z\in\mathcal{K})\iff\mathbb{E}(X-Y)Z=0\ (\forall Z\in\mathcal{K})$

### Proof of Orthogonal Projection Theorem

1. $\Delta$ is the distance of $X$ to the subspace $\mathcal{K}\implies$ exists a sequence $(Y_n)\subset\mathcal{K}:\lVert X-Y_n \rVert_2\to\Delta$

   $$
   \lVert X-Y_n \rVert_2^2+\lVert X-Y_m \rVert_2^2=2\lVert X-\frac{1}{2}(Y_n+Y_m) \rVert^2_2+2\lVert \frac{1}{2}(Y_n-Y_m) \rVert_2^2
   $$

   The first term of the r.h.s $\geq\Delta$ since it is a linear vector space. Considering the second term, the distance between $X$ and $Y_m$ are both converging to $\Delta$, 

   $$
   2\lVert \frac{1}{2}(Y_n-Y_m) \rVert_2^2=\lVert X-Y_n \rVert_2^2+\lVert X-Y_m \rVert_2^2-2\lVert X-\frac{1}{2}(Y_n+Y_m) \rVert_2^2\leq2(\Delta^2+\epsilon^2)-2\Delta^2=2\epsilon^2
   $$

   That is $Y_n$ is a Cauchy sequence in $L^2$; but since $L^2$ is complete, therefore $(Y_n)$ converges to an element of $L^2$, and $Y\in\mathcal{K}$. 

   $$
   \lVert X-Y \rVert_2\leq\lVert X-Y_n \rVert_2+\lVert Y_n-Y \rVert_2\to\Delta
   $$

   Therefore, $\lVert X-Y \rVert_2\leq\Delta$. To sum up, $\lVert X-Y \rVert_2=\Delta$

2. Take $Z\in\mathcal{K}:Y+tZ\in\mathcal{K},t\in\mathbb{R}$

   $$
   \lVert X-(Y+tZ) \rVert_2\geq\Delta=\lVert X-Y \rVert_2\implies\lVert X-(Y+tZ) \rVert_2^2\geq\lVert X-Y \rVert_2^2
   $$

   $$
   \lVert X-(Y+tZ) \rVert_2^2=\lVert X-Y \rVert_2^2+t^2\lVert Z \rVert_2^2-2t\mathbb{E}[(X-Y)Z]\geq\lVert X-Y \rVert_2^2
   $$

   Therefore, $t^2\lVert Z \rVert^2_2-2t\mathbb{E}[(X-Y)Z]\geq0$. Let $t=r\text{sgn}(\mathbb{E}[(X-Y)Z]),r>0$. If $\mathbb{E}[(X-Y)Z]>0$, $-r\mathbb{E}[(X-Y)Z]+r^2\lVert Z \rVert_2^2\geq0$. Let $r\to0$, $-2\mathbb{E}[(X-Y)Z]\geq0$, therefore, $\mathbb{E}[(X-Y)Z]=0$.


