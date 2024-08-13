# Optimized Scheduling in Wireless Sensor Networks with DQN and Stable Baselines3

**Project Overview:**
This repository contains the code and resources for a comprehensive scheduling framework aimed at optimizing energy consumption and enhancing state estimation within a Wireless Sensor Network (WSN). The project leverages Reinforcement Learning, particularly the Deep Q-Network (DQN) algorithm, along with the Stable Baselines3 library, to address the intricate challenges of scheduling in WSNs.

**Core Concepts:**
- **Reinforcement Learning:** This project utilizes Reinforcement Learning to enable adaptive and intelligent scheduling within the WSN. The agent learns optimal scheduling strategies by interacting with the environment and receiving feedback in the form of rewards.
- **Deep Q-Networks (DQN):** DQN is employed to approximate the optimal action-value function, which guides the agent in making informed decisions within the network.
- **Stable Baselines3:** The project incorporates the Stable Baselines3 library, a powerful tool for developing and testing reinforcement learning algorithms, to train and evaluate the DQN model.
- **Custom Gymnasium Environment:** A custom WSN environment, `WSNEnvironment`, is built using the Gymnasium library. This environment simulates realistic sensor deployment, event detection, and energy optimization scenarios, serving as a testing ground for the scheduling algorithms.

# Environment Description

## WSNEnvironment: A Custom Reinforcement Learning Environment

At the core of this project is `WSNEnvironment`, a custom-designed Gymnasium environment tailored to simulate the dynamics of a Wireless Sensor Network. This environment plays a crucial role in training and evaluating the scheduling algorithms, particularly in reinforcement learning contexts. Below is a detailed breakdown of its key features:

### Observation and Action Spaces
The design of observation and action spaces is fundamental in reinforcement learning as it dictates what the agent perceives and the actions it can take. In `WSNEnvironment`:
- **Observation Space:** The observation space is a matrix representing the 2D positions of sensors in the network. A third column tracks the frequency of sensor selection during each episode, enabling the agent to evolve from random behavior to a more strategic approach based on the DQN model.
- **Action Space:** The action space corresponds to the number of sensors in the network, with each action representing the selection of a specific sensor to retrieve data from its buffer.

### Environment Dynamics
The dynamic nature of `WSNEnvironment` allows for realistic simulation of sensor network operations over time:
- **Sensor Deployment:** The environment supports customizable sensor deployment, where the number of sensors (`num_sensors`) and their spatial distribution are generated using a Poisson point distribution to ensure randomness and diversity.
- **Coverage and Energy Optimization:** Sensors operate within defined coverage areas, and the environment simulates the efficient use of sensor energy while maintaining optimal area coverage.
- **Event Handling:** Events are generated probabilistically based on a threshold probability (`threshold_prob`). When an event occurs, its location is randomly assigned within the monitored area. Sensors within the event’s coverage zone detect and log the event, simulating real-world event detection, and store it in their buffers.

### Agent Interaction
- **Step and Reset Functions:** The `step` function simulates the agent’s interaction with the environment, encompassing sensor selection and event capture across multiple time steps. The `reset` function reinitializes the environment at the start of each episode.
- **Reward Function:** The reward mechanism is centered around minimizing the Age of Information (AoI), a critical factor for optimizing state estimation. The agent is rewarded based on its effectiveness in reducing AoI, encouraging strategic sensor selection.

`WSNEnvironment` offers a robust and flexible platform for experimenting with and developing advanced scheduling strategies, particularly in the context of reinforcement learning.

## Implemented Algorithms
This project includes the implementation of several algorithms designed to optimize sensor energy consumption and improve state estimation within the WSN environment:
- **Round Robin Scheduler:** A simple scheduler that systematically cycles through the available actions.
- **Random Scheduler:** A baseline scheduler that selects actions randomly from the available action space.
- **Q-Learning Model:** A traditional reinforcement learning approach that selects actions based on learned Q-values.
- **Deep Q-Network Model (DQN):** A more advanced model that uses deep neural networks to make complex scheduling decisions. This model is the primary focus of the project.
- **Stable Baselines3 DQN Model:** An implementation of the DQN model using the Stable Baselines3 library, providing a robust and scalable approach to training and evaluation.

## Algorithm Comparison and Data Analytics

The repository provides detailed analyses of the performance of each algorithm, including:
- **Average Reward Comparisons:** Evaluating the average rewards obtained by different schedulers over multiple episodes.
- **Boxplot Analysis:** Visualizing the distribution of rewards across different scheduling strategies.
- **Latency Analysis:** Assessing the time latency of captured events to evaluate the efficiency of each scheduler.

These analyses are documented in the Jupyter notebooks included in this repository, offering insights into the relative performance of each scheduling strategy.
