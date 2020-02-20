---
layout: post
title: Introduction to Probability Spaces 
---

When describing something that requires a probabilistic description, we have to define how probability will describe our task. This requires us to define a clear mathmatical description as to how the task can be expressed mathematically through a Probability Triple. The elements of this triple $$(\Omega, \mathcal{F}, P)$$ are defined as follows:

1. $$\Omega$$ - The **sample space** is the set of all possible outcomes.
2. $$\mathcal{F}$$ - An **event space** is a **$$\sigma$$-Algebra** over $$\Omega$$. It is a set of sets composed of the sample space. 
3. $$P$$ - **Probability Measure** that tells us the probability of each element in $$\mathcal{F}$$.

In order to undestand these further, let's try to build a strong intuition first, and then build upon that intuition mathematically.

### 1. **Sample Space** $$\Omega$$ 
### - Intuition
A **sample space** can be thought of as the set of all possible outcomes. Imagine you want to listen to music and you're thinking about which piece of music to choose. Any and all music in your memory can be organized into a set; this is the set of all possible outcomes(songs) that is named the *sample space*.

### - Mathematical Perspective
Once again, a **sample space** can be thought of as the set of all possible outcomes. Furthermore, the sample space can be tiny or infinite in size. For example, the set of all outcomes in a coin toss is 2, so the sample space $$\Omega =$$ {heads, tails}; the sample space, or set of all outcomes, of a die is 6 given 6 unique faces, $$\Omega=$$ {1,2,3,4,5,6}. However, as an extreme example, the set of all outcomes that atoms can be arranged in the universe can be truly infinite (ever expanding infinite).

### 2. **Event Space** $$\mathcal{F}$$

### - Intuition
Intuitively, we can think of the **event space** as subsets under some conditions from the *event space* that represent our probleem; in other words, we are creating a collection of subsets, where each subset is composed of elements from the *sample space*. 

**How** we create this event space depends heavily on what question we are trying to ask and how we are trying to *represent* that question. The manner with which we represent a question is important because these sets are what we will map probabilities to; if we have irrelevant sets representing our question, we are missrepresenting our problem and the associated probabilities will not mean much. For instance, music you absolutely hate (or even duck sounds disguised as music) in your music sample space are useless, so there's no need to include it in our event space; having $$\mathcal{F}$$ consist of only the songs you already like represents the problem a lot better.


### - Mathematical Perspective
We can think of the **event space** as a collection of subsets composed from the *event space*. An event space $$\mathcal{F}$$ is known as a $$\sigma$$-Algebra over $$\Omega$$. A $$\sigma$$-Algebra are just the subsets of $$\Omega$$ that represent our problem. Formally, $$\mathcal{F}$$ is a collection of subsets of $$\Omega$$ that satisfy the following properties:
1. $$\mathcal{F}$$ may contain the empty set $$\emptyset$$ and $$\Omega$$
2. $$\mathcal{F}$$ is closed under complements: $$A \in \mathcal{F}$$, then $$A^c \in \mathcal{F}$$, where $$A^c = \{ \omega \in  \Omega \vert \omega \notin A \} $$; $$A^c$$ is the subset of elements not found in the subset $$A$$.

3. $$\mathcal{F}$$ is closed under countable unions: If $$A_1, A_2, \dots \in \mathcal{F}$$, the $$\bigcup_{i=1}^{\infty} A_i \in \mathcal{F}$$. In other words, the unions of subset found in $$\mathcal{F}$$ are still within $$\mathcal{F}$$. Similarly,  $$\mathcal{F}$$ is also closed under countable intersections:  $$\bigcap_{i=1}^{\infty} A_i \in \mathcal{F}$$. This is a result from De Morgan's Law, which states that $$(A \cup B)^c = A^c \cap B^c$$ and $$(A \cap B)^c = A^c \cup B^c$$ and the previous two properties.

Note:
1. Having the complement of a set A written as $$\overline{A}$$ instead of $$A^c$$ makes Morgan's Law closer to its usual written form as: $$\overline{A \cap B} = \overline{A} \cup \overline{B}$$ and $$\overline{A \cup B} = \overline{A} \cap \overline{B}$$. Or even $$\neg(A \cap B) = \neg A \cup \neg B$$ and $$\neg(A \cup B) = \neg A \cap \neg B$$.

Technically, $$\mathcal{F}$$ *can be* the entire possibility of subsets in each problem we are trying to represent, but that is not useful in all representations. For instance, if we had the die example again,  $$\{ \{ \}, \}$$.


 
### 3. **Probability Measure** $$P$$

### - Intuition
The **Probability Measure** $$P$$ gives probabilities to the elements in the event space, $$\mathcal{F}$$. Using our music example, this is just assigning a probability that you will listen to a song in the event space. The total probability among all events in $$\mathcal{F}$$ is 1. 


### - Mathematical Perspective 
The **Probability Measure** $$P$$ is a function that maps an event space $$\mathcal{F}$$ to probabilities, so $$P: \mathcal{F} \rightarrow \mathbb{R}$$. A few properties on P are that:
1. $$P(E) \geq 0$$ for all subsets $$E \in \mathcal{F}$$
2. $$\sum_{s \in \mathcal{F}} P(s) = 1$$
3. $$P(E \cup F) = P(E) + P(F)$$ if $$E \cap F=\emptyset$$ for all subsets $$E,F \in \mathcal{F}$$. Furthermore, we can see this has countable additivity as well: $$A_1, A_2, \dots \in \mathcal{F}$$, the $$P(\bigcup_{i=1}^{\infty} A_i) = \sum_i^{\infty} P(A_i)$$, where $$A_j \cap A_k = \emptyset \text{ if } j \neq k$$.




### Sources
[1] Count Bayesie. [Blog](https://www.countbayesie.com/blog/2015/8/30/picture-guide-to-probability-spaces) <br>
[2] Probability space. [Webpage](http://planning.cs.uiuc.edu/node432.html) <br>
[3] Probability Definitions. SFU. [PDF](http://people.stat.sfu.ca/~lockhart/richard/450/02_3/slides/prob_theory/web.pdf) <br>
[4] Introduction to Probability Theory. CalTech. [PDF](http://www.its.caltech.edu/~mshum/stats/lect1.pdf) 


<br/>

|[Index](../../../../) | [Previous](../../../) | [Next](../probabilityreview)|
