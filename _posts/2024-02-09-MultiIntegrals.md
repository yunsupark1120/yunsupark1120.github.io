---
title: Vector Integral Theorems Summary
date: 2024-02-09 00:23
categories: [Mathematics, Calculus]
tags: [vector, integral, math, multivariable, calculus] # TAG names should always be lowercase
math: true
image: assets/img/Calculus/Background.jpg
---

## Introduction

In this post, I will be introducing the extension of the fundamental theorem of calculus, and the summary of the useful theorems for integrals in vector field: _Green's Theorem_, _Divergence Theorem_, and _Stokes' Theorem_

Prerequsites:

- Undersatnding in multivariable integrals
- Understanding in Vector Field
- Understanding in gradient of multivarible functions
- Understanding in Curl and Divergence of Vector Field

## Fundamental Theorem of Line Integrals

If a vector field $$\vec{F} $$ is conservative, then the line integral through a curve $$C$$ depends only on the endpoints of $$C$$. Mathematically, this can be expressed as:

$$
\int_C \vec{F} \cdot d\vec{r} = f(\vec{r}(b)) - f(\vec{r}(a))
$$

where $$ f $$ is the potential function for $$ \vec{F} $$.

The theorem is particularly useful in physics when calculating work done by a force field in moving an object along a path.

## Green's Theorem

Let $$ C $$ be a positively oriented, piecewise smooth, simple, closed curve, and let $$ \vec{F} $$ be a vector field where $$ \vec{F}(x, y) = \langle M(x, y), N(x, y) \rangle $$. Let $$ D $$ be the region enclosed by the curve. If $$ M $$ and $$ N $$ have continuous first-order partial derivatives on $$ D $$, then Green's Theorem states:

$$
\oint_C (M dx + N dy) = \iint_D \left(\frac{\partial N}{\partial x} - \frac{\partial M}{\partial y}\right) dA = \iint_D (\nabla \times \vec{F}) \cdot \vec{k} \, dA
$$

where $$ M $$ and $$ N $$ are functions of $$ x $$ and $$ y $$ with continuous partial derivatives in $$ D $$. Green's Theorem can be applied to determine the circulation and flux of a fluid across a region.

## Divergence Theorem

Let $$ E $$ be a simple solid region and $$ S $$ be the boundary surface of $$ E $$ with positive orientation. Let $$ \vec{F} $$ be a vector field whose components have continuous first-order partial derivatives. Then,

$$
\iint_{S} \vec{F} \cdot d\vec{S} = \iiint_{E} \text{div} \vec{F} \, dV
$$

This applies, for example, to calculating the net flow of fluid through a surface.

## Stokes' Theorem

Let $$ S $$ be an oriented smooth surface that is bounded by a simple, closed, smooth boundary curve $$ C $$ with positive orientation. Also let $$ \vec{F} $$ be a vector field then,

$$
\oint_{C} \vec{F} \cdot d\vec{r} = \iint_{S} \text{curl} \vec{F} \cdot d\vec{S}
$$

Stokes' Theorem allows analysis of rotational effects in fluid flow or magnetic fields.

## Applications

In this section, I will provide a detailed example of the situation where one of the theorems can be applied. Consider a situation of analyzing airflow in a room with an air conditioning system. By representing the airflow with a velocity field $$ \vec{F} $$, the divergence $$ \nabla \cdot \vec{F} $$ quantifies the net airflow rate out of a volume. Integrating this over the room's volume $$ V $$ gives the total airflow rate, which, by the Divergence Theorem, equals the flux through the room's boundary surface $$ S $$:

$$
\iiint_{V} (\nabla \cdot \vec{F}) \, dV = \iint_{S} \vec{F} \cdot d\vec{S}
$$

The left side of the equation represents the total source strength within the room, while the right side represents the total airflow across the room's boundary. This can help in designing efficient ventilation systems by ensuring the balance between the air introduced and the air exhausted, thus maintaining air quality and proper pressurization.
