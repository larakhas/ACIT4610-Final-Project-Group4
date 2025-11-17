# Problem 1 – Ant Colony Optimization for Bin Packing

This project contains a Jupyter Notebook that runs the ACO algorithm on bin packing instances from OR-Library, as well as generates the necessary plots and result tables for the task.


## Folder structure

```
Problem 1/
│
├── problem1.ipynb        # Notebook containing all code and experiments
│
├── data/                 # All input datasets must be placed here
│   ├── binpack1.txt
│   ├── binpack2.txt
│   ├── ...
│   ├── binpack8.txt
│   └── binpack2D.txt     # 2D dataset
│
├── plots/                # All plots are automatically generated here
│   ├── 1D/
│   └── 2D/
│
└── README.md             # Documentation for Problem 1
```


## Requirements

### Libraries used in Problem 1

- **numpy** – numerical calculations and data manipulation  
- **matplotlib** – generation of convergence and load distribution plots  
- **pandas** – result tables and structured reporting  
- **jupyter** – required to run the .ipynb notebook  


## Installation

Install required libraries:

pip install numpy matplotlib pandas jupyter

## Running the notebook

The notebook can be started in two ways:

---

### 1) Open Jupyter Notebook

1. Start Jupyter Notebook.
2. Åpne filen **Problem 1/problem1.ipynb**.
3. Kjør **Run All**.
4. Resultattabellene vises nederst i notebooken.
5. Plottene genereres automatisk og lagres i:
   - `plots/1D/`
   - `plots/2D/`

---

### 2) Manually via the Jupyter interface

1. Åpne Jupyter.
2. Naviger til filen:

problem1.ipynb

3. Kjør notebooken.

---

### Directly from the terminal

Kjør notebooken med:

```bash
jupyter notebook problem1.ipynb


## Output

The notebook automatically generates:

- Convergence plots

- Load distribution plots

- Result tables for all instances