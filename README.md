# Double Pendulum Analysis

**A Python simulation of the double pendulum system using Lagrangian mechanics to demonstrate chaotic behavior and analyze normal modes.**

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)  
![License](https://img.shields.io/badge/License-MIT-green)

## Overview

This repository contains a numerical investigation of the double pendulum. It explores two main regimes:

1. **Non-Linear (Chaotic):** Solving the full Euler–Lagrange equations to visualize sensitivity to initial conditions.  
2. **Linearized (Small Angle):** Deriving the equations of motion for small angles to find normal-mode frequencies (eigenvalues) and verifying them using Fast Fourier Transforms (FFT).

## Demo

<div align="center">
  <img src="media/chaos.gif" alt="Double Pendulum Chaos" />
  <br>
  <em>Figure 1: Simulation of the chaotic regime showing the sensitivity to initial conditions.</em>
</div>

## Repository Structure

| File | Description |
|------|-------------|
| `notebooks/01_full_simulation.ipynb` | Derives the full non-linear EOMs using SymPy, solves them with `scipy.integrate.solve_ivp`, and animates the chaotic trajectory. |
| `notebooks/02_linearization_analysis.ipynb` | Linearizes the system around the stable equilibrium, calculates eigenvalues/eigenfrequencies, and compares analytical predictions with FFT results. |

## The Physics

The system consists of two masses $m_1$ and $m_2$ connected by massless rods of length $l_1$ and $l_2$. The configuration is described by the angles $\theta_1$ and $\theta_2$.

### Lagrangian Formulation

The Lagrangian $\mathcal{L} = T - V$ is:

$$
T = \frac{1}{2}(m_1 + m_2) l_1^2 \dot{\theta}_1^2 
    + \frac{1}{2} m_2 l_2^2 \dot{\theta}_2^2 
    + m_2 l_1 l_2 \dot{\theta}_1 \dot{\theta}_2 \cos(\theta_1 - \theta_2)
$$

$$
V = -(m_1 + m_2) g l_1 \cos\theta_1 - m_2 g l_2 \cos\theta_2
$$

### Linearization & Normal Modes

For small angles ($\cos\theta \approx 1$, $\sin\theta \approx \theta$), the system behaves as two coupled harmonic oscillators.

The normal-mode frequencies follow from:

$$
\det(K - \omega^2 M) = 0
$$

Where:

- $M$ is the mass matrix  
- $K$ is the stiffness matrix from the linearized potential energy


## Installation

1. Clone the repository:

      ```bash
      git clone https://github.com/abdelrahman-26/double-pendulum-analysis.git

3. Install dependencies:

    ```bash
    pip install numpy scipy matplotlib sympy jupyter

## Usage

Launch Jupyter Notebook inside the repository folder:

    jupyter notebook

Then open the notebooks in the `notebooks/` directory:

- **Full simulation:** `01_full_simulation.ipynb`  
  Run all cells to see the animation of the chaotic system.

- **Physics + FFT analysis:** `02_linearization_analysis.ipynb`  
  Walks through the small-angle approximation, eigenvalue calculation, and FFT analysis.

## Key Libraries

- **SymPy** — symbolic derivation of Euler–Lagrange equations  
- **SciPy** — `solve_ivp` for numerical integration.
- **NumPy** — array operations, FFT  
- **Matplotlib** — plotting and animation  

## License

Distributed under the MIT License. See `LICENSE` for details.

## Acknowledgments

Derived from standard Lagrangian mechanics coursework.  
Visualizations inspired by examples from the Python scientific computing community.
