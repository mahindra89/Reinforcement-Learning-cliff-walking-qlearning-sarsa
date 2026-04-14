#RL Cliff Walking with Q-Learning and SARSA

## Overview

This project is a notebook-based solution for **Homework 3** in **CS 4391 / 5391 – Reinforcement Learning**.  
The notebook builds a **sample-based cliff-walking environment** and compares how different policies and reinforcement learning methods behave in that environment.

The main goal of this homework is to study learning in a risky stochastic gridworld and compare:

- a **random policy**
- an **HW2-style optimal policy**
- **Q-learning**
- **SARSA**

The notebook also visualizes trajectories, learning curves, and final learned value functions / greedy policies.

---

## File

- `RL_HW3_final.ipynb` – main notebook containing all code, plots, analysis, and discussion

---

## Problem Setup

The environment is a **5 × 10 gridworld** with:

- **Start state:** `(4, 0)`
- **Goal state:** `(0, 9)`
- **Cliff cells:** `(0, 6)`, `(0, 7)`, `(0, 8)`

### Rewards
- Normal step reward = **-1**
- Goal reward = **0**
- Cliff reward = **-100**

If the agent falls into the cliff, it is **teleported back to the start state**.

### Stochastic Motion Model
The environment is stochastic:

- Intended action happens with probability **0.7**
- Each of the other three actions happens with probability **0.1**

This makes the task harder because the agent cannot always trust its chosen action.

---

## What the Notebook Does

The notebook is organized into 5 main tasks:

### Task 1 – Cliff-Walking Environment
- Builds the cliff-walking step-based environment
- Simulates 10 trajectories under:
  - a random policy
  - the HW2-style optimal policy
- Compares returns, cliff hits, success count, and path length

### Task 2 – Q-Learning
- Implements **tabular Q-learning**
- Trains from scratch over multiple runs
- Plots accumulated reward per episode
- Shows average learning trend and variance

### Task 3 – SARSA
- Implements **tabular SARSA**
- Uses the same training setup as Q-learning
- Plots reward curves and compares learning behavior

### Task 4 – Q-Learning vs SARSA
- Places both methods on the same graph
- Compares:
  - sample efficiency
  - stability
  - final performance
  - cliff behavior

### Task 5 – Learned Value Functions and Policies
- Extracts:
  - state-value estimate `V(s) = max_a Q(s, a)`
  - greedy policy from learned Q-tables
- Visualizes final policies and value maps for both methods

---

## Methods Used

### 1. Policy Iteration
The notebook first recreates an **HW2-style optimal policy** using the old no-cliff model.  
This policy is then tested in the new cliff environment to see how well it transfers.

### 2. Q-Learning
Q-learning is an **off-policy temporal-difference control method**.  
It updates the action-value table using the best possible next action:

\[
Q(s,a) \leftarrow Q(s,a) + \alpha \Big(r + \gamma \max_{a'} Q(s',a') - Q(s,a)\Big)
\]

### 3. SARSA
SARSA is an **on-policy temporal-difference control method**.  
It updates using the next action actually selected by the behavior policy:

\[
Q(s,a) \leftarrow Q(s,a) + \alpha \Big(r + \gamma Q(s',a') - Q(s,a)\Big)
\]

---

## Training Settings

The main training settings used in the notebook are:

- Discount factor `gamma` = **0.975**
- Learning rate `alpha` = **0.2**
- Exploration rate `epsilon` = **0.1**
- Number of episodes = **800**
- Maximum steps per episode = **200**
- Multiple random seeds are used for repeatability

---

## Main Libraries Used

The notebook uses the following Python libraries:

- `numpy`
- `pandas`
- `matplotlib`

You will also need a Jupyter environment such as:

- Jupyter Notebook
- JupyterLab
- Google Colab

---

## How to Run

### Option 1 – Jupyter Notebook
1. Make sure Python 3 is installed.
2. Install the required packages:
   ```bash
   pip install numpy pandas matplotlib notebook
   ```
3. Open the notebook:
   ```bash
   jupyter notebook RL_HW3_final.ipynb
   ```
4. Run all cells from top to bottom.

### Option 2 – Google Colab
1. Upload `RL_HW3_final.ipynb` to Colab
2. Run all cells in order

---

## Expected Outputs

When the notebook is run, it produces:

- trajectory plots for random and HW2-style policies
- summary tables for Task 1
- Q-learning reward curves
- SARSA reward curves
- comparison plot of Q-learning vs SARSA
- learned value-function and greedy-policy plots
- written discussion below each task

---

## Notes

- The notebook uses **fixed random seeds**, so results are reproducible.
- The code is written in a simple and readable way so each task is easy to follow.
- The notebook mixes both **implementation** and **discussion/report-style explanation**, which makes it suitable for assignment submission.

---

## Summary of the Main Takeaway

This homework shows the difference between simply reusing an old policy and learning directly in a risky environment.  
Both **Q-learning** and **SARSA** learn better policies for the cliff task, but they behave slightly differently:

- **Q-learning** tends to be more aggressive
- **SARSA** tends to be more cautious near the cliff

This makes the comparison useful for understanding the difference between **off-policy** and **on-policy** learning in practice.

---

## Author / Submission Info

**Course:** CS 4391 / 5391 – Reinforcement Learning  
**Assignment:** Homework 3  
**Submission format:** Notebook-based submission

