# Basic Physics

## Microscopic formulation

The physical world shows a diverse set of behaviors on different characteristic scales.
Consider the molecular motion of gases as an example.
Down to the finest scale of a many-particle system, the Newton's second law depicts particle motions via
```math
\mathbf{F} = m \mathbf{a}.
```

As a first order system it reads
```math
\frac{d \mathbf x}{dt} = \mathbf v, \ \frac{d \mathbf v}{dt} = \frac{\mathbf F}{m},
```
where ``\mathbf F`` is external force and ``m`` is particle mass.

An intuitive numerical algorithm is to get the numerous particles on board and track the trajectories of them.
A typical example is the [Molecular Dynamics](https://en.wikipedia.org/wiki/Molecular_dynamics).
This is not going to be efficient since there are more than `2e25` molecules per cubic meter in normal atmosphere, and things get even more complicated when you count on the N-body interactions all the time.
Some methods have been proposed to simplify the computation.
As an example, the [Direct simulation Monte Carlo](https://en.wikipedia.org/wiki/Direct_simulation_Monte_Carlo) employs certain molecular models and conduct the intermolecular collisions in a stochastic manner.
It significantly reduces the computational cost, while the trade-off is the artificial fluctuations.
Many realizations must be simulated successively to average the solutions and reduce the errors.

## Mesoscopic formulation

An alternative strategy is made from ensemble averaging, where the coarse-grained modeling is used to provide a bottom-up view.
At the mean free path and collision time scale of molecules, particles travel freely during most of time with mild intermolecular collisions.
Such dynamics can be described with an operator splitting approach, i.e. the kinetic transport equation
```math
\frac{\partial f}{\partial t}+ \mathbf v \cdot \nabla_\mathbf x f + \mathbf a \cdot \nabla_\mathbf v f = Q(f),
```
where ``f`` denotes the probability of finding a particle at certain location in phase space.
The left-hand side of the equation above model the transport phenomena due to the inhomogeneous distribution of particles and external force field,
while the right-hand side depicts intermolecular collision.
Different collision models can be inserted into such equation.
If the particles only collide with a background material one obtains linear Boltzmann collision operator
```math
Q(f)=\int_{\mathbb R^3} \mathcal B(\mathbf v_*, \mathbf v) \left[ f(\mathbf v_*)-f(\mathbf v)\right] d\mathbf v_*,
```
where the collision kernel ``\mathcal B`` models the strength of collisions at different velocities. 
If the interactions among particles are considered, the collision operator becomes nonlinear. 
For example, the two-body collision results in nonlinear Boltzmann equation
```math
Q(f)=\int_{\mathbb R^3} \int_{\mathcal S^2} \mathcal B(\cos \beta, |\mathbf{v}-\mathbf{v_*}|) \left[ f(\mathbf v')f(\mathbf v_*')-f(\mathbf v)f(\mathbf v_*)\right] d\mathbf \Omega d\mathbf v_*.
```
To solve the Boltzmann equation, a discretized phase space needs to be introduced and the solution algorithm is called [discrete ordinates method](https://en.wikipedia.org/wiki/Discrete_ordinates_method) or discrete velocity method.
Due to the complicated fivefold integral in the nonlinear Boltzmann collision operator, sometimes it is replaced by the simplified models in the discrete velocity method, e.g. the relaxation model
```math
Q(f) = \nu (\mathcal M - f).
```
From the [H-theorem](https://en.wikipedia.org/wiki/H-theorem), we learn that an isolated system evolves in the direction with entropy increment.
The maximal entropy status corresponds to the well-known Maxwellian distribution
```math
\mathcal M = n\left(\frac{m}{2\pi k T}\right)^{D/2}\exp \left( -\frac{m}{2kT} (\mathbf v - \mathbf V)^2 \right),
```
where ``k`` is the Boltzmann constant, ``\mathbf V`` and ``T`` are the bulk velocity and temperature.
The Boltzmann dynamics can be projected onto lower dimensionality.
For example, with one-dimensional velocity space formulation, the high-dimensional particle distribution can be integrated with respect to the rest coordinates as
```math
h_0 = \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} f d v dw, \ h_1 = \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} (v^2+w^2) f dv dw,
```
where ``h_0`` and ``h_1`` are called reduced distribution functions and form a so-called `1d2f1v` system.

## Macroscopic formulation

Meanwhile, with the enlargement of modeling scale to a macroscopic hydrodynamic level, the accumulating effect of particle collisions results in an equalization of local temperature and velocity,
where the moderate non-equilibrium effects can be well described by viscous transport, heat conduction and mass diffusion,
i.e., the so called transport phenomena. 
Large-scale dynamics presents the property of waves, and the macroscopic transport equations can be constructed to describe the bulk behaviors of fluids.
Typical examples are the Euler and Navier-Stokes equations
```math
\frac{\partial \mathbf W}{\partial t} + \nabla_\mathbf x \cdot \mathbf F = \mathbf S
```
From microscopic particle transport to macroscopic fluid motion, there is a continuous variation of flow dynamics. 
We pay special attentions to Hilbert's sixth problem, i.e. building the numerical passage between the kinetic theory of gases and continuum mechanics. 
