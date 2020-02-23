---
layout: post
title: Variational Autoencoders
date: 2020-02-19 21:46:04
categories: jekyll css
---

Let's say we are trying to create a model that distinguishes between cats, dogs, horses, and birds - these are states that form our state space. Furthermore, let's say we have labels for each which creates a "ground-truth" probability distribution for each state. For example, if we have a vector where each element is a state, and the first element represents a bird, then the bird state-probability distribution can be represented as a vector, [1,0,0,0]. This is named "ground-truth" since one state contains nearly or complete certainty, so predicted distributions are compared to this distribution$$^1$$. If we name the "ground-truth" probability distribution vectors for each state as $$P_i$$, then we can write entropy as

$$
\begin{align}
    \mathbf{H}(P) &= \sum_{x \in \text{states}} I(P(x)) \cdot P(x)
\end{align}
$$

However, a cleaner notation will help down the line, as so the same equation can be written in the following way

$$
\begin{align}
    \mathbf{H}(P) &= \sum_{i \in \text{states}} I(P_i) \cdot P_i
\end{align}
$$

Let's add to our example by saying we have an untrained model that attempts to predict the state-probability distributions P. The entropy can be calculated in the same manner,

$$
\begin{equation}
    \mathbf{H}(Q) = \sum_{i \in \text{states}} I(Q_i) \cdot Q_i
\end{equation}
$$

What we would like to do is find a way to compare these two distributions in order to use learning (ie. gradient descent or otherwise) to update our model to output vectors closer to P. Notice $$\mathbf{H}(Q)$$ has $$Q_i$$, which is the predicted probability of the state i. This is not favorable since we want to compare the information of the prediction, $$I(Q_i)$$, relative to the ground-truth probability vectors. The entropy of predictions Q *with respect to* P is given the named **Cross-Entropy** and written as

$$
\begin{equation}
    \mathbf{H}(P||Q) = \sum_{i \in \text{states}} I(Q_i) \cdot P_i
\end{equation}
$$

The entropy in $$\mathbf{H}(P)$$ is at it's lowest since our state probability vectors have maximum certainty, and so if we found the entropy difference between the predicted state probability vectors $$\mathbf{H}(Q||P)$$ (ie. the cross entropy of Q *with respect to* P) and $$\mathbf{H}(P)$$ as

$$
\begin{equation}
    \mathbf{KL}(P||Q) = \mathbf{H}(P||Q) - \mathbf{H}(P)
\end{equation}
$$

The given name for this entropy expression is the Kullback Leibler Divergence, $$KL$$, and comes from the names of the mathematicians who pioneered this idea.

A few properties of KL are the following:
1. $$\mathbf{H}(P||Q) - \mathbf{H}(P) \geq 0 $$. This is because $$\mathbf{H}(P)$$ is proposed as the smallest amount of entropy of that system assuming P to be the ground truth.
2. $$\mathbf{KL}(P||Q) \neq \mathbf{KL}(Q||P)$$. This becomes mathematically clearer when written as $$\sum_{i \in \text{states}} I(Q_i) \cdot P_i \neq \sum_{i \in \text{states}} I(P_i) \cdot Q_i$$ since $$I(P_i) \neq I(Q_i)$$. Conceptually, the information from the predicted values Q relative to the ground truth vectors P is not the same as the information from vectors P (which contains the most minimal entropy to begin with) relative to the predicted vectors Q; the latter almost makes no sense.

Notes: <br>
1. Vectors labeled as ground truth, have a single element with a 1. Each element signifies probability, and so the reduced sum equals 1. These single non-zero element vectors are colloquially named "One-Hot-Encoded" vectors.


<br/>

|[Index](../../../) |
