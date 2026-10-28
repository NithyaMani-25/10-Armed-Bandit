 10-Armed-Bandit
 # 10-Armed Bandit Problem 



<img width="1376" height="768" alt="image" src="https://github.com/user-attachments/assets/173c0186-1414-43e7-9f2e-5a276a88cfc0" />








## 1. Introduction

The 10-Armed Bandit is a Reinforcement Learning problem in which an agent chooses from 10 different actions (arms). Each arm provides a reward, but the reward values are initially unknown.

**Objective:** Learn which arm provides the highest reward while maximizing the total reward.

## 2. Exploration and Exploitation

The epsilon-greedy algorithm balances two strategies:

- **Exploration:** Selecting an arm to discover its reward.
- **Exploitation:** Selecting the arm with the highest estimated reward.

The probabilities are calculated as follows:

**Exploration:**

```text
P(Exploration) = ε
```

**Exploitation:**

```text
P(Exploitation) = 1 - ε
```

For example, if `ε = 0.1`:

- Exploration = 0.1 = 10%
- Exploitation = 1 − 0.1 = 0.9 = 90%

Therefore, the agent explores 10% of the time and exploits 90% of the time, on average.

## 3. Action-Value Function (Expected Reward)


The true value of an action (choosing arm \(a\)) is the expected reward when action \(a\) is selected.

$$
q_*(a) = \mathbb{E}[R_t \mid A_t = a]
$$


In practice, the true action value is unknown to the agent. The agent estimates it using the rewards received while learning.

## 4. Estimated Reward Formula

The estimated reward represents the average reward obtained from selecting an arm.

**Formula:**

```text
Q(a) = Total reward from arm a / Number of times arm a was selected
```

Where:

- `Q(a)` = Estimated reward of arm `a`
- `Total reward` = Sum of rewards received from that arm
- `Number of times selected` = Total selections of that arm

### Example: Arm 3

Suppose Arm 3 is selected three times and provides these rewards:

| Attempt | Arm Selected | Reward |
|---|---|---:|
| 1 | Arm 3 | 2 |
| 2 | Arm 3 | 1 |
| 3 | Arm 3 | 5 |

**Step 1: Calculate the total reward.**

```text
Total reward = 2 + 1 + 5 = 8
```

**Step 2: Count the selections.**

```text
Number of selections = 3
```

**Step 3: Calculate the estimated reward.**

```text
Q(3) = (2 + 1 + 5) / 3
     = 8 / 3
     = 2.67
```

**Result:** The estimated average reward for Arm 3 is `2.67`.

## 5. Estimated Reward Update Formula

The agent updates its estimated reward whenever it selects an arm and receives a new reward.

$$
Q_{\text{new}}(a)=Q_{\text{old}}(a)+\frac{1}{N(a)}\left[R-Q_{\text{old}}(a)\right]
$$

Where:

- Q<sub>new</sub>(a) = Updated estimated reward
- Q<sub>old</sub>(a) = Previous estimated reward.
- \(N(a)\) = Number of times the arm has been selected, including the current selection.
- \(R\) = Reward received from the current selection.

### Example Calculation

Suppose the previous estimate is 2.67, the new reward is 4, and the arm has now been selected four times.

$$
Q_{\text{old}}(3)=2.67
$$

$$
R=4,\qquad N(3)=4
$$

Substitute the values into the formula:

$$
Q_{\text{new}}(3)=2.67+\frac{1}{4}(4-2.67)
$$

$$
Q_{\text{new}}(3)=2.67+0.25(1.33)
$$

$$
Q_{\text{new}}(3)=2.67+0.3325
$$

$$
Q_{\text{new}}(3)=3.0025\approx3.00
$$

**Result:** The updated estimated reward is approximately 3.00.

The estimate increases because the new reward is greater than the previous estimate.

## 6. Algorithm Steps

1. Initialize the estimated rewards of all 10 arms.
2. Choose an arm using the epsilon-greedy strategy.
3. Receive a reward from the selected arm.
4. Update the estimated reward of that arm.
5. Repeat the process for multiple attempts.
6. Compare the rewards and observe how the agent learns over time.

