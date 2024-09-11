---
layout: page
title: Chapter 10 Mathematical Statistics
description: Parametric v.s. Non-Parametric, Donimated Family, Exponential Family.
importance: 1
category: ST552 Probability and Mathematical Statistics I
related_publications: false
pseudocode: true
---

******

Suppose a probability space $(\Omega,\mathcal{F},\mathbb{P})$. The data set is called a sample from a population described by $\mathbb{P}$. $\mathbb{P}$ is partially unknown. The goal is to deduce properties of $\mathbb{P}$ from the available sample. In particular, the data set $(X_1,X_2,\dots,X_n)$ with sample space $\Omega$ are obtained as i.i.d. observations. Thus, we can define $\mathbf{X}=(X_1,\dots,X_n)$ on $\prod_{i=1}^n(\mathbb{R},\mathcal{B},\mathbb{P})$.  E.g., $\bar{X},S^2$ are product measurable.

**Parametric v.s. Non-Parametric**: A set of probability measures $(\mathbb{P}\_\theta)$ on $(\Omega,\mathcal{F})$ indexed by $\theta\in\Theta$ is said to be a parametric family if $\Theta\subset\mathbb{R}^d$ for some $d$ and $\mathbb{P}\_\theta$ is a known probability measure.

- $(\mathbb{P}\_\theta)$ is said to be identifiable if $\theta_1\neq\theta_2\implies\mathbb{P}\_{\theta_1}\neq\mathbb{P}\_{\theta_2}$.
- Assumption: All parametric families are identifiable.

## Definition 1 (Donimated Family)

Let $\mathcal{P}$ be a family of probability measures and $\nu$ a $\sigma$-finite measure on $(\Omega,\mathcal{F})$. If $\mathbb{P}<<\nu$, i.e. $\mathbb{P}(A)=\int_{\Omega}X_{\mathbb{P}}\mathbb{1}\_A\mathrm{d}\nu$ for all $A\in\mathcal{F}$ and some measurable $X_\mathbb{P}$ for all $\mathbb{P}\in\mathcal{P}$, then $\mathcal{P}$ is said to be dominated by $\nu$. In this case, $\forall\mathbb{P},\exists f_\mathbb{P}$, s.t. $X_\mathbb{P}=f_\mathbb{P}(X)=\partial\mathbb{P}/\partial\nu$.

### Example of donimated family

$k$-dimensional normal distribution $N_k(\boldsymbol{\mu},\Sigma),\boldsymbol{\mu}\in\mathbb{R}^k,\Sigma\in\mathcal{M}_k$. This family is dominated by the Lebesgue measure on $\mathcal{B}^k$.

## Definition 2 (Exponential Family)

$\mathcal{P}=\\{\mathbb{P}_\theta:\theta\in\Theta\\}<<\nu$  is called an exponential family if 

$$
f_{\theta}(x)=\frac{\mathrm{d}\mathbb{P}_\theta(x)}{\mathrm{d}\nu}=\exp\left\{\eta(\theta)\cdot T(x)-\xi(\theta)\right\}h(x),
$$

where $\eta:\Theta\to\mathbb{R}^m,T:\mathbb{R}^n\to\mathbb{R}^m,h:\Omega\to\mathbb{R}_+$, $\xi$ is a normalization constant, and $\cdot$ means dot product.

### Examples of exponential family

- $k=1$

  - $\nu=\text{Leb}\mid\_{(0,\infty)},f_{\lambda}(x)=\lambda e^{-\lambda x}=\exp\\{(-\lambda)x+\log\lambda\\}$
  - $\nu=\text{counting measure on }\mathbb{N}$, $f_\theta(x)=e^{-\lambda}\frac{\lambda^x}{x!}=\exp\\{x\log\lambda-\lambda\\}\frac{1}{x!}$

- $k=2$

  $$
  \begin{aligned}
  f_{\mu,\sigma^2}(x)&=\frac{1}{\sqrt{2\pi}\sigma}\exp\left\{-\frac{(x-\mu)^2}{2\sigma^2}\right\}\\
  &=\frac{1}{\sqrt{2\pi}\sigma}\exp\left\{\frac{\mu}{\sigma^2}x-\frac{x^2}{2\sigma^2}-\frac{\mu^2}{2\sigma^2}\right\}\\
  &=\frac{1}{\sqrt{2\pi}}\exp\left\{\frac{\mu}{\sigma^2}x-\frac{x^2}{2\sigma^2}-\frac{\mu^2}{2\sigma^2}-\log\sigma\right\}
  \end{aligned}
  $$

  where $T(x)=(x,x^2),\eta(\theta)=(\mu/\sigma^2,-1/(2\sigma^2)),\xi(\theta)=\mu^2/(2\sigma^2)+\log\sigma$.

- Cauchy density with center $\mu$, and $\nu=\text{Leb}(\mathbb{R})$: **NOT** an exponential family,  but a location family:

  $$
  f_\mu(x)=\frac{1}{\pi}\frac{1}{1+(x-\mu)^2}
  $$

