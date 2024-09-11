---
layout: page
title: Chapter 9 The Central Limit Theorem
description: Lévy's Convergence Theorem and Central Limit Theorem.
importance: 1
category: ST552 Probability and Mathematical Statistics I
related_publications: false
pseudocode: true
---

******

## Theorem 1 (Lévy's Convergence Theorem)

Let $(F_n)$ be a sequence of distribution functions with characteristic functions $(\varphi_n)$, respectively. Suppose $g(\theta)=\lim_{n\to\infty}\varphi_n(\theta)$ exists for all $\theta$, and $g$ is continuous at $\theta=0$. Then, $g=\varphi_F$ for some distribution function $F$, and $F_n\Rightarrow F$.

### Proof of Lévy's Convergence Theorem

Suppose $(F_n)$ is tight, then there exists a subsequence $(F_{n_k})$ s.t. $F_{n_k}\Rightarrow F$ for some distribution function $F$. $\varphi_{F_{n_k}}\rightarrow \varphi_F$ since $e^{i\theta X}$ is bounded and continuous. Thus, $g=\varphi_F$. We want to show that $F_n\Rightarrow F$, and we argue by contradiction:

Suppose there exists a continuity point $x$ of $F$, and a subsequence $\tilde{F}\_n$ s.t. $\lvert\tilde{F}\_n(x)-F(x)\rvert\geq\epsilon$ for some $\epsilon>0$. On the other hand, since $(\tilde{F}\_n)$ is tight, there exists a further subsequence $\tilde{F}\_{n_k}\Rightarrow\tilde{F}$, therefore $\varphi\_{\tilde{F}\_{n_k}}\rightarrow\varphi\_{\tilde{F}}$. But $\varphi\_{\tilde{F}\_{n_k}}\rightarrow\varphi_F$, hence $\varphi_{\tilde{F}}=\varphi_F$, that is $\tilde{F}=F$, i.e. $\tilde{F}_{n_k}\rightarrow F$ at every continuity point of $F$. So, it remains to prove tightness.

First observe that

$$
\varphi_n(\theta)+\varphi_n(-\theta)=2\int\cos(\theta x)\mathrm{d}F_n(x)\in\mathbb{R},
$$

and it is bounded by $2$. Since $g$ is continuous and $g(0)=1$, $\forall\epsilon>0,\exists\delta\text{ s.t. }\lvert 1-g(\theta)\rvert<\epsilon/4$ for $\lvert\theta\rvert<\delta$. Therefore, 

$$
0<\frac{1}{\delta}\int_0^{\delta}(2-g(\theta)-g(-\theta))\mathrm{d}\theta\leq\frac{\epsilon}{2}.
$$

Hence, $\exists n_0,\text{ s.t. }n\geq n_0$,

$$
\begin{aligned}
\epsilon&\geq\frac{1}{\delta}\int_0^{\delta}(2-\varphi_n(\theta)-\varphi_n(-\theta))\mathrm{d}\theta\\
&=\int\frac{1}{\delta}\int_{-\delta}^{\delta}\left(1-e^{i\theta x}\right)\mathrm{d}\theta\mathrm{d}F_n(x)\\
&\geq 2\int\left(1-\frac{\sin(\delta x)}{\delta x}\right)\mathrm{d}F_n(x)\\
&\geq 2\int_{|x|\geq\frac{2}{\delta}}\left(1-\frac{1}{|\delta x|}\right)\mathrm{d}F_n(x)\\
&\geq \int_{|x|\geq\frac{2}{\delta}}1\mathrm{d}F_n(x)\\
&= \mu_n(\{x:|x|<\frac{2}{\delta}\})
\end{aligned}
$$

## Theorem 2 (Central Limit Theorem)

Let $(X_n)$ be i.i.d. with $\mathbb{E}[X]=0$ and $\text{Var}(X)=\sigma^2$. Let $S_n=\sum_{i=1}^n X_i$ and $G_n=S_n/(\sigma\sqrt n)$. Then,

$$
\mathbb{P}(G_n\leq x)\rightarrow\Phi(x)=\frac{1}{\sqrt{2\pi}}\int_{-\infty}^x e^{-\frac{1}{2}y^2}\mathrm{d}y
$$

### Proof of CLT

$\varphi_{G_n}(\theta)\rightarrow\varphi_Z(\theta)$, where $Z\sim N(0,1)$. $\varphi_Z(0)$ is continuous at $\theta=0$.
