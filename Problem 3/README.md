README — Bees Algorithm for 0–1 (Multi) Knapsack

This project implements the Bees Algorithm (BA) to solve the 0–1 knapsack and multidimensional knapsack problems using benchmark datasets from the OR-Library and Pisinger’s Hard Instances.

1. Folder Structure
Problem3.ipynb
data/
 ├── OR-Library/
 │     └── mknap2.txt
 └── PisingerHard/
       └── knapPI_11_50_1000.csv

2. Required Python Packages
pip install numpy pandas matplotlib

3. Instances Used
Small Instances

WEING3 — 2 knapsacks, 28 items

WEING4 — 2 knapsacks, 28 items

Medium Instances

WEISH08 — 5 knapsacks, 40 items

WEISH09 — 5 knapsacks, 40 items

Large Instances

WEISH27 — 5 knapsacks, 90 items

WEISH28 — 5 knapsacks, 90 items

Pisinger Hard Instance

knapPI_11_50_1000_21 — 1 knapsack, 50 items

4. How to Run

Open the notebook:

jupyter notebook


Then open Problem3.ipynb and run all cells:

Run > Run All Cells


The notebook automatically:

Loads all 7 instances

Runs BA 10 times per instance

Runs greedy baseline

Generates tables, statistics, and plots

5. Running BA on a Single Instance
Example (OR-Library):
loader = DataLoader()
instance = loader.load_or_library(
    "data/OR-Library/mknap2.txt",
    ["WEISH27"]
)[0]

ba = BeesAlgorithmStandard(instance, random_seed=0)
solution, value, stats = ba.optimize()
print(value)

Example (Pisinger):
loader = DataLoader()
instance = loader.load_pisinger(
    "data/PisingerHard/knapPI_11_50_1000.csv",
    "knapPI_11_50_1000_21"
)

ba = BeesAlgorithmStandard(instance, random_seed=0)
solution, value, stats = ba.optimize()
print(value)

6. Output Produced

Results table with:
instance, n, W, best value, weight used, baseline, improvement %, runtime, iteration to best, population fitness

Statistics of best values over 10 runs

Convergence plots

Sensitivity analysis plots

7. Reproducibility

Uses random seeds 0–9

All instance IDs clearly listed

Repair function ensures feasible solutions

8. Summary

This project includes:

BA solver with repair

Baseline greedy heuristic

Required tables and plots

Six OR-Library instances + one Pisinger instance

Sensitivity analysis

Full reproducibility