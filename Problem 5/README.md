# Problem 5 – Solving a Real-World Task Using Reinforcement Learning

This project implements Q-learning, SARSA, and Double Q-learning to solve a real-world problem: a warehouse robot that must navigate a slippery floor (FrozenLake-v1). The code trains and evaluates the agent, compares the results to both random and heuristic baselines, and generates learning curves and performance graphs. The project supports both 6×6 and 8×8 variants of the FrozenLake environment, as well as both linear and exponential epsilon decay.


## What the Code Does
- Creates FrozenLake-v1 environments (6×6 and 8×8)
- Visualizes the grid (S, F, H, G)
- Implements:
  - Q-Learning  
  - SARSA  
  - Double Q-Learning  
- Allows linear or exponential epsilon decay
- Trains the agent for many episodes
- Tracks rewards, steps, success rate, and epsilon
- Plots:
  - Smoothed rewards  
  - Smoothed episode lengths  
  - Epsilon decay curve  
- Evaluates:
  - Trained policy  
  - Random policy baseline  
  - Simple heuristic baseline  
- Prints success rate comparisons

This satisfies the assignment requirement to implement, train, evaluate, compare, and visualize reinforcement learning algorithms for a real-world problem.



## How to Run

### 1. Open the Notebook
Open the file **problem5.ipynb** notebook.

### 2. Run All Cells
Run the notebook by choosing “Run All,” which executes all cells sequentially.


## Python Version
Tested with **Python 3.12.4**



## Libraries Used
- matplotlib  
- numpy  
- seaborn  
- pandas  
- gymnasium  
- itertools (built-in)



## How to Install Required Libraries

```bash
pip install matplotlib numpy seaborn pandas gymnasium
