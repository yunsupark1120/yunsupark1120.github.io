---
title: Feynman's Trick
date: 2024-03-04 15:42
categories: [Mathematics, Calculus]
tags: [math, integration, partial differentiation, calculus] # TAG names should always be lowercase
math: true
image: assets/img/Calculus/Background.jpg
---

## Introduction

Richard Feynman was a theoretical physicist known for his work in the path integral formulation of quantum mechanics, the theory of quantum electrodynamics, physics of the superfluidity of supercooled liquid helium, and more. His was not only a significant contributor to the field of physics, he also made numerous contribution to the field of mathematics. In this post, I will be introducing one of the most famous tricks in mathematics, Feynman's Trick. Feynman's Trick is a mathematical technique that provides a valuable connection between integration and differentiation. It is often used to simplify complex integrals and to solve partial differential equations.

Prerequisities:

- Fundemental Theorem of Calculus
- Basic understanding in partial differentiation
- Definite integral
- Basic understanding in parameterization

## Differentiating under the integral sign

If $ f(t,x) $ and if the partial derivatives of $ f(t,x) $ with respect to both variables are continuous over the $ [a, b] $ interval, then

$$
\frac{d}{dx} \int_a^b f(t,x) dt = \int_a^b \frac{\partial f}{\partial x} dt
$$

**Example**

let $ f(t,x) = 2xt $, then

- $ \frac{d}{dt} \int\limits_0^1 2xt \, dx = \frac{d}{dt} \left[ x^2t \right]\_0^1 = \frac{d}{dt} (t) = 1 $

- $ \int_0^1 \frac{\partial f}{\partial x} dt = \int_0^1 2t dt = [t^2]\_0^1 = 1 $

### Application

Evaluate the following definite integral

$$ I = \int_0^1 \frac{x-1}{\ln{x}} dt $$

_The logarithm in the denominator makes this integral difficult to evaluate with traditional integration techniques._

Feynman's Trick for integration resolves this problem.

**Feynman's Trick simplifies the integral by differentiating with respect to a parameter that appears in the integral and then integrating it back.**

Let's solve the integral

$$
I = \int_0^1 \frac{x-1}{\ln{x}} dt
$$

using Feynman's Trick.

1. The first step is to parameterize the integral.

   Let

   $$
   I(t) = \int_0^1 \frac{x^{t}-1}{\ln{x}} dx
   $$

   then

   $$
   I = I(1) = \int_0^1 \frac{x-1}{\ln{x}} dx
   $$

2. Differentiate with respect to the parameter

   $$
   \frac{dI(t)}{dt} = \frac{d}{dt} \int_0^1 \frac{x^{t}-1}{\ln{x}} dx = \int_0^1 \frac{\partial}{\partial t} \left( \frac{x^{t}-1}{\ln{x}} \right) dx = \int_0^1 \frac{x^{t}ln{x}}/ln{x} dx = \int_0^1 x^{t} dx = \frac{1}{t+1}
   $$

   Thus,

   $$
   I'(t) = \frac{1}{t+1}
   $$

3. Integrate $ I'(t) $ back to get $ I(t) $.

   By the fundamental theorem of calculus,

   $$ \int_a^b I'(t) dt = I(b) - I(a) $$

   Since $ I(0) = \int_0^1 \frac{1}{\ln{x}} dx = 0 $,

   $ I = I(1) - I(0) = \int_0^1 I'(t)dt = [\ln{t+1}]\_0^1 = \ln{1} - \ln{0} $

4. Finish Evaluation.

   By following the steps, we conclude that

   $$
    I = \int_0^1 \frac{x^{t}-1}{\ln{x}} dt = \ln{2}
   $$

   _This particular solution is referenced from [Feynman's Trick on zackyzz.github.io](https://zackyzz.github.io/feynman.html)._

## Parameterization

The challenging part of Feynman's Trick is to find a suitable parameterization for the integral. The parameterization should be chosen such that the integral becomes easier to evaluate. The parameterization should also be chosen such that the integral can be differentiated with respect to the parameter and then integrated back.

The above integral $ I = \int_0^1 \frac{x-1}{\ln{x}} dt $ was parameterized as $ I(t) = \int_0^1 \frac{x^{t}-1}{\ln{x}} dx $, and the integral was successfully evaluated as the parameter was properly chosen.

However, even for the same integral $ I = \int_0^1 \frac{x-1}{\ln{x}} dt $, there are other options for parameterization.

For example, consider the function $ I(\alpha) = \int_0^1 \frac{x - \alpha}{\ln{x}} dx $. You are encouraged to apply the Feynman's Trick to this integral and evaluate it.

The parameterization with a parameter $\alpha$ only makes the problem more complicated.

As demonstrated, to apply Feynman's Trick, the parameterization should be chosen carefully.

## Conclusion

Feynman's Trick is a powerful technique for particular integrals, especially for integrals that is challenging to solve with traditional methods.The key to applying Feynman's Trick is to find a suitable parameterization for the integral. The parameterization should be chosen such that the integral becomes easier to evaluate. I encourage to solve more practice problems to achive an intuition for choosing the right parameter and become familar with this technique.
