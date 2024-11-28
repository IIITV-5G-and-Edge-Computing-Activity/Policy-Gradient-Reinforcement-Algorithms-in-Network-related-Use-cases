# Q-Learning and Policy Gradient Reinforcement Learning for Network Route Optimization

This project applies **Reinforcement Learning (RL)** to the problem of **route optimization in networks**. The goal is to leverage RL algorithms, particularly **Q-Learning** and **Policy Gradient Methods**, to optimize routing decisions in dynamic networks, improving performance metrics like latency, throughput, and congestion.

## Table of Contents
1. [Overview](#overview)
2. [Key Components](#key-components)
3. [Algorithm](#algorithm)
    - [Q-Learning](#q-learning)
    - [Policy Gradient Methods](#policy-gradient-methods)
4. [Methodology](#methodology)
5. [Evaluation](#evaluation)
6. [Future Work](#future-work)
7. [Acknowledgments](#acknowledgments)

---

## Overview

In modern networks, efficient routing is crucial for minimizing latency, avoiding congestion, and ensuring smooth data transfer. This project focuses on **Reinforcement Learning (RL)** to dynamically optimize routing decisions. Initially, we implemented **Q-learning** for route optimization, where the agent learns through trial and error to minimize routing costs. Later, we also explored **Policy Gradient Methods** like **REINFORCE** and **PPO** for handling more complex routing scenarios, such as continuous action spaces and real-time traffic adaptation.

---

## Key Components:
- **Q-Learning**: Model-free RL algorithm used for learning the best routing path based on rewards and penalties.
- **Policy Gradient Methods**: Advanced RL techniques (e.g., REINFORCE, PPO) for optimizing network routing policies with continuous action spaces.

---

## Algorithm

### Q-Learning

1. **Initialize** the Q-table arbitrarily for all states and actions.
2. **Action Selection**: Use an \(\epsilon\)-greedy policy to balance exploration and exploitation.
3. **Update** ### Q-function Formula

The Q-function, \( Q(s, a) \), is updated using the following formula:

\[
Q(s, a) \gets Q(s, a) + \alpha \left[ r + \gamma \min_{a'} Q(s', a') - Q(s, a) \right]
\]

Where:
- \( s \) is the current state,
- \( a \) is the action taken,
- \( \alpha \) is the learning rate,
- \( r \) is the reward received after taking action \( a \) in state \( s \),
- \( \gamma \) is the discount factor,
- \( \min_{a'} Q(s', a') \) represents the minimum Q-value for the next state \( s' \).

4. **Repeat** until the Q-values converge, indicating optimal routing paths.

### Policy Gradient Methods (for future expansion):
Policy gradient methods, like **REINFORCE** or **Proximal Policy Optimization (PPO)**, directly optimize the policy for selecting routing decisions. These methods use a neural network to parameterize the policy, and the objective is to maximize the cumulative rewards by adjusting the policy parameters.

- **REINFORCE**: A Monte Carlo method that optimizes policies by calculating gradients of the expected return.
- **PPO**: A more stable version of policy gradients, which uses a clipped objective function to ensure that the policy does not change too drastically.

---

## Methodology

The methodology of this project involves applying **Q-Learning** and **Policy Gradient methods** to optimize routing in a simulated network environment. Here is the step-by-step process we followed:

### 1. **Problem Formulation**
   The network routing problem was modeled as a **Markov Decision Process (MDP)**. The elements of the MDP are defined as:
   - **States**: Represent the current network configuration or node in the network.
   - **Actions**: Represent the possible routing decisions or next hops.
   - **Rewards**: A higher reward is given for efficient routes (e.g., those minimizing latency, packet loss, or congestion).
   - **Transitions**: Defined by the movement of packets from one node to another based on the selected action.

   The objective was to find an **optimal policy** (\(\pi^*\)) that minimizes the routing cost, maximizing the efficiency of packet flow through the network.

### 2. **Q-Learning Algorithm Implementation**
   The Q-learning algorithm was used to iteratively learn the best routing paths by updating the Q-values for each state-action pair:
   - **Initialize**: The Q-values for all state-action pairs were initialized arbitrarily or to zero.
   - **Action Selection**: The agent used an \(\epsilon\)-greedy policy to select actions, balancing exploration and exploitation.
   - **Update Rule**: The Q-value for the chosen state-action pair was updated using:
     \[
     Q(s, a) \gets Q(s, a) + \alpha \left[ r + \gamma \max_{a'} Q(s', a') - Q(s, a) \right]
     \]
   - **Convergence**: The algorithm iterated over multiple episodes until the Q-values converged, representing the learned optimal policy.

### 3. **Policy Gradient Method Implementation (for future expansion)**
   For handling continuous action spaces and improving adaptability, we planned to implement **Policy Gradient methods**:
   - **Network Architecture**: A neural network was used to parameterize the policy.
   - **Optimization**: Policies were optimized using gradient ascent methods (e.g., REINFORCE or PPO).
   - **Action Selection**: The agent would select actions probabilistically, based on the learned policy, aiming to maximize the expected cumulative reward.

### 4. **Experimental Setup**
   - **Graph Representation**: The network was represented as a directed graph with nodes and edges where edges represent paths with associated costs.
   - **Simulation**: We simulated packet transmission through the network and used Q-learning to optimize the path selection over multiple episodes.
   - **Metrics**: The performance was evaluated based on:
     - **Path Cost**: Total cost of the selected route.
     - **Convergence Time**: The number of episodes required for the agent to stabilize its policy.
     - **Comparison with Traditional Algorithms**: We compared our RL-based approach with traditional algorithms like Dijkstra’s to evaluate improvements in efficiency and adaptability.

---

## Evaluation

After training the Q-learning or Policy Gradient agent, the performance can be evaluated based on:
- **Path Cost**: Total cost of the optimal route.
- **Convergence**: The number of episodes required for the agent to stabilize its policy.
- **Comparison**: Compare RL-based routing against traditional algorithms like **Dijkstra’s** to measure improvement in network performance.

---

## Future Work

- **Scalability**: Apply Deep Q-Networks (DQN) to handle larger networks with complex state-action spaces.
- **Multi-Agent Reinforcement Learning**: Implement multi-agent systems where different network routers act as individual agents collaborating to optimize network-wide routing.
- **Policy Gradient Methods**: Further implement **Proximal Policy Optimization (PPO)** and other policy gradient methods to handle continuous action spaces and improve routing decisions.
- **Integration with SDN**: Explore integrating RL with **Software-Defined Networking (SDN)** for centralized dynamic routing control.

---

## Acknowledgments

We would like to express our sincere gratitude to **Dr. Bhupendra Kumar**, our mentor, for his invaluable guidance and support throughout this project. His insights helped us refine our approach and deepen our understanding of reinforcement learning. We also thank our peers for their collaborative efforts and contributions, which greatly enhanced the quality of this work.

---

