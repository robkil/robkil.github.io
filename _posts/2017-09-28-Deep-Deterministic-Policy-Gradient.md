---
title: "Deep Deterministic Policy Gradients"
excerpt: "A model-free actor-critic algorithm for continuous control that incorporates experience replay and target networks from DQN to the actor-critic approach to policy gradients"
mathjax: true
categories:
  - paper-summary
tags:
  - Reinforcement Learning
---

The paper is available here: [Lillicrap et al. 2016](https://arxiv.org/abs/1509.02971)

While the DQN algorithm is able to learn good policies in environments with high-dimension observation spaces, it can only handle low-dimensional discrete action spaces. Robot control in the real world has a continuous and high-dimensional action space, to which DQN can't be applied since it requires a maximum over action space at each update step, which would be very expensive in a continuous action space.

**Why can't we simply discretize the action space and be done with it?**
1. Loss of fine control capabilities required for robot manipulation
2. Curse of dimensionality: number of actions increases exponentially with the degrees of freedom of the robot
3. Discretization wastes info about the structure of action space

**The Approach**
Directly builds on the [Deterministic Policy Gradients](http://proceedings.mlr.press/v32/silver14.pdf) work presented by Silver et al. in 2014, by modifying it in much the same way as DQN modified Q-learning. This allows DPG to work with neural network function approximators, allowing large observation and action spaces. The modifications introduced are:
1. Replay buffer: At each timestep, the experience tuple $$s_{t},a_{t},r_{t},s_{t+1}$$ is stored in the replay memory. The actor and critic are updated by sampling a minibatch uniformly from the buffer. This allows the samples used in each update to be somewhat independent, which is essential to the success of our optimization algorithms.
2. Soft target network updates: The Q-network used to calculate target value is updated separately to stabilise learning. Rather than copying the weights directly every few steps, the target network weights $$ \theta' $$ are made to slowly track the learned network $$\theta $$ : $$\theta' = \tau \theta + (1-\tau ) \theta' $$ with $$ \tau << 1$$
3. Batch Normalization: Normalizing each dimension across a minibatch to have zero mean and unit variance helps network learn effectively and eases hyperparameter tuning.
4. Exploration Noise: can be added independently because DDPG is off-policy. In physical control problems with inertia such as those used for the paper's experiments, the [Ornstein-Uhlenbeck process](https://en.wikipedia.org/wiki/Ornstein%E2%80%93Uhlenbeck_process) can be used to generate temporally correlated noise.

**Results**
1. Experiments were done on physical environments simulated in MuJoCo, with actions being the torques applied to actuated joints.
2. Ablation studies confirmed the necessity of target networks and batch normalization.
3. Surprisingly, learning from pixels was often as fast as learning using a low dimensional state descriptor; and often outperformed planning based solvers like iLQG which have full access to the underlying model and its derivatives.
4. Learning on the racing game, [Torcs](http://torcs.sourceforge.net/) was better than prior work but still not very stable.

