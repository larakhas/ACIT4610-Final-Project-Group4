# Optimize Classic Benchmark Functions using Particle Swarm Optimization (PSO)

This repository contains a full implementation of Particle Swarm Optimization (PSO) for minimizing several standard continuous benchmark functions. The notebook includes:

- Global-best PSO (gbest)  
- Local-best PSO (lbest)  
- Hybrid PSO + Nelder–Mead  
- Parameter studies  
- Statistical evaluation over 30 independent runs  
## Benchmark Functions

**1. Sphere Function**

$$
f(x) = \sum_{i=1}^{n} x_i^2
$$

* Global minimum: x = 0, f(x) = 0
* Bounds: $x_i \in$  [-5.12, 5.12]


**2. Rosenbrock Function**

$$
f(x) = \sum_{i=1}^{n-1} [100(x_{i+1} - x_i^2)^2 + (x_i - 1)^2]
$$

* Global minimum: x = 1, f(x) = 0
* Bounds: $x_i \in$ [-5, 10]


**3. Rastrigin Function**

$$
f(x) = 10n + \sum_{i=1}^{n} [x_i^2 - 10\cos(2\pi x_i)]
$$

* Global minimum: x = 0, f(x) = 0
* Bounds: $x_i \in$ [-5.12, 5.12]

**4. Ackley Function**

$$
f_{\text{Ack}}(x) = -20 \exp\left(-0.2 \sqrt{\frac{1}{n} \sum x_i^2}\right) - \exp\left(\frac{1}{n} \sum \cos(2\pi x_i)\right) + 20 + e
$$


 
* Global minimum: x = 0, f(x) = 0
* Bounds: $x_i \in$ [-32.768, 32.768]

## Dimensions Tested

Each benchmark function is tested in three different dimensions:

- \( n = 2 \)  
- \( n = 10 \)  
- \( n = 30 \)

For every dimension, the experiment is repeated **30 independent times** to ensure reliable statistics.



## PSO Configuration (gbest)

The global-best PSO variant (gbest) is used with the following settings:

- Inertia weight: \( w = 0.7 \)  
- Cognitive component: \( c_1 = 1.5 \)  
- Social component: \( c_2 = 1.5 \)

**Swarm size**
- 30 particles for \( n = 2 \) and \( n = 10 \)  
- 50 particles for \( n = 30 \)

**Runtime parameters**
- Maximum iterations: 300  
- Maximum evaluations: 30,000  
- Initial velocities: 10–20% of the search range  
- Velocity clamp:

$$|v_i| \le 0.5(upper_i - lower_i)$$

**Stopping criteria**
- The evaluation budget is exhausted  
- Early stopping if the fitness drops below a predefined threshold  

All runs use fixed random seeds to ensure reproducibility.



## Local-Best PSO (lbest)

A local-best version of PSO is also implemented for comparison.  
This variant uses a **ring topology**, where each particle considers:

- Its left neighbor  
- Itself  
- Its right neighbor  

The same hyperparameters as gbest are used.  
This setup makes it possible to study the balance between **exploration** (lbest) and **exploitation** (gbest).



## Hybrid PSO + Nelder–Mead

To improve solution accuracy, a hybrid approach is applied:

1. Run standard PSO (gbest).  
2. Take the final gbest solution.  
3. Use it as the starting point for a **Nelder–Mead** local search (up to 200 iterations).  
4. If Nelder–Mead finds a better solution, it replaces the PSO result.

This hybrid strategy is especially effective for difficult multimodal problems.



## Recorded Data

For each run (function × dimension × repetition), the following are stored:

- Best fitness value per iteration  
- Final best fitness  
- Final best position  
- Total number of evaluations  

Across 30 runs, the following summary statistics are reported:

- Mean  
- Median  
- Best and worst results  
- Standard deviation  
- Success rate (relative to a target threshold)



## Parameter Study (w, c₁, c₂)

A parameter analysis is performed for \( n = 10 \), testing four settings:

| Setting            | \(w\) | \(c_1\) | \(c_2\) |
|--------------------|------:|--------:|--------:|
| default            | 0.7   | 1.5     | 1.5     |
| more_inertia       | 0.9   | 1.5     | 1.5     |
| more_exploration   | 0.7   | 2.0     | 2.0     |
| more_exploitation  | 0.4   | 2.5     | 2.5     |

A summary DataFrame of these results is automatically generated.



## gbest vs lbest Comparison

A direct comparison between gbest and lbest is performed on the **10-dimensional Rastrigin function**.

The recorded metrics include:

- Mean final fitness  
- Best final fitness  

In general:

- **gbest** converges faster  
- **lbest** is more robust on highly multimodal landscapes  


## Visualizations

The notebook produces several visual plots:

- Convergence curves (single run + average across 30 runs)  
- Boxplots for dimensions 2, 10, and 30  
- Comparison before/after applying Nelder–Mead  

All fitness plots are displayed on a logarithmic scale for clarity.


## How to Run

1. Open `problem2.ipynb`  
2. Click **Run All**  
3. All experiments, statistics, and visualizations will be generated automatically  



## Requirements

Install dependencies:

```bash
pip install numpy matplotlib pandas scipy
```

## Libraries used:

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

















