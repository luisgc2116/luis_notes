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
Once again, a **sample space** can be thought of as the set of all possible outcomes. Furthermore, the sample space can be tiny or infinite in size. For example, the set of all outcomes in a coin toss is 2, so the sample space $$\Omega = \text{{heads, tails}}$$; the sample space, or set of all outcomes, of a die is 6 given 6 unique faces, $$\Omega = \text{{1,2,3,4,5,6}}$$. However, as an extreme example, the set of all outcomes that atoms can be arranged in the universe can be truly infinite (ever expanding infinite).


### 2. **Event Space** $$\mathcal{F}$$

### - Intuition
Intuitively, we can think of the **event space** as subsets under some conditions from the *event space* that represent our probleem; in other words, we are creating a collection of subsets, where each subset is composed of elements from the *sample space*. 

**How** we create this event space depends heavily on what question we are trying to ask and how we are trying to *represent* that question. The manner with which we represent a question is important because these sets are what we will map probabilities to; if we have irrelevant sets representing our question, we are missrepresenting our problem and the associated probabilities will not mean much. For instance, music you absolutely hate (or even duck sounds disguised as music) in your music sample space are useless, so there's no need to include it in our event space; having $$\mathcal{F}$$ consist of only the songs you already like represents the problem a lot better.


### - Mathematical Perspective
We can think of the **event space** as a collection of subsets composed from the *event space*. An event space $$\mathcal{F}$$ is known as a $$\sigma$$-Algebra over $$\Omega$$. A $$\sigma$$-Algebra are just the subsets of $$\Omega$$ that represent our problem. Formally, $$\mathcal{F}$$ is a collection of subsets of $$\Omega$$ that satisfy the following properties:
1. $$\mathcal{F}$$ may contain the empty set $$\emptyset$$ and $$\Omega$$
2. $$\mathcal{F}$$ is closed under complements: $$A \in \mathcal{F}$$, then $$A^c \in \mathcal{F}$$, where $$A^c = \{ \omega \in  \Omega | \omega \notin A \} $$; $$A^c$$ is the subset of elements not found in the subset $$A$$.
 

Note:
1. Having the complement of a set A written as $$\overline{A}$$ instead of $$A^c$$ makes Morgan's Law closer to its usual written form as: $$\overline{A \cap B} = \overline{A} \cup \overline{B}$$ and $$\overline{A \cup B} = \overline{A} \cap \overline{B}$$. Or even $$\neg(A \cap B) = \neg A \cup \neg B$$ and $$\neg(A \cup B) = \neg A \cap \neg B$$.

Technically, $$\mathcal{F}$$ *can be* the entire possibility of subsets in each problem we are trying to represent, but that is not useful in all representations. For instance, if we had the die example again,  $$\text{ {{},} }$$

If we had the die from the previous example with a sample space of 6, and we asked what the probability was of getting any of the 6 values, (assuming a normal die where each face is equally likely) then we'd have $$P(s \in \mathcal{F})=1/6$$. Our event space here would be $$\text{{{1},{2},{3},{4},{5},{6}}}$$, since each subset would consist of a single unique element from our sample space which represents one face. Another $$\mathcal{F}$$ we can use is the entire possible subsets $$\text{ {{},{1}, {1,2}, ...} }$$. Notice how some of these elements like $$\text{{1,2}}$$ don't even make sense for our what we are representing, so we create our event space $$\mathcal{F}$$ under the conditions that fit our problem.

If we instead wanted to take the space where we want the probability of getting an even face value, then our event space would consist of subsets of the sample space where there are even numbers and another where is not 
(ie. the compliment of the set of even numbers); hence, $$\text{{{2,4,6},{1,3,5}}}$$. The probability of getting a number that is even is then 1/2, since our total event space is 2, and only one set satisfies the original question we were trying to represent.


### 3. **Probability Measure** $$P$$

### - Intuition
The **Probability Measure** $$P$$ gives probabilities to the elements in the event space, $$\mathcal{F}$$. Using our music example, this is just assigning a probability that you will listen to a song in the event space. The total probability among all events in $$\mathcal{F}$$ is 1. 


### - Mathematical Perspective 
The **Probability Measure** $$P$$ is a function that maps an event space $$\mathcal{F}$$ to probabilities, so $$P: \mathcal{F} \rightarrow \mathbb{R}$$. A few properties on P are that:
1. $$P(E) \geq 0$$ for all subsets $$E \in \mathcal{F}$$
2. $$\sum_{s \in \mathcal{F}} P(s) = 1$$
3. $$P(E \cup F) = P(E) + P(F)$$ if $$E \cap F=\emptyset$$ for all subsets $$E,F \in \mathcal{F}$$. Furthermore, we can see this has countable additivity as well: $$A_1, A_2, \dots \in \mathcal{F}$$, the $$P(\bigcup_{i=1}^{\infty} A_i) = \sum_i^{\infty} P(A_i)$$, where $$A_j \cap A_k = \emptyset \text{ if } j \neq k$$.



Using the die example one more time, if your task was to find the probability of getting an even number, you had an event space of the set of even numbers and odd numbers(ie. the set of even number's complement), $$\mathcal{F} = \text{{{2,4,6},{1,3,5}}}$$. Since we have two sets of equal size, we can say that the set of even numbers can be mapped to a probability of $$1/2$$. However, this mapping isn't always so clear, and so you are either given this mapping or you find a way to find that relationship.


**Important Note**:
- If the event space $$\mathcal{F}$$ is discrete, then often $$P$$ is written as $$P(\omega)$$ for some sample in our sample space $$\omega \in \Omega$$. This technically is not correct, since we can ONLY map **events** to **probabilities**. Therefore, this notation is just implicitely saying $$P(\{ s \})$$ for some $$\{ s \} \in \mathcal{F}$$, where $$\mathcal{F}$$ is composed of subset with single, unique elements in $$\Omega$$.



### Sources
[1] Count Bayesie. [Blog](https://www.countbayesie.com/blog/2015/8/30/picture-guide-to-probability-spaces) <br>
[2] Probability space. [Webpage](http://planning.cs.uiuc.edu/node432.html) <br>
[3] Probability Definitions. SFU. [PDF](http://people.stat.sfu.ca/~lockhart/richard/450/02_3/slides/prob_theory/web.pdf) <br>
[4] Introduction to Probability Theory. CalTech. [PDF](http://www.its.caltech.edu/~mshum/stats/lect1.pdf) 


<br/>

|[Index](../../../../) | [Previous](../../../) | [Next](../probabilityreview)|
