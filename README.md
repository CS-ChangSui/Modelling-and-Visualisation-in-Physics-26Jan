# 2D Ising Model Simulation with Optional Numba JIT Acceleration

**Course:** Modelling and Visualisation in Physics  
**Student Name:** Chang Sui  
**Student ID:** s2261175  
**Date:** February 11, 2026  

---

## Project Overview

This project implements a Monte Carlo simulation of the **2D Ising Model** using the **Metropolis–Hastings algorithm** (accept/reject scheme). The simulation investigates phase transitions in ferromagnetic systems and explores critical phenomena such as:

- Spontaneous magnetization  
- Heat capacity peaks  
- Magnetic susceptibility divergence  

To improve computational efficiency, the core Monte Carlo update loops are optimized using **Numba JIT (Just-In-Time) compilation**, achieving near C-level performance.

---

## Key Features

### Dual Dynamics Support

- **Glauber Dynamics**
  - Single spin-flip updates  
  - Non-conserved order parameter  
  - Suitable for studying ferromagnetic phase transitions  

- **Kawasaki Dynamics**
  - Spin-exchange updates  
  - Conserved order parameter  
  - Suitable for studying diffusion and phase separation  

---

### Performance Optimization

- Accelerated using the `@njit` decorator from `numba`
- Significant speed-up compared to pure Python implementation

---

### Statistical Analysis

- Implements **Bootstrap Resampling**
- Provides reliable error estimates for:
  - Heat Capacity ($C_V$)
  - Magnetic Susceptibility ($\chi$)
  - Magnetisation error bars

---

### Visualization

- Combined thermodynamic plots including:
  - Average Energy ($E$)
  - Magnetisation ($M$)
  - Heat Capacity ($C_V$)
  - Magnetic Susceptibility ($\chi$)
- Error bars included where applicable
- Optional **GIF animation** for temperature sweep

---

## Dependencies

Install required packages using:

```bash
pip install numpy matplotlib pandas numba pillow
```

Or with conda:

```bash
conda install numpy matplotlib pandas numba pillow
```

---

## How to Run the Notebook

### Cell Structure

0. **Global Parameters**  
   Define dynamics type, lattice size, temperature range, etc.

1. **Simulation with Numba JIT**  
   Optimized simulation (~2 minutes default runtime)

2. **Simulation (Pure Python)**  
   Non-optimized version (~30 minutes default runtime)

3. **Animation with Numba JIT**  
   Optional standalone animation generation

4. **Animation (Pure Python)**  
   Optional standalone animation generation

---

## Recommended Workflow

If using **Numba JIT version**:

Run:
Cell 0 → Cell 1 → Cell 3

If using **Pure Python version**:

Run:
Cell 0 → Cell 2 → Cell 4

---

## Outputs

All graphs and data files are automatically saved to your current working directory.  
The notebook will print the save path when saving files.

---

# Output Details

## Glauber Dynamics

### Saved Files

- `glauber_results.csv`
- One combined figure with four subplots

### Generated Plots

1. Average Energy vs $k_B T$
2. Specific Heat vs $k_B T$ (with vertical error bars)
3. Average Absolute Magnetisation vs $k_B T$ (with vertical error bars)
4. Magnetic Susceptibility vs $k_B T$ (with vertical error bars)

### CSV File Columns

1. Temperature ($T$)
2. Average Energy ($E$)
3. Average Absolute Magnetisation ($M$)
4. Magnetisation Error ($M_{err}$)
5. Specific Heat ($C_V$)
6. Specific Heat Error ($C_{err}$)
7. Magnetic Susceptibility ($\chi$)
8. Susceptibility Error ($\chi_{err}$)

---

## Kawasaki Dynamics

### Saved Files

- `kawasaki_results.csv`
- One combined figure with two subplots

### Generated Plots

1. Average Energy vs $k_B T$
2. Specific Heat vs $k_B T$ (with vertical error bars)

### CSV File Columns

1. Temperature ($T$)
2. Average Energy ($E$)
3. Average Absolute Magnetisation ($M$)
4. Magnetisation Error ($M_{err}$)
5. Specific Heat ($C_V$)
6. Specific Heat Error ($C_{err}$)
7. Magnetic Susceptibility ($\chi$)
8. Susceptibility Error ($\chi_{err}$)

---

## Notes

- Critical temperature for 2D square lattice Ising model ($J=1$):

  $$
  T_c \approx 2.269
  $$

- Finite lattice sizes may cause slight shifts in peak positions due to finite-size effects.
