---
layout: post
title: Introduction to Entropy and Information
date:   2020-02-19 21:46:04
categories: jekyll css
---

Let's build our intuition of *entropy* by layering one concept at a time. Let's start with the first concept:
- **Entropy** is a measure of uncertainty. 

In order to understand how entropy is related to uncertainty, we must first recall what states are. States are the possible outcomes of a system; they are the elements of an event(or outcome) space $$\mathcal{F}$$. *Confusingly*, states are often written as $$\omega \in \Omega$$, however, $$\omega$$ is technically the sample space discussed in [Introduction to Probability Spaces]. Since the event space is a collection of subsets from the sample space, you can think of the event space as being built in such a way where the event space has sets of length one, where that element are the unique elements in the sample space, so $$\omega \in \mathcal{F}$$. This can be a very confusing notation, however, it's just assumed that when you see *states* and $$\omega \in \Omega$$, these state belong to an *event space* that maps to a *probability space*, where the total sum probabilities for all the states in a system is 1. 

In regards to how uncertainty and states are related, a system with a higher number of states tends to have more uncertainty since each state must be a fraction of 1, and therefore states have less individual probability. 

Since entropy is related to the number of states in a system, we can see if we can measure entropy based on the number of states. Let's start with a system that has N states, all with equal probability. We wish to choose a random element from the set of states (ie. sample the state distribution) and use a method to find this state in the state space using the least number of steps. We can choose a naive method to go element by element, but that is incredibly inefficient since it takes N steps. We can instead use the idea of binary search, where we iteratively group the current state in half. If the target state is in one group, you discard the other group and reduce the number of available states by half at each step$$^1$$, $$\frac{N_\text{states}}{2}$$; this approach of dividing the state space by half leads to the most efficient method. After a number of steps, we expect 

