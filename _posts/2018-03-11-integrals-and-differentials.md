---
layout: post
title:  "An Intuition on Why Integrals and Derivatives Are Related"
date:   2019-03-11
categories: math
comments: true
---
The integral of an expression $f(x)$ from $a$ to $b$, written:

$$\int_{a}^{b} f(x) dx$$

 represents the sum of all of the values of $f(x)$ when $x$ varies between $x=a$ and $x=b$ multiplied by the change in $x$ between, or the $x$ distance between values, $dx$.  In the case of an integral, these chosen values are all of the values of $f(x)$ between $a$ and $b$, making $dx$ infinitely small.  The integral could also be informally written as $dx \int_{a}^{b} f(x)$, where $dx$ is the spacing used in the integral.

The derivative of an expression $f(x)$, written:

$$\frac{d[f(x)]}{dx}$$

represents a change in the value of the function $f$ caused by a change in $x$, divided by said change in $x$, where this change in $x$ is infinitely small.  $d[f(x)]$ is just shorthand for $f(x+dx)-f(x)$.

So, let's set up an equality $\frac{d[f(x)]}{dx} = f'(x)$, which just means $f'(x)$ is the derivative of $f(x)$.  If we multiply $dx$ to the other side, we get $d[f(x)] = f'(x) dx$, which is important for the next step.  Now, since the 2 sides of the equation are equal, we can add up all of the values of each side from $x=a$ to $x=b$, which is the same as taking the integral from $a$ to $b$ of each side, as shown above: $\int_{a}^{b} d[f(x)] = \int_{a}^{b} f'(x) dx$.  It is important to remember here that all the integral does is add up all of the values of an expression you get from plugging in numbers to $x$ (or whatever variable you choose).  The reason we don't always get an infinite number is because we usually multiply every value by $dx$, which happens to be infinitely small.  

Let's look at the left hand side of the equation:

$$\int_{a}^{b} d[f(x)]$$

$d[f(x)]$ is just shorthand for $f(x+dx)-f(x)$, so when we evaluate this expression at a certain $x$, it gives us the change in $f(x)$ caused by a change of $dx$ in $x$.  So what would happen if took the value of this expression at every $x$ between $a$ and $b$ and add them all up?  If we add up all of the changes the function goes through, we are pretty much tracing the exact path the function took as it went from $x=a$ to $x=b$.

If we assume for the sake of visualization that there are increments of $dx$ on the graph, we can visualize adding the changes like this:

<iframe src="https://www.desmos.com/calculator/huynuacfce?embed" width="700px" height="500px" style="border: 1px solid #ccc" frameborder="0"></iframe>



Notice that the sum of all of the changes is simply the difference between the endpoints of the graph, that is: $f(b)-f(a)$.  replacing $\int_{a}^{b} d[f(x)]$ with $f(b)-f(a)$, we now have the equation $f(b)-f(a) = \int_{a}^{b} f'(x) dx$.  Remember before we said that $\frac{d[f(x)]}{dx} = f'(x)$, meaning $f'(x)$ is the derivative of $f(x)$.  This means that when we take the integral of a derivative of a function, we can use that function to find the value of the integral, because the integral and derivative "cancel out" in a way.

Here is a brief summary:

|Step                                                          |Explanation                                   |
|--------------------------------------------------------------|----------------------------------------------|
|$\displaystyle \frac{d[f(x)]}{dx} = f'(x)$                    |Start                                         |
|$\displaystyle d[f(x)] = f'(x) dx$                            |Multiply by $dx$                              |
|$\displaystyle \int_{a}^{b} d[f(x)] = \int_{a}^{b} f'(x) dx$  |Integrate Both Sides                          |
|$\displaystyle f(b)-f(a) = \int_{a}^{b} f'(x) dx$             |Rewrite the left hand side: <br> $\displaystyle \int_{a}^{b} d[f(x)]=f(b)-f(a)$|  

<br>

Another way of looking at the relation is through examining what the derivative and integral are supposed to tell us about a function.  One of the reasons that it is hard to understand why an derivative and integral are connected is because they are actually telling you facts about 2 different functions.  Let's say we have a function $f$, and its derivative $f'$.  This means $f'(x)$ is supposed to tell you how a function is changing at a certain $x$.  The integral of $f$ wouldn't help conceptualtize what the integral is trying to find.  The integral of $f'$ helps us more in this case.  

Saying that "the integral" is the inverse of the derivative is somewhat misleading, as the integral is really just an infinite sum.  The essential part of an integral expression that makes it the inverse of a derivative is the $dx$ part, the fact that we multiply every term in the infinite sum by an infinitely small change in $x$.  When we take $\int_{a}^{b} f'(x) dx$, what we are finding is a sum of many rates of change in $f$ times a small distance.  If we look at this from  a more familiar perspective, when we multiply a slope of a function by a distance, we are essentially finding how far up or down that function went in that distance.  The same is true for what we are doing in our integral, except the distance happens to be infinitely small.  When we add up all of the slopes of $f$ times a distance $dx$, we are essentially adding up all of the changes up or down $f$ goes through on its course from $a$ to $b$.  Another way to find this number would be to just find the difference between $f(a)$ and $f(b)$.

