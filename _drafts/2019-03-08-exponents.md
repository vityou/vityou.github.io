---
layout: post
title:  "How Exponents are Extended Past Whole Numbers"
date:   2019-03-08
categories: math
comments: true
---

Everyone knows how to evaluate an exponential expression when the exponent is a whole number, like $5^3$ or $4^{23}$.  All you have to do is multiply the base that many times.  However, this basic idea can be extended to other types of numbers while maintaining consistency and elegance.  Each step we take when extending the exponents allows us to define what we mean by exponent in a more general way.

### Zero

One of the properties of exponential expressions is that when two expressions with the same base are multiplied, their exponents can be added and written as a single exponent:

$$x^mx^n=x^{m+n}$$

The opposite happens with division:

$$\frac{x^m}{x^n}=x^{m-n}$$

However, what happens when $m=n$?  This would mean that $\frac{x^m}{x^n}=\frac{x^m}{x^m}=1$, and $x^{m-n}=x^0$, which implies that $x^0=1$.  This is indeed the case.  Another way to look at sometinhg to the $0^{th}$ power is that repeated multiplication can always start with an implicit $1*...$ at the beginning.  If there are 0 products to be multiplied after the $1$, it simply remains $1$.

### Negative Integers

We can view exponents as a way of relating repeated multiplication to addition: when you multiply by the base, you add $1$ to the exponent.  A logical way to apply this to negative integer exponents would have them relate to repeated division, since division is to multiplication as subtraction is to addition.  This is indeed what mathematicians have chosen.  The process can be viewed as starting at 1, and repeatedly dividing the base.  This gives rise to things like:

$$\frac{x^2}{x^4}=x^{2-4}=x^{-2}=(1/x)/x$$

Since $\require{cancel} \frac{x^2}{x^4} = \frac{\cancel{x} * \cancel{x}}{\cancel{x} * \cancel{x} * x * x} = \frac{1}{x^2} = (1/x)/x$, this is what we would expect.

### Rational Numbers

If we want to have the rule: $x^m*x^n=x^{m+n}$ still apply, things like $9^\frac{1}{2} * 9^\frac{1}{2}=9^{\frac{1}{2} + \frac{1}{2}} = 9^1 = 9$ would have to be true.  This would mean that $9^\frac{1}{2} = \sqrt{9}$, since $ \sqrt{9} * \sqrt{9} = 9 $.  The key idea here is that exponentiation can be thought of as simply relating repeated multiplication with addition/normal numbers.  For example, when multiply another $ 9 $ onto $ 9^2 $, you **add** $1$ to its exponent, and you are relating the repeated multiplication of the base ($9$), with a number ($3$).  For rational exponents less that $1$, we want the exponent to perform something like a fraction of a multiplication.  It turns out that taking $n^{th}$ roots is to repeated multiplication as multiplying by a fraction is to normal numbers.

Here is a simple example: Say we have the number $9$.  When we multiply 9 by $\frac{1}{2}$, we get a number, which when added to $0$, $2$ times, gives us $9$.  This is true for any fraction:  When we have a number $x$, and we multiply $x$ by $\frac{1}{n}$, we get a number which when repeatedly added $n$ times, gives us $x$.

It is the same exact idea for exponents, except that repeated addition is replaced with repeated multiplication.  When we take a number $x$ to the power of $\frac{1}{n}$, we get a number that when **repeatedly multiplied** $n$ times, gives us $x$.  Roots of a number, like $\sqrt[3]{x}$, or $\sqrt[25]{x}$, are defined to be exactly this.  The square root of something is defined to be the number, which when repeatedly multiplied 2 times, gives us that something.  All of this leads to the rule:

$$x^{\frac{1}{n}}=\sqrt[n]{x}$$

### Imaginary Numbers

Let's start with what the imaginary number $i$ actually means.  $i$ represents the square root of $-1$, which means when we multiply it by itself, it reduces to $-1$.  Let's combine this with the idea that we have been using so far: exponents are to multiplication as multiplication is to addition.  So what happens when we multiply something by $i$?  We get a pretty similar number, the only difference being that when we square it, we get a negative number.  So, $ (2i) * (2i)=-4 $.  So the only unique property that $2i$ has, can only be witnessed when we square it.

Remember, we are trying to see how $i$ behaves in multiplication, and then attempting to translate this over to exponentiation.  If the unique property of $2i$ is only revealed through repeated multiplication in the multiplication realm, we should expect that unique properties of $2i$ should be revealed equivalently through repeated exponentiation.  Intuitively, the repeated exponentiation version of $(2i)*(2i)$ would be $(x^{2i})^{2i}$.  Using properties of exponents we find that $(x^{2i})^{2i}=x^{-4}$.