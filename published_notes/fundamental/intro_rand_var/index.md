---
layout: post
title: Random Variables
date:   2020-02-21 21:46:04
categories: jekyll css
---


A **Random Variable** is a function that maps event spaces to real numbers, so $$X: \mathcal{F} \rightarrow \mathbb{R}$$, where the probability of an event $$s \in \mathcal{F}$$ at some value $$k$$ is defined as $$P(X=k) := P(X(s)=k)$$. 

Let's examine random variables through an example. If we defined an event as flipping a coin 10 times, and we wanted to know the probability of getting 4 heads within those 10 coins in an event, we can write that the number of heads is a random variable, $$X$$, that takes the event of 10 coin flips is expressed as $$P(X=4)$$. Therefore, X is mapping the outcomes of 10 coin flips onto a value, k, that represents the number of heads that occurs in each event.

Notice how $$X$$ can take values between 1-10. For convenience, let's use $$Val(X)$$ to denote the possible values $$X$$ can take, $$Val(X) = \{ 1,2,3,4,5,6,7,8,9,10 \}$$. We also know that the sum the probability of each possible value must add to 1 as such,

$$
\begin{equation}
    \sum_{x \in Val(X)} P(X=x) = 1.
\end{equation}
$$


|[Index](../../../) |
