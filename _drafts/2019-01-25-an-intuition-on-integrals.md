---
layout: post
title:  "An Intuition on the Meaning of an Integral"
date:   2019-01-25
categories: math
comments: true
---

$$\int$$

It is no mistake that the integral symbol looks like the letter "S".  Leibniz meant for this symbol to represent a sum, or more specifically, an infinite sum.  The $\int_{a}^{b}$ symbol essentially takes a certain expression, and adds up every single value of this expression you get when plugging in every value of a certain variable to it.

For example, lets say we want to find:

$$\int_{1}^{2}x^2$$

Notice that there is no $dx$ at the end, this is on purpose.  We will go ahead and assume that we will plug in values to $x$.  It is obvious that if we plug in every single value of $x$ between $1$ and $2$ and add our results together, we are going to get an infinite number.  Our sum could look something like $(1)^2+(2)^2+(1.5)^2+(1.25)^2+(1.75)^2+(1.125)^2+...$ .  This sum increases without bound since we keep on adding terms greater than 1 (and we never run out of terms to add).  If we wanted to express this sum in terms of a summation, we could write:

$$\lim_{n\to\infty}\sum_{i=0}^{n}f(1+\frac{2-1}{n}i) \text{, where } f(x)=x^2$$

Here, ${2-1}$ represents the length of our range we are going over ($x=1$ to $x=2$).  When we divide it by $n$, which represents the total number of terms in our sum, we essentially get a length which is $1/n^{th}$ of our original range.  The $i$ represents the number of the current term in the sum we are on.  Let's for the purpose of visualization say we have 6 terms in our sum, so $n=5$ (since we start at $0$).  So what is happening here is that our first term is $f(1+\frac{2-1}{5}({\color{red} 0}))$, our second term is $f(1+\frac{2-1}{5}({\color{red} 1}))$, our fourth term is $f(1+\frac{2-1}{5}({\color{red} 2}))$... We start at 1, and then add on a certain multiple of $\frac{2-1}{5}$, we then evaluate our function $f$ at this point which gives us the value for the term.  This makes it so that we sweep through the range we are integrating as $i$ (red) goes up.  When $n$ goes to infinity, each $i$ increment is infinitely small.

The way that we get around our integrals all being infinity is by multiplying them by a $dx$.  $dx$ represents an infinitely small number, which means that it is a number that is smaller than all positive real numbers but greater than $0$.  $dx$