## Optimize Classic Benchmark Functions using Particle Swarm Optimization (PSO)

This repository contains a full implementation of Particle Swarm Optimization (PSO) for minimizing several standard continuous benchmark functions. The notebook includes:

- Global-best PSO (gbest)  
- Local-best PSO (lbest)  
- Hybrid PSO + Nelder–Mead  
- Parameter studies  
- Statistical evaluation over 30 independent runs  

---

## Benchmark Functions

### 1. Sphere

**Formula**

\[
f_{\text{Sphere}}(x) = \sum_{i=1}^{n} x_i^2
\]

**Global minimum**

\[
x^\* = 0,\quad f^\* = 0.
\]

**Bounds**

\[
x_i \in [-5.12,\; 5.12].
\]

---

### 2. Rosenbrock

**Formula**

\[
f_{\text{Ros}}(x) = \sum_{i=1}^{n-1} \left[ 100(x_{i+1} - x_i^2)^2 + (1 - x_i)^2 \right]
\]

**Global minimum**

\[
x^\* = 1,\quad f^\* = 0.
\]

**Bounds**

\[
x_i \in [-5,\; 10].
\]

---

### 3. Rastrigin

**Formula**

\[
f_{\text{Rast}}(x) = 10n + \sum_{i=1}^{n} \left[ x_i^2 - 10\cos(2\pi x_i) \right]
\]

**Global minimum**

\[
x^\* = 0,\quad f^\* = 0.
\]

**Bounds**

\[
x_i \in [-5.12,\; 5.12].
\]

---

### 4. Ackley

**Formula**

\[
f_{\text{Ack}}(x) =
-20 \exp\left( -0.2 \sqrt{\frac{1}{n} \sum_{i=1}^{n} x_i^2} \right)
- \exp\left( \frac{1}{n} \sum_{i=1}^{n} \cos(2\pi x_i) \right)
+ 20 + e
\]

**Global minimum**

\[
x^\* = 0,\quad f^\* = 0.
\]

**Bounds**

\[
x_i \in [-32.768,\; 32.768].
\]

---

## Dimensions Tested

Each benchmark function is evaluated in the following dimensions:

- \( n = 2 \)
- \( n = 10 \)
- \( n = 30 \)

For each function × dimension combination, the algorithm is run **30 independent times**.

---

## PSO Configuration (gbest)

Global-best PSO (gbest) uses the following configuration:

- Inertia weight: \( w = 0.7 \)  
- Cognitive coefficient: \( c_1 = 1.5 \)  
- Social coefficient: \( c_2 = 1.5 \)  

**Swarm size**

- 30 particles for \( n = 2 \) and \( n = 10 \)  
- 50 particles for \( n = 30 \)  

**Stopping / runtime limits**

- Max iterations: 300  
- Max evaluations: 30 000  

**Velocity settings**

- Initial velocities: 10–20% of the variable range  
- Velocity clamp:  
  \[
  |v_i| \le 0.5 \cdot (\text{upper}_i - \text{lower}_i)
  \]

**Stopping criteria**

- Evaluation budget reached, **or**  
- Early stop when function value < given threshold  

All experiments are fully reproducible using fixed random seeds.

---

## Local-Best PSO (lbest)

A local-best PSO variant is also implemented:

- Ring topology  
- Each particle considers:
  - Left neighbor  
  - Itself  
  - Right neighbor  

The same parameters as gbest are used (\(w, c_1, c_2\), swarm size, etc.).  
This allows comparison of **exploration vs. exploitation** behavior between gbest and lbest.

---

## Hybrid PSO + Nelder–Mead

To improve final accuracy, a hybrid approach is implemented:

1. Run PSO (gbest) normally.
2. Take the best global position found by PSO.
3. Use this as the starting point for **Nelder–Mead** local search (gradient-free):
   - Up to 200 iterations.
4. Replace the PSO best solution if Nelder–Mead finds an improvement.

This hybrid scheme is especially beneficial for difficult, multimodal landscapes.

---

## What Is Recorded (Per Assignment Requirements)

For **every** combination of:

- Function  
- Dimension  
- Run (out of 30)

The following is stored:

- Best fitness per iteration (gbest history)  
- Final best fitness  
- Final best position  
- Number of evaluations used  

Aggregated over 30 runs, the following statistics are reported:

- Mean  
- Median  
- Best  
- Worst  
- Standard deviation  
- Success rate (based on a chosen threshold)

---

## Parameter Study (w, c₁, c₂)

A parameter study is performed on \( n = 10 \) for all benchmark functions.

### Tested configurations

| Setting            | \(w\) | \(c_1\) | \(c_2\) |
|--------------------|------:|--------:|--------:|
| default            | 0.7   | 1.5     | 1.5     |
| more_inertia       | 0.9   | 1.5     | 1.5     |
| more_exploration   | 0.7   | 2.0     | 2.0     |
| more_exploitation  | 0.4   | 2.5     | 2.5     |

A `DataFrame` summarizing results across these configurations is generated in the notebook.

---

## gbest vs lbest Comparison

An example comparison is performed on **Rastrigin, \( n = 10 \)**.

For both topologies (gbest and lbest), the following are reported:

- Mean final fitness  
- Best final fitness  

Typical behavior:

- **gbest** converges faster.  
- **lbest** tends to be more robust on highly multimodal landscapes.

---

## Visualizations

The notebook generates several plots, including:

- Convergence plot for a single run (fitness vs. iterations)  
- Average convergence plot over 30 runs  
- Boxplots of final fitness for dimensions \( n = 2, 10, 30 \)  
- Pre-/post-hybrid (PSO vs. PSO + Nelder–Mead) comparison  

All fitness plots are shown on a **logarithmic scale** (log10) for clarity.

---

## How to Run

1. Open `PSO.ipynb`.  
2. Click **Run All** in Jupyter / VS Code / Google Colab.  
3. All experiments, statistics, and plots are generated automatically.

---

## Requirements

Install the required libraries:

```bash
pip install numpy matplotlib pandas scipy


## The implementation uses:

- numpy

- matplotlib

- pandas

- scipy.optimize

- statistics

- random

- math

## Reproducibility

- All runs use fixed random seeds.

- This ensures consistent and repeatable results across executions.

```bash
pip install numpy matplotlib pandas scipy
