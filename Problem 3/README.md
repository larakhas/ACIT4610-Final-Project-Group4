# Problem 3: Bees Algorithm for 0-1 Knapsack

## Running the Bees Algorithm on All Instances

This project evaluates the Bees Algorithm (BA) on a set of benchmark 0/1 knapsack instances from the OR-Library and the Pisinger Hard dataset.  
The following sections describe the instances used and explain how to run the solver on each of them.



## 1. Instances Used

### 1.1 OR-Library Instances  
We selected six classical 0/1 knapsack instances from the OR-Library benchmark set.  
They are grouped by size as follows:

#### Smallest Instances (fewest objects)
- **WEING1.DAT** — 2 knapsacks, 28 objects  
- **WEING4.DAT** — 2 knapsacks, 28 objects  

#### Medium Instance (middle range)
- **WEISH06.DAT** — 5 knapsacks, 40 objects  
- **WEISH07.DAT** — 5 knapsacks, 40 objects  



#### Largest Instances (most objects)
- **WEISH26.DAT** — 5 knapsacks, 90 objects  
- **WEISH30.DAT** — 5 knapsacks, 90 objects  

### 1.2 Pisinger Hard Instance
Additionally, we include one Pisinger “hard” knapsack instance for comparison:

- **knapPI_11_50_1000_19** — 1 knapsack, 50 objects

These files are placed in:

```
data/OR-Library/mknap2.txt         # contains all WEING/WEISH instances
data/PisingerHard/knapPI_11_50_1000.csv
```

---

## 2. Loading the Instances

### 2.1 Load OR-Library instances
```python
or_instances = loader.load_or_library(
    "data/OR-Library/mknap2.txt",
    ['WEING1', 'WEING4', 'WEISH06', 'WEISH07', 'WEISH26', 'WEISH30']
)
```

### 2.2 Load Pisinger Hard instance
```python
pisinger_instance = loader.load_pisinger(
    "data/PisingerHard/knapPI_11_50_1000.csv",
    "knapPI_11_50_1000_19"
)

```



## 3. Running Bees Algorithm

### 3.1 Run BA on a single OR-Library instance
```python
ba = BeesAlgorithmStandard(instance=or_instances[0])
best_solution, best_value = ba.optimize()

print("WEING1 – Best value:", best_value)
```

### 3.2 Run BA on all OR-Library instances
```python
for inst in or_instances:
    ba = BeesAlgorithmStandard(instance=inst)
    sol, val = ba.optimize()
    print(inst.name, val)
```

### 3.3 Run BA on the Pisinger instance
```python
ba = BeesAlgorithmStandard(instance=pisinger_instance)
sol, val = ba.optimize()
print("Pisinger instance:", val)
```

---

## 4. Greedy Baseline

```python
print("Greedy WEING1:", greedy_baseline(or_instances[0]))
print("Greedy Pisinger:", greedy_baseline(pisinger_instance))
```

---

## 5. 10-Run Statistical Evaluation

```python
runner = ExperimentRunner(or_instances)

stats = runner.run_multiple_seeds(
    instance=or_instances[0],   # e.g., WEING1
    num_runs=10
)

print("10-run statistics:", stats)
```

---

## 6. Convergence Plot

After running BA:

```python
ba.plot_convergence()
```







