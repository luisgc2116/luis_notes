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

|[Index](../../../) |
