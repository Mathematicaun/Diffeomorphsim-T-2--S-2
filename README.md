# Mathematical Frameworks for the Torus and Sphere

This repository explores the mathematical formulations and transformations of the torus and the sphere. Below, we detail the parametric equations, transformations, and how specific limits transition between these shapes.

## Torus

The torus is represented parametrically as:

$$
\begin{aligned}
    x(u, v) &= (R + r \cos v) \cos u, \\
    y(u, v) &= (R + r \cos v) \sin u, \\
    z(u, v) &= r \sin v,
\end{aligned}
$$

where:
- $R$ is the major radius (distance from the center of the hole to the center of the tube),
- $r$ is the minor radius (radius of the tube),
- $u, v \in [0, 2\pi)$ are the parametric angles.

### Basis Vectors

The tangent vectors to the torus are obtained by differentiating the parametric equations with respect to $u$ and $v$:
- $\frac{\partial \vec{r}}{\partial u} = \left( -(R + r \cos v) \sin u, (R + r \cos v) \cos u, 0 \right)$,
- $\frac{\partial \vec{r}}{\partial v} = \left( -r \sin v \cos u, -r \sin v \sin u, r \cos v \right)$.

These vectors span the tangent plane at each point on the torus.

## Sphere

The sphere can be represented parametrically as:

$$
\begin{aligned}
    x(\theta, \phi) &= r \sin \phi \cos \theta, \\
    y(\theta, \phi) &= r \sin \phi \sin \theta, \\
    z(\theta, \phi) &= r \cos \phi,
\end{aligned}
$$

where:
- $r$ is the radius of the sphere,
- $\theta \in [0, 2\pi)$ is the azimuthal angle,
- $\phi \in [0, \pi]$ is the polar angle.

### Basis Vectors

The tangent vectors to the sphere are derived by differentiating with respect to $\theta$ and $\phi$:
- $\frac{\partial \vec{r}}{\partial \theta} = \left( -r \sin \phi \sin \theta, r \sin \phi \cos \theta, 0 \right)$,
- $\frac{\partial \vec{r}}{\partial \phi} = \left( r \cos \phi \cos \theta, r \cos \phi \sin \theta, -r \sin \phi \right)$.

These vectors form a basis for the tangent space at any point on the sphere.

## Transition from Torus to Sphere

### Limit as $R \to 0$
When the major radius $R$ tends to $0$, the torus collapses into a sphere-like structure:

$$
\begin{aligned}
    x(u, v) &= r \cos u \cos v, \\
    y(u, v) &= r \sin u \cos v, \\
    z(u, v) &= r \sin v,
\end{aligned}
$$

This corresponds to a sphere where $r$ remains constant, and the parameters $u$ and $v$ map directly to spherical coordinates.

## Special Cases

1. **Degenerate Sphere:** When $r \to 0$, both the sphere and the torus reduce to a single point.
2. **Flat Ring:** If $r$ is constant and $R \to \infty$, the torus becomes an infinitely thin flat ring.

## Applications

- **Torus:** Used in topology, geometry, and physics to study periodic systems.
- **Sphere:** Central to many fields, including astronomy, computer graphics, and geodesy.

## Visualization

Use Python and libraries like Matplotlib or Manim to visualize the transitions and structures. Scripts are provided in this repository to generate 3D plots and animations.
