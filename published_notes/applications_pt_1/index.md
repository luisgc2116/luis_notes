---
layout: post
title: Variational Autoencoders
date: 2020-02-19 21:46:04
categories: jekyll css
---

Let's say we are trying to create a model that distinguishes between cats, dogs, horses, and birds; these are states that form our state space. Furthermore, let's say we have labels for each which creates a "ground-truth" probability distribution for each state. For example, if we have a vector where each element is a state, and the first element represents a bird, then the bird state-probability distribution can be represented as a vector, $$ \[ 1,0,0,0 \] $$. This is named "ground-truth" since one state contains nearly or complete certainty, so predicted distributions are compared to this distribution$$^1$$. If we name the "ground-truth" probability distribution vectors for each state as $$P_i$$, then we can write entropy as


<br/>

|[Index](../../../) |
