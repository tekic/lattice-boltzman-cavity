# Lattice Boltzmann Simulation of Lid-Driven Flow in a Square Cavity with Bottom Corner Obstacles

## Overview

This repository contains the numerical implementation and simulation framework developed for the manuscript:

**“Lattice Boltzmann Simulation of Lid-Driven Flow in a Square Cavity with Bottom Corner Obstacles”**

The project investigates incompressible fluid flow inside a two-dimensional square cavity using the **Lattice Boltzmann Method (LBM)**. The study focuses on the influence of solid obstacles positioned at the bottom corners of the cavity and their effects on vortex formation, recirculation zones, and overall flow behavior.

The lid-driven cavity problem is a classical benchmark in computational fluid dynamics (CFD) and is widely used for validating numerical methods due to its well-known vortex structures and sensitivity to Reynolds number variations.

---

## Physical Problem

The simulated domain consists of:

* A square cavity filled with incompressible fluid
* A moving top wall (lid) with constant horizontal velocity
* Stationary side and bottom walls
* Two solid obstacles placed near the bottom corners

The moving lid generates circulation inside the cavity, producing primary and secondary vortices. The presence of corner obstacles modifies the local flow topology and affects:

* Vortex intensity
* Streamline patterns
* Velocity distribution
* Flow separation behavior

---

## Numerical Method

The simulations are performed using the **Lattice Boltzmann Method (LBM)**, specifically:

* D2Q9 lattice model
* Single Relaxation Time (BGK approximation)
* Bounce-back boundary conditions for solid walls and obstacles

### Governing Equation

The evolution of particle distribution functions is governed by:

[
f_i(\mathbf{x}+\mathbf{c}_i\Delta t, t+\Delta t)
================================================

## f_i(\mathbf{x}, t)

\frac{1}{\tau}
\left(
f_i(\mathbf{x}, t) - f_i^{eq}(\mathbf{x}, t)
\right)
]

where:

* (f_i) = particle distribution function
* (f_i^{eq}) = equilibrium distribution
* (\tau) = relaxation time
* (\mathbf{c}_i) = discrete lattice velocities

Macroscopic quantities are recovered from the distribution functions:

[
\rho = \sum_i f_i
]

[
\rho \mathbf{u} = \sum_i f_i \mathbf{c}_i
]


---

## Simulation Parameters

Typical simulation parameters include:

| Parameter     | Description         |
| ------------- | ------------------- |
| Re            | Reynolds number     |
| Nx, Ny        | Grid resolution     |
| U_lid         | Lid velocity        |
| tau           | Relaxation time     |
| obstacle_size | Obstacle dimensions |

---

## Boundary Conditions

| Boundary    | Condition           |
| ----------- | ------------------- |
| Top wall    | Moving lid          |
| Side walls  | No-slip             |
| Bottom wall | No-slip             |
| Obstacles   | Bounce-back no-slip |

---

## Results

The simulations reproduce characteristic lid-driven cavity flow phenomena, including:

* Primary central vortex
* Secondary corner vortices
* Obstacle-induced recirculation zones
* Reynolds-number-dependent flow transitions

The inclusion of bottom corner obstacles alters the local velocity field and modifies vortex interactions near the lower cavity region.

---

## Requirements

Typical dependencies may include:

* Python 3.x / MATLAB / C++ (adjust as needed)
* NumPy
* Matplotlib
* SciPy

Example installation:

```bash
pip install numpy matplotlib scipy
```

---

## Running the Simulation

Example execution:

```bash
python main.py
```

or

```bash
./simulate
```

depending on the implementation language.

Simulation parameters can usually be modified in configuration files or directly in the source code.

---

## Visualization

Post-processing scripts can generate:

* Velocity contours
* Streamlines
* Vorticity fields
* Convergence histories

Example outputs are stored in the `plots/` directory.

---

## Applications

This project is relevant to studies involving:

* Computational fluid dynamics
* Lattice Boltzmann methods
* Internal flow systems
* Obstacle-fluid interactions
* Numerical benchmark validation

---

## Citation

If you use this code or methodology in academic work, please cite the corresponding manuscript.

```bibtex
@article{yourcitation,
  title={Lattice Boltzmann Simulation of Lid-Driven Flow in a Square Cavity with Bottom Corner Obstacles},
  author={Author Names},
  journal={Journal Name},
  year={2026}
}
```

---

## License

Specify the project license here.

Example:

```text
MIT License
```

---

## Authors

* Author Name
* Institution
* Contact information

---

## Acknowledgments

The authors acknowledge the use of numerical methods and computational resources that supported this work.

