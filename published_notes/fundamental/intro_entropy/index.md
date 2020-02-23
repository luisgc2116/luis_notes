---
layout: post
title: Introduction to Entropy and Information
date:   2020-02-19 21:46:04
categories: jekyll css
---

Let's develop our definition for entropy through each layer of concepts. But let's start with a very brief high level description.


**Entropy** is a measure of uncertainty. 

In order to understand how entropy is related to uncertainty, we must first understand what states are and how they related to entropy. States are the possible outcomes of a system, where the total probability of a system is 1. In regards to how uncertainty and states are related, a system with a higher number of states tends to have more uncertainty since each state must be a fraction of 1, and therefore states have less individual probability.

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
<br><br>

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

|[Index](../../../) |
