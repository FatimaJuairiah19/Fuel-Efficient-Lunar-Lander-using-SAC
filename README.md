# Fuel-Efficient-Lunar-Lander-using-SAC
Reinforcement Learning project: SAC agent for fuel-efficient lunar landings with baseline comparison

This project implements Soft Actor-Critic (SAC) for controlling the Lunar Lander environment in OpenAI Gym, with a focus on fuel-efficient landing policies. It compares a baseline agent with a fuel-efficient SAC agent using multi-objective reinforcement learning.

## Project Overview

The goal is to train an RL agent that can:

1. Land the Lunar Lander safely between the flags.
2. Minimize fuel usage while landing.
3. Demonstrate **trade-offs in multi-objective reinforcement learning**.

Two policies were implemented:

- **Baseline:** Standard reward from LunarLanderContinuous-v3 environment.  
- **Fuel-Efficient SAC:** Modified reward penalizing high thrust usage to encourage minimal fuel consumption.

This simulates challenges similar to **satellite or spacecraft landing**, where precision and fuel efficiency are often conflicting objectives.

## Environment

- **Gymnasium Environment:** `LunarLanderContinuous-v3`  
- **Observation Space:** 8-dimensional vector (position, velocity, angle, angular velocity, leg contact)  
- **Action Space:** Continuous thrust values for main engine and side engines  
- **Wrapper:** `FuelEfficientWrapper` to add a fuel penalty to the reward:

```python
fuel_penalty = 0.1 * np.sum(np.square(action))
reward -= fuel_penalty

Evaluation Metrices

We evaluate agents using three metrics:
Average Episode Reward – overall performance of the policy.
Fuel Usage – sum of squared action magnitudes (thrust usage).
Landing Success Rate – fraction of episodes with total reward > 200.
