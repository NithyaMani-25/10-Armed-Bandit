 10-Armed-Bandit
 # 10-Armed Bandit Problem Using Python

## 1. Introduction

The **10-Armed Bandit Problem** is a fundamental problem in Reinforcement Learning (RL). It is used to understand how an agent learns to select the best action through repeated interaction with an environment.

The problem consists of 10 different actions, called arms. Each arm provides a reward based on an underlying reward distribution. The agent must learn which arm gives the highest expected reward.

The main challenge is balancing **exploration** (trying different arms) and **exploitation** (choosing the arm that appears to provide the highest reward).

## 2. Objectives

- To understand the 10-Armed Bandit problem in Reinforcement Learning.
- To implement the problem using Python.
- To study exploration and exploitation.
- To calculate and analyze rewards obtained from different arms.
- To visualize the learning performance using graphs.

## 3. Problem Description

In this experiment, the agent has 10 possible actions:

- Action 1
- Action 2
- Action 3
- Action 4
- Action 5
- Action 6
- Action 7
- Action 8
- Action 9
- Action 10

Each action has an unknown true expected reward. Whenever the agent selects an action, it receives a reward generated from that action's reward distribution.

The agent learns through repeated trials and attempts to maximize the total reward.

## 4. Methodology

The experiment follows these steps:

1. Initialize the 10 arms with their reward distributions.
2. Select an action using an action-selection strategy.
3. Receive a reward from the selected arm.
4. Update the estimated value of that action.
5. Repeat the process for multiple time steps.
6. Calculate the rewards and evaluate the agent's performance.
7. Plot graphs to visualize the results.

## 5. Algorithm

The action-value estimate can be updated using the sample-average method:

Q(a) = Q(a) + [R - Q(a)] / N(a)

Where:

- Q(a) is the estimated value of action a.
- R is the reward received.
- N(a) is the number of times action a has been selected.

This update allows the agent to improve its estimate of each arm's expected reward.

## 6. Exploration and Exploitation

The experiment can use the epsilon-greedy strategy.

- **Exploration:** Select a random action to discover its reward.
- **Exploitation:** Select the action with the highest estimated reward.

The parameter epsilon (ε) controls the probability of exploration.

For example, when ε = 0.1, the agent explores with a probability of 10% and exploits with a probability of 90%, subject to the action-selection implementation.

## 7. Technologies Used

- Python
- Google Colab
- NumPy
- Matplotlib

## 8. Graphical Analysis

The experiment can generate graphs such as:

- Average reward versus time steps.
- Percentage of optimal action selections versus time steps.
- Comparison of performance across different exploration rates.

These graphs help evaluate how the agent learns and how its strategy affects performance.

## 9. Expected Outcome

The agent should gradually improve its action-value estimates through repeated interactions. With an appropriate action-selection strategy, it can learn to select the arm with the highest expected reward more frequently.

The actual results depend on the reward distributions, exploration rate, number of steps, and experimental settings.

## 10. Applications

The multi-armed bandit problem has applications in:

- Online advertising.
- Recommendation systems.
- Clinical trial allocation.
- A/B testing.
- Resource allocation.
- Adaptive decision-making.

## 11. How to Run the Project

1. Open the notebook in Google Colab.
2. Run the Python cells in sequence.
3. Observe the reward values and action selections.
4. Generate and analyze the graphs.
5. Compare the performance of different parameter settings, if implemented.

## 12. Conclusion

The 10-Armed Bandit problem demonstrates how an agent can learn to make better decisions under uncertainty. It provides a simple foundation for understanding the exploration-exploitation trade-off in Reinforcement Learning.

## 13. Author

Add your name here.

## 14. License

This project is intended for educational and research purposes. Add a suitable open-source license if you wish to distribute the code for reuse.
