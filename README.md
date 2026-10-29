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

## 6. Selecting the Optimal Action (Greedy vs. Epsilon-Greedy)

### Greedy Action Selection

At each time step \(t\), the agent selects the action with the highest estimated reward using the `argmax` operator.

**Formula:**

$$
A_t = \arg\max_a Q_t(a)
$$

**Where:**

- \(A_t\): The action selected at time step \(t\).
- \(Q_t(a)\): The estimated reward of action \(a\) at time step \(t\).
- \(\arg\max_a\): Selects the action with the highest estimated reward.

**Limitation:** A greedy strategy may repeatedly select the same arm and miss other arms that could provide higher rewards.



### Epsilon-Greedy Action Selection

The epsilon-greedy strategy selects the greedy action with probability \(1-\varepsilon\) and a random arm with probability \(\varepsilon\).

**Formula:**

$$
A_t =
\begin{cases}
\arg\max\limits_a Q_t(a), & \text{with probability } 1-\varepsilon \\
\text{random arm}, & \text{with probability } \varepsilon
\end{cases}
$$



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

## 1. Overview

This project implements a Nonstationary 10-Armed Bandit problem using Python. It compares two reward estimation methods:

1. Sample-Average Method
2. Constant Step-Size Method

The agent uses the epsilon-greedy strategy to select actions and learn from rewards in a changing environment.

## 2. Parameters

| Parameter | Value | Description |
|---|---:|---|

| Steps  | 10000 | Selects an arm 10000 times |
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

$$Q_{n+1}(a)=Q_n(a)+\frac{1}{n}[R-Q_n(a)]$$

Where:
- \(Q_n(a)\) is the previous estimated reward.
- \(R\) is the latest reward.
- \(n\) is the number of times the arm has been selected after the latest selection.

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






## Comparison of Sample-Average and Constant Step-Size Methods

## Example: Constant Step-Size Gives a Higher Estimated Reward

Assume the previous estimated reward is 2 and the latest reward received is 8.

### 1. Sample-Average Method

Assume the arm has been selected 10 times, including the latest selection.

**Formula:**

$$
Q_{\text{new}}=Q_{\text{old}}+\frac{1}{n}(R-Q_{\text{old}})
$$

**Substitute the values:**

$$
Q_{\text{new}}=2+\frac{1}{10}(8-2)
$$

$$
Q_{\text{new}}=2+0.1(6)
$$

$$
\boxed{Q_{\text{new}}=2.6}
$$

The new estimated reward using the sample-average method is **2.6**.

### 2. Constant Step-Size Method

Let the constant learning rate be \(\alpha=0.5\).

**Formula:**

$$
Q_{\text{new}}=Q_{\text{old}}+\alpha(R-Q_{\text{old}})
$$

**Substitute the values:**

$$
Q_{\text{new}}=2+0.5(8-2)
$$

$$
Q_{\text{new}}=2+0.5(6)
$$

$$
\boxed{Q_{\text{new}}=5.0}
$$

The new estimated reward using the constant step-size method is **5.0**.

### 3. Comparison of Results

| Parameter | Sample-Average Method | Constant Step-Size Method |
|---|---:|---:|
| Previous estimated reward | 2 | 2 |
| Latest reward | 8 | 8 |
| Update step | 0.1 | 0.5 |
| New estimated reward | 2.6 | 5.0 |

### 4. Why Does Constant Step Size Give a Higher Estimate?

The constant step-size method uses a learning rate of 0.5, while the sample-average method uses an update step of 0.1.

Since the constant step-size method uses a larger update step, its estimated reward moves more quickly toward the latest reward of 8.

### 5. Conclusion

In this example, the constant step-size method produces a higher estimated reward of 5.0, compared with 2.6 for the sample-average method.

In a nonstationary environment, the true reward values of the arms change over time. The constant step-size method can adapt more quickly because recent rewards continue to influence its estimates.

**Note:** A higher estimate after one update does not guarantee better overall performance. The result depends on the learning rate, reward changes, and action-selection strategy.






