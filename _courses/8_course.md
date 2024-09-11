---
layout: page
title: Chapter 7 Conditional Expectation
description: Proof of existence and uniqueness of conditional expectation.
importance: 1
category: ST552 Probability and Mathematical Statistics I
related_publications: false
pseudocode: true
---

******

Let $(\Omega,\mathcal{F},\mathbb{P})$ be a probability space. Take $X\in L^1(\Omega,\mathcal{F},\mathbb{P})$, and $\mathcal{G}\subset\mathcal{F}$, where $X$ may not be $\mathcal{G}$-measuable. $\exists\text{a r.v. }Y,\text{s.t.}$

1. $Y\in L^1(\Omega,\mathcal{G},\mathbb{P})$
2. $\mathbb{E}[Y\mathbb{1}_A]=\mathbb{E}[X\mathbb{1}_A],\forall A\in\mathcal{G}$

Moreover, if $\tilde{Y}$ is another r.v. with same properties, $\tilde{Y}=Y,\text{a.s.}$.

## Proof of uniqueness

$$
\mathbb{E}[(Y-\tilde{Y})\mathbb{1}_A]=0,\qquad\forall A\in\mathcal{G}
$$

Noticing $\\{\omega:Y(\omega)-\tilde{Y}(\omega)>0\\}\in\mathcal{G}$.

$$
\mathbb{E}\left[(\tilde{Y}-Y)^+\mathbb{1}_{\{Y-\tilde{Y}>0\}}\right]=0\implies Y=\tilde{Y},\text{ a.s.}
$$

## Proof of existence

Let $X\in L^2(\Omega,\mathcal{F},\mathbb{P})$. By Orthogonal Projection Theorem, $\exists Y\in\mathcal{K}=L^2(\Omega,\mathcal{G},\mathbb{P}),\text{s.t.}$

$$
\mathbb{E}[(X-Y)^2]=\inf\{\mathbb{E}[(X-W)^2]:W\in\mathcal{K}\}\text{ and }\mathbb{E}[(X-Y)Z]=0(\forall Z\in\mathcal{K})
$$

Let $A\in\mathcal{G},\mathbb{1}_A\in\mathcal{K}$. Therefore, $\mathbb{E}[(X-Y)\mathbb{1}_A]=0$.

General case: $X\in L^1$, wlog, $X\geq0$ since otherwise $X=X^+-X^-, X^{\pm}\in L^1$. 

$X_n=X\wedge n\implies\exists Y_n\in\mathcal{K},\text{s.t. }\mathbb{E}[X_n\mathbb{1}_A]=\mathbb{E}[Y_n\mathbb{1}_A]$, take limit of both sides, and use MCT:

$$
\lim_{n\to\infty}\mathbb{E}[Y_n\mathbb{1}_A]=\mathbb{E}[X\mathbb{1}_A]
$$

Look at 

$$
\mathbb{E}[(Y_{n+1}-Y_n)\mathbb{1}_A]=\mathbb{E}[((X\wedge n+1)-(X\wedge n))\mathbb{1}_A]\geq0
$$

$\forall A\in\mathcal{G}:(Y_{n+1}-Y_n)\mathbb{1}\_A\geq0,\text{a.s. on }\mathcal{G}\implies Y_{n+1}-Y_n\geq0,\text{a.s. on }\mathcal{G}$. $Y_n$'s are non-decreasing, using MCT in the dominance of a.s.:

$$
Y(\omega)=\lim\sup Y_n(\omega)
$$

Prove the properties of conditional expectation in Section 9.7 in Williams.
