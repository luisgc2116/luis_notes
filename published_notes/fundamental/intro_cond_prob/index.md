---
layout: post
title: Introduction to Conditional Probability  
date:   2020-02-21 21:46:04
categories: jekyll css
---

Let's expand our intuition for probability. To do so, we have to extend our understanding of sets as well. Recall from the previous entry on Probability Spaces that the glue that held the intuition and mathematical explanations was the concept of sets. 

Currently, we know that probabilities under a Probability Triplet $$(\Omega, \mathcal{F}, P)$$ maps elements of an event space $$\mathcal{F}$$ to probabilities P, which are real numbers in $$\mathbb{R}$$. In order to ease the notation to be more readable, let's say the probability of an event $$A \in \mathcal{F}$$ to be $$P(A)$$.

Now, let's visualize the event space A as a circle, as in Figure 1a. Any element in this circle is part of the set A that has a probability $$P(A)$$. Furthermore, let's say we have a second event space B with elements in B also having probabilities $$P(B)$$. If we assume these circles intersected as in Figure 1b, then the set intersection between $$A $$and $$B$$ is $$A \cap B$$. 

The probability of this intersection then just **seems** to be $$P(A \cap B)$$. But notice how this is ambiguous - the elements in this intersection can have probabilities mapped with respect to $$P(A)$$ and $$P(B)$$. So what are we trying to find with $$P(A \cap B)$$ - the probability of the intersection $$A \cap B$$ with respect to $$P(A)$$ or $$P(B)$$? Both. We want to know the probability of getting this intersection with respect to $$P(A)$$ and $$P(B)$$. The probability of getting both requires us to ask: does it matter if we get $$P(A)$$ before $$P(B)$$, or vice versa? If the answer is no, we say these two probability spaces are **independent**. 

If they are independent, we then find the probability of getting P(A) by multiplying the elements in that intersection with respect to A, with the elements of that intersection with respect to B $$P(A \cap B) = P(A)P(B)$$. But why do we multiply? 

Imagine $$A \cap B$$ contains one element and probability $$P(A)=\frac{1}{N}$$ and $$P(B)=\frac{1}{M}$$, where N and M are the number of elements in A and B, respectively. The total number of possible combinations between all elements in A and B is the number of pairs we can make from them. Since each element of A can be paired to the entire space in B(ie. one element in A can be paired with all of B), the total number of pairs is $$N \cdot M$$. Getting this single pair that satisfies being the intersection between $$A$$ and $$B$$, $$A \cap B$$, is then $$P(A \cap B) = \frac{1}{N \cdot M}$$, which is the same as expressing this as $$P(A \cap B) = \frac{1}{N \cdot M} = \frac{1}{N} \cdot \frac{1}{M} = P(A)P(B)$$. 


<br/>

|[Index](../../../) |
