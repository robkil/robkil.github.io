---
title: Deep Recurrent Q-Networks (DRQN)
excerpt: Deep Q-Learning with an LSTM, for partially observable MDPs
categories:
  - paper-summary
tags:
  - Reinforcement Learning
---
The paper is available here: [Hausknecht et al. 2015](https://arxiv.org/abs/1507.06527)

**Motivation**
While DQN performs well on Atari games (completely observable), the authors postulate that real world scenarios have incomplete and noisy observation because of partial observability. Adding an LSTM after the conv layers would help the Q-network retain some memory of previous observations,  enabling better decision making. 

**DRQN**
1. Architecture: The DQN architecture is minimally modified: The first fully-connected layer is replaced with a recurrent LSTM layer of the same size. Parameters are learned from scratch.
2. Updates: Backpropagating through a recurrent network requires each backward pass to have many timesteps of game screens and target values. The authors evaluate 2 types of updates: sequential and random, where the sequential updates learn faster because they can carry forward the LSTM hidden state, but violate DQN's independent sample assumption. The random updates are not able to learn as quickly because the hidden state has to be zeroed, but they don't violate the independence assumption. Both strategies are shown to perform well.

**Experiments**
1. DRQN performs well at Atari games with just one input frame per timestep. Having just one input frame makes it impossible for the conv layers to estimate essential quantities like the velocity of the ball in Pong, and the LSTM layer compensates with its hidden state. 
2. Randomly blacking out half the input frames also does not affect the performance significantly.
3. DRQN is more robust against missing information during test time even if it was trained with full state information.
4. Overall, recurrency offers _no systematic advantage_ over stacking observations in the input to conv layers (as done in the original DQN)

**Takeaway**

A recurrent layer can handle partial observability induced by having access to only one frame per timestep, however if these observations were simply stacked and given to a regular DQN, it would be able to perform similarly. 