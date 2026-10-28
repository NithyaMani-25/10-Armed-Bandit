 10-Armed-Bandit
 # 10-Armed Bandit Problem 

## 1. Objectives
To maximize the reward

<img width="1376" height="768" alt="image" src="https://github.com/user-attachments/assets/173c0186-1414-43e7-9f2e-5a276a88cfc0" />




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


## 5. Algorithm

The action-value estimate can be updated using the sample-average method:

Q(a+1) = Q(a) +1/N(a) [R - Q(a)] 

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


## 10. Conclusion

The 10-Armed Bandit problem demonstrates how an agent can learn to make better decisions under uncertainty. It provides a simple foundation for understanding the exploration-exploitation trade-off in Reinforcement Learning.



