<div align="center">
  <h1>Kinetic</h1>
  <img
    src="https://i.postimg.cc/ncXfgjXd/dancing-circles.gif"
    alt="Kinetic Logo" width="300">
  </img>
  
  [![version](https://juliahub.com/docs/Kinetic/version.svg)](https://juliahub.com/ui/Packages/Kinetic/wrVmu)
  [![](https://img.shields.io/badge/docs-latest-blue)](https://xiaotianbai.com/Kinetic.jl/dev/)
  [![](https://img.shields.io/badge/docs-stable-blue)](https://xiaotianbai.com/Kinetic.jl/stable/)
  [![status](https://joss.theoj.org/papers/65d56efef938caf92c2cc942d2c25ea4/status.svg?style=flat-square)](https://joss.theoj.org/papers/65d56efef938caf92c2cc942d2c25ea4)
  [![downloads](https://shields.io/endpoint?url=https://pkgs.genieframework.com/api/v1/badge/Kinetic/label:downloads-sep:,-logo:Julia-color:important)](https://pkgs.genieframework.com?packages=Kinetic)
  
  | [Kinetic](https://github.com/vavrines/Kinetic.jl) | [KitBase](https://github.com/vavrines/KitBase.jl) | [KitML](https://github.com/vavrines/KitML.jl) | [KitFort](https://github.com/vavrines/KitFort.jl) |
| ---------- | --------- | ---------------- | ------ |
| ![CI](https://img.shields.io/github/workflow/status/vavrines/Kinetic.jl/CI?style=flat-square) | ![CI](https://img.shields.io/github/workflow/status/vavrines/KitBase.jl/CI?style=flat-square) | ![CI](https://img.shields.io/github/workflow/status/vavrines/KitML.jl/CI?style=flat-square) | ![CI](https://img.shields.io/github/workflow/status/vavrines/KitFort.jl/CI?style=flat-square) |
| [![codecov](https://img.shields.io/codecov/c/github/vavrines/Kinetic.jl?style=flat-square)](https://codecov.io/gh/vavrines/Kinetic.jl) | [![codecov](https://img.shields.io/codecov/c/github/vavrines/KitBase.jl?style=flat-square)](https://codecov.io/gh/vavrines/KitBase.jl) | [![codecov](https://img.shields.io/codecov/c/github/vavrines/KitML.jl?style=flat-square)](https://codecov.io/gh/vavrines/KitML.jl) | [![codecov](https://img.shields.io/codecov/c/github/vavrines/KitFort.jl?style=flat-square)](https://codecov.io/gh/vavrines/KitFort.jl) |
</div>

<!--
![](https://img.shields.io/github/v/tag/vavrines/Kinetic.jl?include_prereleases&label=latest%20version&logo=github&sort=semver)
![](https://img.shields.io/badge/License-MIT-yellow.svg)
![](https://zenodo.org/badge/243490351.svg?style=flat-square)
[![ColPrac: Contributor's Guide on Collaborative Practices for Community Packages](https://img.shields.io/badge/ColPrac-Contributor's%20Guide-blueviolet)](https://github.com/SciML/ColPrac)
[![GitHub commits since tagged version](https://img.shields.io/github/commits-since/vavrines/Kinetic.jl/v0.7.0.svg?style=social&logo=github)](https://github.com/vavrines/Kinetic.jl)
[![Visits Badge](https://badges.pufler.dev/visits/vavrines/Kinetic.jl)](https://badges.pufler.dev)
-->

<!--<div align="center"> <img
  src="https://i.postimg.cc/ncXfgjXd/dancing-circles.gif"
  alt="Kinetic Logo" width="300"></img>
</div>-->
<!--
# Kinetic.jl
<img src="https://i.postimg.cc/ncXfgjXd/dancing-circles.gif" width="300"/>
-->

**Kinetic** is a computational fluid dynamics toolbox written in [Julia](https://julialang.org).
Based on differentiable programming, mechanical and neural network models are fused and solved in a unified framework.
Simultaneous 1-3 dimensional numerical simulations can be performed on CPUs and GPUs.

The ecosystem follows the modular design philosophy.
Depending on the specific use case, the main module is split into portable components to reduce the lantency caused by the LLVM [just-in-time](https://llvm.org/docs/tutorial/index.html#building-a-jit-in-llvm) compiler:

- [KitBase.jl](https://github.com/vavrines/KitBase.jl): physical models and numerical schemes
- [KitML.jl](https://github.com/vavrines/KitML.jl): neural models and machine learning methods
- [KitFort.jl](https://github.com/vavrines/KitFort.jl): optional high-performance Fortran backend
- [FluxReconstruction.jl](https://github.com/vavrines/FluxReconstruction.jl): high-fidelity solution algorithms
- [Langevin.jl](https://github.com/vavrines/Langevin.jl): intrusive uncertainty quantification methods
- [kineticpy](https://github.com/vavrines/kineticpy): Python interface built on top of [pyjulia](https://github.com/JuliaPy/pyjulia)

## Installation

Kinetic is a registered package in the official [Julia package registry](https://github.com/JuliaRegistries/General).
We recommend installing it with the Julia package manager. 
From the Julia REPL, you can get in the package manager (by pressing `]`) and add the package

```julia
julia> ]
(v1.8) pkg> add Kinetic
```
This will automatically install a currently stable release and all its dependencies.

## Physics

Kinetic models and simulates fluid dynamics problems from the perspective of particle transport.
Any advection-diffusion-type equation of different particles, including molecules, photons, plasmas, neutrons, etc., can be solved within the framework.
Special attentions have been paid on Hilbert's sixth problem, i.e. to build the numerical passage between kinetic theory of gases, e.g. the Boltzmann equation, and continuum mechanics, e.g. the Euler and Navier-Stokes equations.
A partial list of current supported models and equations include:
- Boltzmann equation
- radiative transfer equation
- Fokker-Planck-Landau equation
- direct simulation Monte Carlo
- advection-diffusion equation
- Burgers equation
- Euler equations
- Navier-Stokes equations
- Magnetohydrodynamical equations
- Maxwell's equations

## Documentation

For the detailed implementation and usage of the package, please
check the documentation:

- [**STABLE**](https://xiaotianbai.com/Kinetic.jl/stable/): latest tagged version of the package
- [**LATEST**](https://xiaotianbai.com/Kinetic.jl/dev/): in-development version of the package

## Citing

If you benefit from Kinetic in your research, teaching, or otherwise, we would be happy if you could mention or cite it:

```
@article{Xiao2021,
  doi = {10.21105/joss.03060},
  url = {https://doi.org/10.21105/joss.03060},
  year = {2021},
  publisher = {The Open Journal},
  volume = {6},
  number = {62},
  pages = {3060},
  author = {Tianbai Xiao},
  title = {Kinetic.jl: A portable finite volume toolbox for scientific and neural computing},
  journal = {Journal of Open Source Software}
}
```

## Contributing

Feel free to dive in! If you have any questions or ideas, please [open an issue](https://github.com/vavrines/Kinetic.jl/issues/new) or submit pull requests.
If you're new to the open source community and looking for a cool little project to work on that fits your interests, we're happy to help along the way.

## License

[MIT](LICENSE) © Tianbai Xiao
