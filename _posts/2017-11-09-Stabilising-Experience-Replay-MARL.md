---
title: Stabilising Experience Replay for MARL
excerpt: Making experience replay work in non-stationary multi-agent settings
categories:
  - paper-summary
tags:
  - Reinforcement Learning
  - Multi-agent Systems
mathjax: true
---
The paper is available here: [Foerster et al. 2015](https://arxiv.org/abs/1702.08887)

**What is Experience Replay (XP)?**
DQN stores experience tuples $$s_{t},a_{t},r_{t},s_{t+1}$$ in the replay memory, and samples randomly from it during training. By removing correlation  between data samples it stabilises training, and increases data efficiency by reusing experience in multiple updates. However, the nonstationary environment in multiagent settings means that the environment dynamics which generated past experience might no longer reflect the current environment ground truth. This would result in the algorithm learning on experience which has been rendered obsolete by a dynamic environment.

**Approach 1: Importance Sampling**
The stored experience is interpreted as _off-environment_ data, and the experience tuple is augmented with the probability of taking the joint action according to the policies at that time. Since the policies of all agents are known at each stage of training, the changes in the environment are completely known - and hence the importance of a particular sample of experience in the current environment can be corrected by accounting for the difference in how likely we are to actually take that joint action in the old and current environments.

The adjustment is exact in fully-observable settings, and approximate in partially-observable ones. Importance sampling, while being unbiased, can introduce high variance. 


**Approach 2: Multi-Agent Fingerprints**
The idea is that the Q-network of any agent could be made stationary if conditioned on the policies of the other agents. Naively this would blow up the environment size, rendering learning unfeasible. However, the policies of the other agents are also being learnt by gradient descent, and are following a line trajectory on a high-dimensional policy manifold. If we are able to tell each agent where along this line the sampled experience came from, that should help in inducing stationarity. The training iteration number, $$e$$ and the exploration rate, $$\epsilon$$ (which typically follows an annealing schedule) together provide the required information about the policies of other agents.

**Experiments**
1. Done on Decentralised StarCraft micromanagement problems.
2. Naive XP does outperform no XP, even in the non-stationary multi-agent setting.
3. Importance Sampling barely outperforms naive XP, because the partial observability of the StarCraft problem increases variance of the importance weights and destabilises learning.
4. Even the very simple fingerprint introduced above dramatically improves performance when using a feedforward policy, demonstrating that it is sufficient to disambiguate the policies of other agents' over the course of training.
5. Combining the 2 approaches does not produce any significantly better results.
6. The recurrent model does not benefit from fingerprinting either, since the hidden states allow it to disambiguate between the policies of other agents'. 

**Takeaway**
Fingerprinting seems to stabilise experience replay and improve performance significantly. It allows the model to generalize between best responses to different policies of the other agents. 
