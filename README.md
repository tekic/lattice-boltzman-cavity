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


## How to Run the Code

### Prerequisites

Before compiling the simulation, ensure the following are installed:

* GNU C++ compiler (`g++`)
* `make`
* OpenLB library
* Optional: ParaView for VTK visualization

The code was developed using the OpenLB framework for Lattice Boltzmann simulations.

---

## Compilation

Navigate to the project directory and compile the code using:

```bash
make
```

This will generate the executable file (typically named according to the Makefile configuration).

---

## Running the Simulation

Run the executable with:

```bash
./cavity2d
```

or the executable name specified in the Makefile.

During execution, the solver prints:

* iteration step
* simulation time
* average energy
* average density

Example output:

```text
step i100; t=0.1; av energy=...
Saving Gif ...
Saving VTK file ...
```

---

## Output Files

Simulation results are written into the `tmp/` directory automatically.

Generated outputs include:

| File Type            | Description                      |
| -------------------- | -------------------------------- |
| GIF                  | Velocity magnitude visualization |
| VTK                  | Flow field data for ParaView     |
| ASCII velocity files | Exported velocity vectors        |

Example generated files:

```text
tmp/
├── uz000100.gif
├── vtk000100.vti
├── velocity000100.dat
```

---

## Visualization

### GIF Images

Velocity magnitude snapshots are automatically generated during the simulation.

### ParaView Visualization

VTK files can be opened using ParaView:

```bash
paraview
```

Then open the generated `.vti` files from the `tmp/` directory.

You can visualize:

* velocity vectors
* streamlines
* vorticity contours
* scalar velocity magnitude

---

## Simulation Parameters

The main simulation parameters are defined directly in `cavity2d.cpp`.

Key parameters include:

```cpp
LBunits<T> converter(
    1e-2,   // Maximum velocity
    100.,   // Reynolds number
    100,    // Grid resolution
    1.,     // Domain length x
    1.      // Domain length y
);
```

You may modify:

| Parameter       | Meaning            |
| --------------- | ------------------ |
| Reynolds number | Flow regime        |
| Grid resolution | Numerical accuracy |
| Lid velocity    | Flow intensity     |
| Domain size     | Geometry scaling   |

---

## Notes

* The code uses the D2Q9 lattice model.
* Boundary conditions are implemented using interpolated velocity boundaries.
* Results are saved periodically during the simulation.
* The simulation is configured for a square cavity flow problem.

---

## Parallel Execution

If OpenLB is compiled with MPI support, the code can also run in parallel:

```bash
mpirun -np 4 ./cavity2d
```

---

## Cleaning Build Files

To remove compiled files:

```bash
make clean
```


