---
title: "Opponent Modeling in Deep Reinforcement Learning"
excerpt: "Learning policies which adapt to the opponent's strategy by giving information about the opponent along with the state as input to a Deep Q network"

---
The paper is available here: [He He et al. 2016](https://arxiv.org/abs/1609.05559)

Deep reinforcement learning approaches like Deep-Q networks assume that the agent's environment is stationary, that is, it behaves in a predictable (if stochastic) manner. 
In a multi-agent setting, however, this assumption can only be justified if the other agents are all playing with fixed strategies (which can then be modeled as a part of the transition function of the environment itself). 
Realistically, though, all the agents will be continuously learning and adapting their strategies according to what others are doing - to increase their own payoff in a competitive setting, or to increase the common payoff in a cooperative setting. In the complex continuous action and observation spaces of the real world, it is highly unlikely they will ever reach a stable equilibrium situation from which no agent has any incentive to deviate. 
<br>
The optimal policy for any agent depends on its opponents' policies as well. This paper basically studies two methods by which we can combine features from the state and the opponent as input to a neural network (called the Deep Reinforcement Opponent Network, or DRON) which is learning the Q-values.

The first method, which is DRON-Concat just concatenates learned representations of the state and opponent features, and then lets one MLP layer model the interaction between them. The second method, which is DRON-MixtureOfExperts (DRON-MoE) learns one expert Q-network for tackling each type of opponent that it thinks it will encounter. Effectively, one network models the probability distribution over opponent type, and this probability is used to weight the outputs given by the expert networks to get one final Q-value. 

The experimental results in the paper are in simple 1v1 settings, with hand-crafted state and opponent features. They show that taking opponents' information into account definitely improves performance, and the mixture of experts model usually works better than the concatenation model. 

Takeaway
========
1. Giving information about the opponent to your DQN improves performance against an adaptive opponent.
2. Extra (explicit) supervision in the opponent network (might) help generate more discriminatory representations of the opponent.
