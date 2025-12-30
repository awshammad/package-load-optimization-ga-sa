# Package-to-Vehicle Load Optimization (Genetic Algorithm + Simulated Annealing) — Python

## Overview
This project solves a **package delivery / load assignment optimization** problem:

- You have a set of **packages** (each with coordinates, weight, and priority).
- You have a set of **vehicles** (each with a capacity).
- The goal is to assign packages to vehicles and order each vehicle’s route to:
  1) minimize **total travel distance** (starting/ending at the depot `(0,0)`),  
  2) reduce **priority violations / penalties**,  
  3) reduce the number of **active vehicles** (optional penalty).

The project provides two meta-heuristic optimizers:
- **Genetic Algorithm (GA)**
- **Simulated Annealing (SA)**

A simple GUI (CustomTkinter) allows entering vehicles/packages and selecting the optimization method.

---

## Features
- GUI input for vehicles & packages (CustomTkinter)
- Two optimizers: **GA** and **SA**
- Capacity constraints (packages must fit within vehicle capacity)
- Distance-based objective + penalty terms
- Prints/returns the optimized assignment (vehicles with assigned packages)

---

## Algorithms
### Genetic Algorithm (GA)
- Population-based search (selection, crossover, mutation)
- Builds candidate assignments (chromosomes), evaluates fitness, keeps the best solution

### Simulated Annealing (SA)
- Starts with an initial solution
- Iteratively explores neighbor solutions while gradually reducing temperature
- Accepts worse moves probabilistically to escape local minima

---

## Repository Structure (recommended)
```
package-load-optimization-ga-sa/
├─ README.md
├─ requirements.txt
├─ docs/
│  └─ AI Report.pdf
└─ src/
   ├─ Driver.py
   ├─ GUI.py
   ├─ loadManager.py
   ├─ package.py
   ├─ vehicle.py
   └─ algorithms/
      ├─ __init__.py
      ├─ genetic_algorithm.py
      └─ simulated_annealing.py
```

### Important import note
Your current `loadManager.py` imports like:
```py
from algorithms import genetic_algorithm, simulated_annealing
```
So the clean setup is:
1. Create a folder `src/algorithms/`
2. Move `genetic_algorithm.py` and `simulated_annealing.py` into it
3. Add an empty `__init__.py` file inside `algorithms/`

(Alternative: change the import to match your file layout.)

---

## Requirements
- Python **3.8+**
- `customtkinter`

Install:
```bash
pip install customtkinter
```

If you also want plotting later (optional), install:
```bash
pip install matplotlib
```

Create `requirements.txt` like:
```
customtkinter
```

---

## How to Run
From the `src/` folder:
```bash
python Driver.py
```

1) The GUI will open.  
2) Enter your vehicles and packages.  
3) Select **GA** or **SA**.  
4) The program prints the optimized assignment/result.

---

## Inputs (Concept)
Each package contains:
- `id`, `x`, `y`, `weight`, `priority`

Each vehicle contains:
- `id`, `capacity`

The depot is assumed to be at `(0,0)`.

---

## Files
- `Driver.py` — program entry point (launch GUI → load data → optimize)
- `GUI.py` — GUI for data entry and algorithm selection
- `loadManager.py` — manages packages/vehicles and calls the selected optimizer
- `package.py` — Package class
- `vehicle.py` — Vehicle class
- `genetic_algorithm.py` — GA optimizer
- `simulated_annealing.py` — SA optimizer
- `AI Report.pdf` — project report/documentation

---

## Team
- Aws Hammad (1221697)
- Aboud Fialah (1220216)
