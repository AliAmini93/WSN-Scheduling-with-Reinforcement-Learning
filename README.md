# Optimized Scheduling Strategies in Wireless Sensor Networks
# Advanced Scheduling Strategies in Wireless Sensor Networks

**Project Overview:**
This repository hosts the code and resources for an advanced scheduling framework designed to optimize energy consumption and improve state estimation accuracy within a Wireless Sensor Network (WSN). The project delves into the use of Reinforcement Learning, with a focus on the Deep Q-Networks (DQN) algorithm, to address the complex challenges of scheduling in WSNs.

**Core Concepts:**
- **Reinforcement Learning:** This project harnesses the power of Reinforcement Learning to enable adaptive and intelligent scheduling within the sensor network.
- **Deep Q-Networks (DQN):** DQN is utilized to approximate the optimal action-value function, facilitating informed decision-making within the network.
- **Q-Learning:** A foundational concept in Reinforcement Learning, Q-Learning underpins the understanding and implementation of DQN in this project.
- **Machine Learning:** Machine Learning principles are integrated to enhance the decision-making process in scheduling tasks.
- **Gymnasium and Stable Baselines3:** These libraries are employed to build and simulate a custom environment for training and evaluating the scheduling strategies.

# Environment Description

## WSNEnvironment: A Tailored Gym Environment

At the heart of this project lies 'WSNEnvironment,' a custom-built gym environment designed to simulate realistic scenarios within a WSN. This environment meticulously models sensor deployment, energy optimization, and event handling to align with the project's goals. Below is a detailed exploration of its key features and operations:

### Observation and Action Spaces
In Reinforcement Learning, the definition of observation and action spaces is critical. These spaces dictate what the agent perceives and the actions it can execute. In 'WSNEnvironment':
- **Observation Space:** The observation space is structured as a matrix that maps the 2D positions of sensors within the network. Additionally, an innovative feature has been added—a third column that tracks the frequency of sensor selection during an episode. This allows the agent to evolve from random behavior to a more strategic approach, informed by the DQN model.
- **Action Space:** The action space is directly tied to the number of sensors in the network. Each action corresponds to the selection of a specific sensor to retrieve data from its buffer.

### Environment Dynamics
The essence of 'WSNEnvironment' lies in its dynamic simulation of a sensor network over time:
- **Sensor Deployment:** The environment supports the creation of a customizable sensor network. The number of sensors (`num_sensors`) and their spatial arrangement are determined using a Poisson point distribution, ensuring diverse and random sensor placement.
- **Coverage and Energy Optimization:** 'WSNEnvironment' simulates the efficient use of sensor energy while maintaining optimal coverage of the monitored area. Sensors operate within circular coverage zones, representing the regions where they can detect and capture events.
- **Event Handling:** Events, which represent data to be captured, are generated probabilistically, based on a threshold probability (`threshold_prob`). If an event occurs, its location is randomly assigned within the monitored area. Sensors within the event’s coverage zone detect and log the event, simulating real-world event detection, and store it in their buffers.

### Agent Interaction
- **Step and Reset Functions:** The 'step' function models the agent's interaction with the environment, simulating sensor selection and event capture across multiple time steps. The 'reset' function reinitializes the environment at the beginning of each episode.
- **Reward Function:** The reward mechanism has been significantly upgraded from its original design. Instead of a simplistic reward system, 'WSNEnvironment' now calculates rewards based on the Age of Information (AoI). Minimizing AoI is essential for optimizing the system's state estimation. The agent's reward is directly related to its success in reducing AoI, encouraging more strategic sensor selection.

'WSNEnvironment' provides a versatile and comprehensive platform for testing and developing advanced scheduling strategies, enabling exploration and innovation in the field of sensor network optimization through reinforcement learning.

![WSNEnvironment](https://github.com/fareskhlifi/Intelligent-Scheduling-using-Reinforcement-learning-and-Deep-Q-Networks/blob/main/WSN.png?raw=true)

## Implemented Algorithms
This project features the implementation of five distinct algorithms aimed at optimizing sensor energy consumption and enhancing state estimation in a WSN environment:
- **Round Robin Scheduler:** A scheduler that systematically cycles through available actions.
- **Random Scheduler:** A scheduler that selects actions randomly from the available action space.
- **Q-learning Model:** A traditional Q-learning approach for action selection and reward maximization.
- **Deep Q-Network Model:** An advanced extension of Q-learning utilizing deep neural networks for more sophisticated decision-making.
- **Stable Baselines3 Model:** A reinforcement learning model leveraging the Stable Baselines3 library for training and performance evaluation.

The main focus of this project is on the Deep Q-Network Model, which offers advanced capabilities for optimizing sensor energy and improving system state estimation. The other algorithms are implemented as baselines for comparison.

## Algorithm Comparison and Data Analytics

For a detailed examination of the implementation and performance of each algorithm, including comparisons and data analysis, please refer to the Jupyter notebooks included in this repository. The project provides extensive data analytics, such as:

- Average reward comparisons
- Boxplots for reward distribution
- Latency analysis

