##Optimize Classic Benchmark Functions using Particle Swarm Optimization (PSO)

This repository contains a full implementation of Particle Swarm Optimization (PSO) for minimizing several standard continuous benchmark functions. The notebook includes global-best PSO (gbest), local-best PSO (lbest), hybrid PSO + Nelder–Mead, parameter studies and statistical evaluation over 30 independent runs.

Benchmark Functions
Sphere

Formula:
f(x) = Σ x_i²
Global minimum: x = 0
Bounds: [-5.12, 5.12]

Rosenbrock

Formula:
f(x) = Σ [100(x_{i+1} – x_i²)² + (1 – x_i)²]
Global minimum: x = 1
Bounds: [-5, 10]

Rastrigin

Formula:
f(x) = 10n + Σ [x_i² – 10 cos(2πx_i)]
Global minimum: x = 0
Bounds: [-5.12, 5.12]

Ackley

Global minimum: x = 0
Bounds: [-32.768, 32.768]

Dimensions Tested

Each function is evaluated in:

n = 2

n = 10

n = 30

Each configuration runs 30 independent repetitions.

PSO Configuration (gbest)

Inertia weight: w = 0.7

Cognitive coefficient: c1 = 1.5

Social coefficient: c2 = 1.5

Swarm size:

30 (for n = 2 and 10)

50 (for n = 30)

Max iterations: 300

Max evaluations: 30 000

Initial velocities: 10–20% of variable range

Velocity clamp: |v| ≤ 0.5 * (upper – lower)

Stopping criteria:

evaluation budget reached

early stop when function value < threshold

Fully reproducible using fixed random seeds

Local-Best PSO (lbest)

Ring topology

Each particle considers: left neighbor, itself, right neighbor

Same PSO parameters as gbest

Used to compare exploration vs. exploitation behavior

Hybrid PSO + Nelder–Mead

After PSO finishes, a local search step is applied:

Start from the best PSO solution (gbest position)

Apply Nelder–Mead (gradient-free)

Up to 200 iterations

Replace gbest if improved

This improves final accuracy on difficult landscapes.

What Is Recorded (Per the Assignment Requirements)

For every function × dimension × run:

Best fitness per iteration (gbest history)

Final best fitness

Final best position

Evaluations used

Aggregated over 30 runs:

mean

median

best

worst

standard deviation

success rate (based on threshold)

Parameter Study (w, c1, c2)

Studied on n = 10 for all functions.

Tested configurations
Setting	w	c1	c2
default	0.7	1.5	1.5
more_inertia	0.9	1.5	1.5
more_exploration	0.7	2.0	2.0
more_exploitation	0.4	2.5	2.5

A DataFrame summarizing results is generated.

gbest vs lbest Comparison

Example performed on: Rastrigin, n = 10

Reported for both topologies:

mean final fitness

best final fitness

Typical outcome:

gbest converges faster

lbest is more robust for multimodal landscapes

Visualizations

The notebook generates:

Convergence plot for a single run

Average convergence plot across 30 runs

Boxplots for final fitness (dims 2, 10, 30)

Pre-/post-Hybrid-Search comparison

All fitness plots are on a logarithmic scale.

How to Run

Open PSO.ipynb

Click Run All

All experiments, statistics, and plots are generated automatically

Requirements

Install required libraries:

pip install numpy matplotlib pandas scipy


Used:

numpy

matplotlib

pandas

scipy.optimize

statistics

random

math

Reproducibility

All runs use fixed random seeds

Ensures consistent and repeatable results across executions