## 7. Important Formulas Summary
| **Formula** | **Purpose** |
|---|---|
| <code>Q(a) = Total reward / Number of selections</code> | Calculates the average estimated reward |
| <code>Q<sub>new</sub>(a) = Q<sub>old</sub>(a) + (1/N(a)) [R - Q<sub>old</sub>(a)]</code> | Updates the estimated reward |
| <code>P(Exploration) = ε</code> | Probability of exploration |
| <code>P(Exploitation) = 1 - ε</code> | Probability of exploitation |

## 8. Conclusion

The 10-Armed Bandit problem demonstrates how Reinforcement Learning agents learn from rewards. Using the epsilon-greedy strategy, the agent balances exploration and exploitation to identify better actions and maximize its total reward over time.


# Nonstationary 10-Armed Bandit in Reinforcement Learning

## 1. Project Overview

This project implements a Nonstationary 10-Armed Bandit problem using Python. It compares two reward estimation methods:

1. Sample-Average Method
2. Constant Step-Size Method

The agent uses the epsilon-greedy strategy to select actions and learn from rewards in a changing environment.

## 2. Parameters

| Parameter | Value | Description |
|---|---:|---|
| Number of runs | 2000 | Repeats the experiment 2000 times |
| Steps per run | 10000 | Selects an arm 10000 times per run |
| Number of arms | 10 | Ten possible actions |
| Epsilon (ε) | 0.1 | 10% exploration and 90% exploitation |
| Alpha (α) | 0.1 | Constant learning rate |

## 3. Epsilon-Greedy Strategy

Epsilon-greedy balances exploration and exploitation.

- **Exploration:** Select a random arm to discover its reward.
- **Exploitation:** Select the arm with the highest estimated reward.

The probability of exploration is:

$$P(\text{Exploration})=\varepsilon$$

The probability of exploitation is:

$$P(\text{Exploitation})=1-\varepsilon$$

For ε = 0.1, the agent explores 10% of the time and exploits 90% of the time.

## 4. Sample-Average Method

The sample-average method estimates an arm's reward by averaging the rewards received from that arm.

$$Q_{n+1}(a)=Q_n(a)+\frac{1}{n+1}[R-Q_n(a)]$$

Where:
- \(Q_n(a)\) is the previous estimated reward.
- \(R\) is the latest reward.
- \(n+1\) is the number of times the arm has been selected after the latest selection.

**Example:**

Previous estimate = 2, new reward = 4, and selection count = 3.

$$Q_3=2+\frac{1}{3}(4-2)\approx2.67$$

The updated estimate is approximately 2.67.

## 5. Constant Step-Size Method

The constant step-size method uses a fixed learning rate to update the estimated reward.

$$Q_{\text{new}}(a)=Q_{\text{old}}(a)+\alpha[R-Q_{\text{old}}(a)]$$

Where α is the learning rate.

**Example:**

Previous estimate = 2, new reward = 4, and α = 0.1.

$$Q_{\text{new}}=2+0.1(4-2)=2.2$$

The updated estimate is 2.2.

## 6. Nonstationary Environment

In a nonstationary environment, the true reward values of the arms change over time. Therefore, an arm that was best earlier may not remain the best arm.

The sample-average method retains the influence of older rewards. The constant step-size method gives more continuing influence to recent rewards and can adapt more quickly to changes.


## 7. Performance Evaluation

The program evaluates the methods using two measures.

### Average Reward

$$\bar{R}_t=\frac{1}{M}\sum_{i=1}^{M}R_{i,t}$$

Here, M represents the number of runs. Higher average reward generally indicates better performance.

### Percentage of Optimal Actions

$$\text{Optimal Action Percentage}=\frac{\text{Number of optimal selections}}{\text{Number of runs}}\times100$$

This measures how frequently the agent selects an arm with the highest current true reward value.

## 8. Graphs

The Python program generates two graphs:

1. **Average Reward Graph:** Compares the average rewards of the sample-average and constant step-size methods.
2. **Optimal Action Percentage Graph:** Compares how frequently each method selects the currently optimal arm.


## 9. Conclusion

This project demonstrates how reinforcement learning can solve a decision-making problem in a changing environment. It compares the sample-average and constant step-size methods using epsilon-greedy action selection.

The sample-average method uses accumulated rewards, while the constant step-size method responds more continuously to recent rewards. The comparison helps demonstrate why a constant step size is often useful in nonstationary environments.

**Key takeaway:** The actual reward is received from the environment, while the estimated reward is calculated from the agent's past experience.




