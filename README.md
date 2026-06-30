# 1D-Heat-Transfer-Solver
Numerical simulation of 1D heat transfer in single and composite materials, featuring convection and non-linear radiation boundary conditions.
# 1D Heat Transfer Solver (Finite Difference Method)

This repository contains a numerical solver for 1D steady-state heat conduction problems using the Finite Difference Method (FDM) in Python. The script evaluates temperature distributions across both single-material and multi-layer composite structures.

## Mathematical Formulation
The core of the simulation relies on the 1D steady-state heat conduction equation with no internal heat generation:
$$k \frac{d^2T}{dx^2} = 0$$

The solver converts this differential equation into a system of linear algebraic equations ($[A][T] = [b]$) by discretizing the domain into nodes.

### Boundary Conditions
The model handles complex boundary conditions at the surfaces, integrating both convection and thermal radiation. The energy balance at the boundary nodes is defined as:
$$-k \frac{dT}{dx} = h(T - T_{\infty}) + \epsilon \sigma (T^4 - T_{rad}^4)$$

Because the radiation term involves $T^4$, the problem becomes non-linear. The solver uses an iterative approach, linearizing the radiation term in each iteration until the convergence tolerance ($10^{-6}$) is met.

## Features
* **Problem 1 (Single Material):** Calculates the temperature gradient along the $x$-axis with convection on the left and mixed (convection + radiation) boundary conditions on the right.
* **Problem 2 (Composite Material):** Simulates heat transfer along the $y$-axis through 4 different material layers (A, B, C, D) with varying thermal conductivities. Uses harmonic means to evaluate the thermal conductivity at the interface nodes.
* **Visualization:** Uses `matplotlib` to plot the temperature distribution across the spatial domains, with shaded regions to highlight different material layers in the composite problem.

## Requirements
* `numpy`
* `matplotlib`

## How to Run
Simply execute the Python script. The script will iteratively solve the matrices, output the converged iterations in the console, and generate a side-by-side comparative plot for both problems.
