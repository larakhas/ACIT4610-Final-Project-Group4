# 🐝 Bees Algorithm – 0/1 Multiple Knapsack Problem

## 1. Overview

This project implements the **Bees Algorithm (BA)** to solve the **0–1 Multiple Knapsack Problem (MKP)** with:

- Scout bees for global exploration  
- Elite and selected sites for local search  
- Shrinking neighborhoods  
- Stagnation-based site abandonment  
- A **repair operator** to enforce feasibility  
- A **greedy baseline heuristic** for comparison  

The implementation runs the algorithm on **OR-Library** MKP instances and one **Pisinger** “hard” instance, and produces:

- Convergence plots (iteration vs best value)  
- Statistics over 10 runs per instance  
- Summary table with baseline comparison  

---

## 2. Instances Used

### Smallest Instances (fewest objects)
- `WEING3.DAT`: 2 knapsacks, 28 objects  
- `WEING4.DAT`: 2 knapsacks, 28 objects  

### Medium Instances (middle range)
- `WEISH14.DAT`: 5 knapsacks, 50 objects  
- `WEISH16.DAT`: 5 knapsacks, 50 objects  

### Largest Instances (most objects)
- `WEISH28.DAT`: 5 knapsacks, 100 objects  
- `WEISH29.DAT`: 5 knapsacks, 100 objects  

### Pisinger “hard” instance
- `knapPI_11_50_1000_21` (from `knapPI_11_50_1000.csv`)

These are all loaded and run inside the notebook.

---

## 3. Requirements

### 3.1 Software

- Python **3.9+** (3.10/3.11 also fine)  
- Jupyter Notebook / JupyterLab / VS Code with Jupyter extension  

### 3.2 Python packages

Install required libraries:

```bash
pip install numpy pandas matplotlib
