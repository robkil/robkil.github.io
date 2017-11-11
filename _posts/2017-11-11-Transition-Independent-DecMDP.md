---
title: Transition-Independent Decentralized MDPs
excerpt:
categories:
  - paper-summary
tags:
  - Multi-agent Systems
mathjax: true
---
The paper is available here: [Becker et al. 2004](https://jair.org/media/1497/live-1497-2345-jair.pdf)

**Problem Setting**
1. 2 or more cooperative agents solving (mostly) independent local problems
2. Actions taken by one agent don't affect the observation or local state of other agents, and there is no explicit communication
3. The interaction between agents happens implicitly through a global (collective) value/reward function. The value of an activity performed by an agent might depend on activities performed by other agents. For example, in information collection, if one agent has already explored a site then the value of another agent exploring it is zero.
4. Agents can communicate during the planning stage (but not during execution), so the optimal policy must not involve any exchange of information.

**Transition Independence**
First, a definition: _Local State_ for each agent consists of the part of the world state that it observes and affects, and the _external features_ (like weather and time) which affect all agents.

If the new local state of each agent depends only on its previous local state, the action taken by it, and the current external features (world features which affect all agents, like weather or time), then the dec-MDP is said to be transition independent.

**Observation Independence** If each agent's observation depends only on its current and next local state and current action.

**Locally fully observable** If each agent can fully observe its own local state.

**Reward Independece** Individually maximizing local reward functions for each agent also maximizes the global reward function, and each local reward function depends only on local state and actions of that agent.

The rover example used in the paper exhibits transition and observation independence, and is locally fully observable. The reward consists of 2 parts, one of which is a set of local reward functions which are reward independent, and the other is a reward signal the system receives which depends on the action of multiple agents. 
(Note that if the reward were totally independent, the n-agent Dec-MDP could be decomposed into n independent local MDPs)

Results
=======
1. Deciding a Dec-MDP with independent transitions and observations, local full observability and joint reward structure is NP-complete.
2. A coverage set algorithm which finds optimal joint policies for these MDPs by augmenting the reward function of each agent's MDP with info about the global reward and other agent's policy, finding the set of optimal policies for any possible policy of the other agent, and then returning the best policies from both agent's coverage sets. The resulting policy is a Nash equilibrium. It is solved using an iterative hill climbing procedure which converges to a locally optimal solution, and with random restarts is a reasonable approximation to the global optima.
3. The anytime performance of this algorithm is surprisingly good, at least with the rover example presented.