$$
\begin{align}
    2^{\text{total # of steps}} &= N_\text{states}.
\end{align}
$$


**Ex1:**
For example, suppose you have a state space composed of the alphabet [A-Z]. If you sample a letter from this state-space, and try to find this sampled letter through a series of yes/no questions using binary search, we can start by asking: is the letter between A-M (ie. the first half of the alphabet)? No, then it must be in N-Z. You can reduce your state space to N-Z and ask again. Is the letter in N-T? Yes, so you can reduce your state space to N-T, and so on. 


Therefore, **Entropy** is a measure of uncertainty. It *relates* to the minimum number of steps to reduce the state space by half until we reach a target state. Note that $$\text{total # of steps}$$ refers to the total number of steps needed to find the target state.

$$
\begin{align}
    2^{\text{total # of steps}_{\text{target_state}}} &= N_\text{states} \\
    \text{total # of steps}_{\text{target_state}} &= \log_2{(N_\text{states})}
\end{align}
$$
$$
\begin{align}
    2^{\text{total # of steps}_{\text{target_state}}} &= N_\text{states} 
\end{align}
$$
$$
\begin{align}
    \text{total # of steps}_{\text{target_state}} &= \log_2{(N_\text{states})}
\end{align}
$$


Often, we don't have $$N_\text{states}$$, and instead have the probabilities for each state. In order to find the relationship above in terms of the probability of each state rather than the set of states, we must try to related the two. We can do this by assuming that each state is unique and equally likely. By doing so we can denote that the probability of a target state as the number of target states over the total number of states, or $$P_{\text{target_state}} = \frac{1}{N_\text{states} }$$. We can use this relationship on the $$\text{total # of steps}$$ as follows$$^2$$,
$$
\begin{align}
    \text{total # of steps}_{\text{target_state}} &= \log_2{(N_\text{states})} \\
        &= \log_2{\bigg(\frac{1}{P_{\text{target_state}}}\bigg)} \\
        &= -\log_2{\bigg(P_{\text{target_state}}\bigg)} 
\end{align}
$$
<br>

We can see that the higher number of total steps is related to a larger number of states. We also know that a higher number of states tends to leads toward more uncertainty; this is because probabilities among those states must add to a total probability of 1, and therefore each state can get smaller fractions of probability. 

Furthermore, a larger number of states can be associated with the **information** of a system; more clearly, the *amount of information we can learn* from a system is greater as the number of states increases. *Information* is often mischaracterized as being a limitless quantity, but in reality if we think of information in a system as something which has a limited amount, then we can see that - the possible amount of information that could be learned from a system is higher when the states in a system are more uncertain (ie. have lower probabilities). Another way to say the same thing is: if we have a system with low probabilities for its states, we have . Conversely, if we have a fully deterministic system where one state has a probability of 1, then we have learn no new information about the system  

For example, a system of one state is completely deterministic, and due to this, we have exhausted the available information we can get from this system and so it gives us no new information anymore. This leads to the inverse relationship between Information and Probability - the more deterministic a system is (ie. states with larger probability values), the less information we are able to learn from it. Lastly, information has a unit assigned to it, named - a *bit*.
$$
\begin{align}
    I_\text{target_state} &= \log_2{\bigg(\frac{1}{P_{\text{target_state}}}\bigg)} \\
    &= -\log_2{\bigg(P_{\text{target_state}}\bigg)} 
\end{align}
$$

Furthermore, let's say we wanted to find the average Information for every state. In other words, we want the average number of minimum steps to get to each state. This average Information (or number of steps) for all states is named **Entropy**. If we denote entropy as $$\mathbf{H}$$, and rephrase $$\text{total # of steps}_{\text{state}}$$ as $$b(\text{state})$$ then we have that the average, or expected value, is 
$$ 
\begin{align}
    \mathbf{E}[g(X)] &= \sum_x g(x) f_X(x)
\end{align}
$$

$$
\begin{align}
    \mathbf{E}[\text{total # of steps}] &= \sum_{x \in \text{states}} \text{total # of steps} \cdot P(x)\\
    \mathbf{E}[b(X)] &= \sum_{x \in \text{states}} b(x) P(x) \\ 
                     &= \sum_{x \in \text{states}} I(x) P(x) \\
                     &= \sum_{x \in \text{states}} \log_2{\frac{1}{P(x)}} P(x)\\
                     &= -\sum_{x \in \text{states}} \log_2{P(x)} \cdot P(x) \\
                     &\equiv \mathbf{H}
\end{align}
$$

$$
\begin{align}
    \mathbf{H} &= -\sum_{x \in \text{states}} P(x) \log_2{P(x)} 
\end{align}
$$


**Entropy** is a measure of uncertainty. It is the average, or expected value, of the minimum number of steps to reduce the state space by half for all states. It is therefore a measure of information, where . For instance, a system with a large number of states that contain low probabilities are able to provide more information if a few of those states contained high probability.

Note: 
1. The binary search algorithm assumes an ordered list, or a list of items that contain information in their positions in order for the pivots to effecively reduce the possible elements by half each iteration.
2. What about when we don't assume equal probabilities for each state, can we still use $$P_{\text{target_state}} = \frac{1}{N_\text{states} }$$?. Yes, but we would relate probability and $$N_\text{states}$$ differently. $$N_\text{states}$$ would be the number of states which *includes* the repeated states based on how probable each state is; ie. this is not a set of unique states any longer. The numerator was 1 before because that's the number of times the state appears in the set. The relationship is therefore, $$P_{\text{target_state}} = \frac{\text{# times state appears}}{N_\text{states}}$$. The main idea is that sum of the probabilities of each state must equal 1, $$\sum_\text{states} P_{\text{target_state}}=1$$. But again, we often don't have $$N_\text{states}$$, and instead have the probabilities for each state so this is often ignored.


[1] Shannon. A Mathematical Theory of Communication. [PDF](http://people.math.harvard.edu/~ctm/home/text/others/shannon/entropy/entropy.pdf)<br>
[2] Aftab, et al. Information Theory: Information Theory and the Digital Age. MIT. [PDF](http://web.mit.edu/6.933/www/Fall2001/Shannon2.pdf)<br>

|[Index](../../../) |
