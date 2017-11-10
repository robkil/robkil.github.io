---
title: Value Iteration Networks (VINs)
excerpt: A fully differentiable planning module which can learn to plan end to end using backpropagation - NIPS 2016 Best Paper
categories:
  - Paper Summary
tags:
  - Reinforcement Learning
---
This paper, [Value Iteration Networks](https://arxiv.org/abs/1602.02867) won the Best Paper Award at NIPS 2016.

Most work in Deep RL has used neural network architectures that were developed for supervised learning, and don't have any explicit module for planning. Given enough diverse training data and rich policy representation, this has been shown to work - but exploiting the prior we have about the planning computation underlying the behavior will help the system learn faster and become more data-efficient. That's what this paper does by introducing the VIN model.

**VIN Model**


**Key Takeaways**
1. The classic Value-Iteration algorithm can be represented as a Convolutional Neural Network, which can be embedded inside standard feed-forward networks and whose parameters can be learnt by regular backpropagation.
2. 