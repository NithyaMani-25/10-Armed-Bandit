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

## 3. Estimated Reward Formula

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



## 4. Important Formulas Summary

| Formula | Purpose |
|---|---|
| `Q(a) = Total reward / Number of selections` | Calculates the average estimated reward |
| `Q_new(a) = Q_old(a) + (1/N(a)) * [R - Q_old(a)]` | Updates the estimated reward |
| `P(Exploration) = ε` | Probability of exploration |
| `P(Exploitation) = 1 - ε` | Probability of exploitation |







## 6. Estimated Reward Formula

The estimated reward represents the average reward obtained from selecting an arm.

$$
Q(a)=\frac{\text{Total reward from arm }a}{\text{Number of times arm }a\text{ was selected}}
$$

Where:

- \(Q(a)\) = Estimated reward of arm \(a\).
- Total reward = Sum of rewards received from that arm.
- Number of times selected = Total selections of that arm.

### Example: Arm 3

Suppose Arm 3 is selected three times and provides the following rewards:

| Attempt | Arm Selected | Reward |
|---|---|---:|
| 1 | Arm 3 | 2 |
| 2 | Arm 3 | 1 |
| 3 | Arm 3 | 5 |

**Step 1: Calculate the total reward.**

$$
\text{Total reward}=2+1+5=8
$$

**Step 2: Count the selections.**

$$
\text{Number of selections}=3
$$

**Step 3: Calculate the estimated reward.**

$$
Q(3)=\frac{2+1+5}{3}
$$

$$
Q(3)=\frac{8}{3}\approx2.67
$$

**Result:** The estimated average reward for Arm 3 is approximately 2.67.

## 7. Estimated Reward Update Formula

The agent updates its estimated reward whenever it selects an arm and receives a new reward.

$$
Q_{\text{new}}(a)=Q_{\text{old}}(a)+\frac{1}{N(a)}\left[R-Q_{\text{old}}(a)\right]
$$

Where:

- \(Q_{\text{new}}(a)\) = Updated estimated reward.
- \(Q_{\text{old}}(a)\) = Previous estimated reward.
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

## 8. Algorithm Steps

1. Initialize the estimated rewards of all 10 arms.
2. Choose an arm using the epsilon-greedy strategy.
3. Receive a reward from the selected arm.
4. Update the estimated reward of that arm.
5. Repeat the process for multiple attempts.
6. Compare the rewards and observe how the agent learns over time.

## 9. Important Formulas Summary

| Formula | Purpose |
|---|---|
| \(Q(a)=\frac{\text{Total reward}}{\text{Number of selections}}\) | Calculates the average estimated reward |
| \(Q_{\text{new}}(a)=Q_{\text{old}}(a)+\frac{1}{N(a)}[R-Q_{\text{old}}(a)]\) | Updates the estimated reward |
| \(P(\text{Exploration})=\varepsilon\) | Probability of exploration |
| \(P(\text{Exploitation})=1-\varepsilon\) | Probability of exploitation |

## 10. Conclusion

The 10-Armed Bandit problem demonstrates how Reinforcement Learning agents learn from rewards. Using the epsilon-greedy strategy, the agent balances exploration and exploitation to identify better actions and maximize its total reward over time.

**Key takeaway:** The actual reward is received from the environment, while the estimated reward is calculated from the agent's past experience.




