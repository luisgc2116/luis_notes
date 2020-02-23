---
layout: post
title: Random Variables
date:   2020-02-21 21:46:04
categories: jekyll css
---

*Under Construction*


A **Random Variable** is a function that maps event spaces to real numbers, so $$X: \mathcal{F} \rightarrow \mathbb{R}$$, where the probability of an event $$s \in \mathcal{F}$$ at some value $$k$$ is defined as $$P(X=k) := P(X(s)=k)$$. 

Let's examine random variables through an example. If we defined an event as flipping a coin 10 times, and we wanted to know the probability of getting 4 heads within those 10 coins in an event, we can write that the number of heads is a random variable, $$X$$, that takes the event of 10 coin flips is expressed as $$P(X=4)$$. Therefore, X is mapping the outcomes of 10 coin flips onto a value, k, that represents the number of heads that occurs in each event.

Notice how $$X$$ can take values between 1-10. For convenience, let's use $$Val(X)$$ to denote the possible values $$X$$ can take, $$Val(X) = \{ 1,2,3,4,5,6,7,8,9,10 \}$$. We also know that the sum the probability of each possible value must add to 1 as such,

$$
\begin{equation}
    \sum_{x \in Val(X)} P(X=x) = 1.
\end{equation}
$$

### Expected Value

Expanding on the previous concept, if we wanted to know a value we could expect to see the most given the probabilities, we can do so with the **Expected Value**.

Take once again the sum of all the values of X, $$\sum_{x \in Val(X)} P(X=x) = 1$$. We know that each probability is in the range from 0 to 1, then $$0 \leq P(X=x) \leq 1$$, and so if we multiplied the values $$x$$ with their respective $$P(X=x)$$, expressed as $$\sum_{x \in Val(X)} xP(X=x)$$, we would have a new relationship with a range between $$[\text{min}(Val(X), \text{max}(Val(X)]$$. 

We can get a clearer view by looking at the edge cases of this relationship. Say $$X$$ takes values between 1-10, but the value 9 has a probability of 1 while the rest of the values have 0 probability. The sum is then 

$$
\begin{align} 
    \sum_{x \in Val(X)} xP(X=x)
        &= 1P(X=1) + \dots + 9P(X=9) + 10P(X=10) \\
        &= 9P(X=9) \\
        &= 9
\end{align} 
$$

Now let's instead say value 7 and 2 have probabilities 0.5 each, now we have 
$$
\begin{align} 
    \sum_{x \in Val(X)} xP(X=x)
        &= 1P(X=1) + \dots + 9P(X=9) + 10P(X=10) \\
        &= 2P(X=2) + 7P(X=7) \\
        &= 4.5
\end{align} 
$$

*One way* perspective we can take is that values act like *weights* to the probabilities, that scale them to a resulting value between the minimum and maximum values. The resulting value is then a predicted value, or weighted value. Notice how this value is in the min/max range of the values, but doesn't actually have to be within the set of values $$x \in Values(X)$$. This is in part because this is a prediction, or an expectation of a value, which why it is named an **Expected Value**. 

However, another perspective is that the probabilities themselves are the weights that scale the values to sum between the min/max of the values. Mathematically, this perspective is the one taken, since we can say the weights are normalized(ie. add to 1).

Finally, the expected value then,

$$
\begin{equation}
    \mathbb{E}[X] = \sum_{x \in Val(X)} xP(X=x)
\end{equation}
$$

### Expanding the Intuition of Expected Values

$$
\begin{equation}
    \mathbb{E}_{P(X)}[g(X)] = \sum_{x \in Val(X)} g(X=x)P(X=x)
\end{equation}
$$

**Note:** <br>
You may often see a random variable defined as the mapping between the sample space and $$X: \Omega \rightarrow \mathbb{R}$$, $$P(\Omega=\omega) := P(\{ \omega: X(\omega)=k \})$$. However, as mentioned in the first entry, this is just the notation often used to describe the same thing. This is because the sample space is defined to have the same elements of the event space, and so the collection of sets with the elements of the sample space is denoted with the same notation as the sample space. From now, when we encounter this, we'll call this the **state space**, to indicate the event space.
<br><br>


|[Index](../../../) |
