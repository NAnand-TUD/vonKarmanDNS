# Introduction
The von Karman vortex street is a well-known phenomenon in fluid mechanics and occurs behind bluff bodies, above some critical Reynolds number, as a result of boundary layer separation. The separated boundary layers forms two shear layers that induce various instabilities, which eventually give rise to the von Karman vortex shedding (Ausoni et al. 2006, Mittal et al. 2008). The bluff body wakes are of great engineering interest as they cangenerate noise or induce structural vibrations and, given agreement between natural frequency of the structure and the frequency of the vortex shedding, cause catastrophic failures (Williamson 1996). An example of such failure is the infamous collapse of the Tacoma Narrows Bridge (Larsen 2000).
![re620Vortex](https://user-images.githubusercontent.com/67333831/111768741-9c1d9600-88a8-11eb-955a-0532cf4f003e.png)



# Code
The code available in this repository has been used to conduct a direct numerical simulation (DNS) of the von Karman vortex street behind a 2D circular cylinder. To create a geometry and then perform the DNS, two pieces of open source software were used that are called Gmsh and openFOAM respectively. The former is a 3D fnite element grid generator with a CAD engine and post-processing capabilities (Geuzaine & Remacle 2009). The openFOAM is a CFD toolbox (OpenCFD 2019) that provides a range of solvers, where each has its specific purpose. This work implements the solver called icoFoam that is used to analyse incompressible and transient fows (OpenCFD 2018).

The computational domain has been created using an open source software Gmsh v4.71 and stretches from (-5.0 -5.0 0.0) to (25.0 5.0 1.0), where the unit associated with the geometry is a meter. The cylinder diameter (d), which happens to be also the characteristics length in Reynolds and Strouhal numbers defnitions, is equal to 1 unit. Based on this length, the rest of the geometry is scaled, with the width of 30d and the height of 10d. In order to monitor convergence of the simulation two probes have been placed within the flow feld and their exact coordinates are (1.0 0.0 0.0) and (10 2.5 0.0) for probes 1 and 2 respectively.

The front and back walls have been defined as empty patches, meaning that the solver reduces the 3D problem to a 2D one. The zeroGradient and fixedValue boundary conditions are equivalent to Neumann and Dirichlet ones respectively. The problem is reduced to an inviscid one at top and bottom walls by applying the slip condition. This removes potential and unnecessary infuence of boundary layer developed at those walls on the free-stream flow that is a subject of the analysis. The inflow velocity was set to be 1 m/s. For both pressure and velocity the internal field value was set to 0.

# Acknowledgement
This work has been carried out by Kamil Dylewicz as part of the Advanced Fluid Mechanics course at the University of Liverpool (2020-2021).

# References
* Ausoni, P., Farhat, M., Ait Bouziad, Y., Kueny, J.-L. & Avellan, F. (2006), Karman vortex shedding in the wake of a 2d hydrofoil: Measurement and numerical simulation, in `IAHR Int. Meeting of WG on Cavitation and Dynamic Problems in Hydraulic Machinery and Systems', number CONF.
* Geuzaine, C. & Remacle, J.-F. (2009), `Gmsh: A 3-d finite element mesh generator with built-in pre-and postprocessing facilities', International journal for numerical methods in engineering 79(11), 1309-1331.
* OpenCFD (2019). URL: https://openfoam.com/
* OpenCFD (2018). URL: https://www.openfoam.com/documentation/guides/latest/doc/guide-applications-solvers-incompressible-icoFoam.html
* Larsen, A. (2000), `Aerodynamics of the tacoma narrows bridge-60 years later', Structural Engineering International 10(4), 243-248.
* Mittal, S., Kottaram, J. J. & Kumar, B. (2008), `Onset of shear layer instability in flow past a cylinder', Physics of Fluids 20(5), 054102.
* Williamson, C. H. (1996), `Vortex dynamics in the cylinder wake', Annual review of fluid mechanics 28(1), 477{539.
