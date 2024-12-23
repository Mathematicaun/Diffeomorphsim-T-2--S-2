# Toroidal Surface Vector Field Visualization

## Overview

This project models a **torus** using parametric equations and computes the tangent vectors at each point on the surface. The vector field is visualized using a 3D plot and quiver vectors, which represent the local orientation and stretching of the surface. The computation is performed using symbolic differentiation, with numerical evaluation via **CuPy** for efficient GPU computation.

## Mathematical Framework

### Torus Parameterization

The torus is described using two angular parameters, $a$ and $b$, each ranging from 0 to 1. The surface is defined by two radii:

- $R$: Major radius (distance from the center of the tube to the center of the torus).
- $r$: Minor radius (radius of the tube).

The parametric equations for the torus are:

$$
\chi(a, b) = (r \cos(2\pi a) + R) \cos(2\pi b)
$$

$$
\psi(a, b) = (r \cos(2\pi a) + R) \sin(2\pi b)
$$

$$
\zeta(a, b) = r \sin(2\pi a)
$$

Where:
- $a$ traces around the minor circle (tube of the torus),
- $b$ traces around the major circle (the central circular path).

### Partial Derivatives

The partial derivatives of the parametric equations with respect to $a$, $b$, $R$, and $r$ are computed to understand how the surface behaves locally:

- $$ \frac{\partial \chi}{\partial a}, \frac{\partial \psi}{\partial a}, \frac{\partial \zeta}{\partial a} $$: Derivatives with respect to the $a$-parameter (minor circle).
- $$ \frac{\partial \chi}{\partial b}, \frac{\partial \psi}{\partial b}, \frac{\partial \zeta}{\partial b} $$: Derivatives with respect to the $b$-parameter (major circle).
- $$ \frac{\partial \chi}{\partial R}, \frac{\partial \psi}{\partial R}, \frac{\partial \zeta}{\partial R} $$: Derivatives with respect to the major radius $R$.
- $$ \frac{\partial \chi}{\partial r}, \frac{\partial \psi}{\partial r}, \frac{\partial \zeta}{\partial r} $$: Derivatives with respect to the minor radius $r$.

### Vector Field on the Torus

The code constructs the following tangent vectors based on the derivatives:

- $$ \vec{e}_a = \left( \frac{\partial \chi}{\partial a}, \frac{\partial \psi}{\partial a}, \frac{\partial \zeta}{\partial a} \right) $$
- $$ \vec{e}_b = \left( \frac{\partial \chi}{\partial b}, \frac{\partial \psi}{\partial b}, \frac{\partial \zeta}{\partial b} \right) $$
- $$ \vec{e}_r = \left( \frac{\partial \chi}{\partial r}, \frac{\partial \psi}{\partial r}, \frac{\partial \zeta}{\partial r} \right) $$
- $$ \vec{e}_R = \left( \frac{\partial \chi}{\partial R}, \frac{\partial \psi}{\partial R}, \frac{\partial \zeta}{\partial R} \right) $$

These vectors represent the local tangent directions to the torus at each point.

### Numerical Evaluation

The parametric functions and their derivatives are evaluated over a grid of $a$ and $b$ values:

- The $a$- and $b$-parameters are discretized using NumPy's `linspace` and `meshgrid`.
- The parametric equations and derivatives are computed symbolically and then lambdified into CuPy functions for efficient GPU-based computation.

### Vector Magnitude and Normalization

The magnitudes of the tangent vectors are computed as:

$$
|\vec{e}_a| = \sqrt{e_{a,x}^2 + e_{a,y}^2 + e_{a,z}^2}
$$

and similarly for the other vectors $\vec{e}_b$, $\vec{e}_r$, and $\vec{e}_R$. These magnitudes represent the local "stretching" of the vectors. The vectors are then normalized to unit length for visualization.

### Visualization

The visualization uses `matplotlib` to create a 3D surface plot of the torus, where:

- The surface color can represent the magnitude of the vector field.
- The `quiver` function is used to display the direction of the vector field on the surface, with vectors normalized to a constant length for clarity.

### Animation (Optional)

Using the `FuncAnimation` module from `matplotlib`, an animation could be created to show how the vector field evolves over time as the parameters $a$ and $b$ vary.

## Installation

To run this code, you will need the following libraries:

- `numpy`
- `matplotlib`
- `sympy`
- `cupy`

You can install these dependencies using:

```bash
pip install numpy matplotlib sympy cupy
