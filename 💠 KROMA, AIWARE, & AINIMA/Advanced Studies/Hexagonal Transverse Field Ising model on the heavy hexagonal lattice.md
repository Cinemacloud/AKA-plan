
---


![[PhysRevLett.133.180402.pdf]] 
---

1. The Model

System

Heavy Hexagonal Lattice:

A regular hexagonal lattice where each edge is "decorated" with an additional lattice site.

Two sublattices:

Sublattice A: Coordination number 2.

Sublattice B: Coordination number 3.




Hamiltonian

The Transverse Field Ising Hamiltonian: $$ H = -J \sum_{\langle i, j \rangle} \sigma_i^z \sigma_j^z - h \sum_i \sigma_i^x $$

: Pauli matrices.

: Interaction strength between spins.

: Transverse magnetic field strength.

: Nearest neighbors.



Initial State

Symmetry-Broken State: $$ |Z^+\rangle = |\uparrow \uparrow \cdots \uparrow\rangle $$ One of the degenerate ground states at .



---

2. Computational Framework

Numerical Method: BP-iTNS

Infinite Tensor Network State (iTNS):

Represents the quantum state as a repeating unit cell of tensors.

Periodic boundary conditions are applied to simulate the thermodynamic limit.


Belief Propagation Optimization:

Used to truncate and optimize the tensor network while assuming "treelike" correlations in the system.


Trotterized Time Evolution:

The propagator  is split into small time steps: $$ U(t) = \left[ \exp(-iH \delta t) \right]^n, , t = n \delta t $$

Second-order Trotter decomposition splits the Hamiltonian into one-site and two-site gates applied sequentially.



Tools

Implemented using ITensorNetworks.jl in Julia, a library specifically designed for tensor network simulations on arbitrary geometries.



---

3. Steps to Recreate the Experiment

1. Setup the Heavy Hexagonal Lattice:

Define the bipartite structure (sublattices A and B).

Set periodic boundary conditions to represent an infinite lattice.



2. Initialize the Tensor Network State:

Start from a product state: $$ |Z^+\rangle $$ with spins aligned along the -axis.



3. Time Evolution:

Apply Trotterized propagators to the tensor network state.

Use belief propagation to optimize the tensors during evolution.



4. Confinement Hamiltonian Approximation:

Construct a minimal model projecting the Hamiltonian into a "confined" subspace of low-energy excitations (as derived in the paper).



5. Calculate Observables:

Measure magnetization and entanglement entropy during the evolution.

Use Fourier analysis to identify the frequencies of quasiparticle oscillations.

Compute two-point correlation functions to analyze the spread of information.





---

4. Key Observations

Persistent Oscillations: Long-lived oscillations in magnetization and entanglement entropy indicate confinement.

Nonthermalization: The system avoids thermal equilibrium due to the confinement of quasiparticles.

Quasiparticle Dynamics: Excitations are bound states of domain walls, confined by the lattice's structure.



---

5. Required Resources

Software

Julia: For tensor network simulations.

ITensorNetworks.jl: Library used in the study.


Hardware

Computational Power:

Moderate CPUs/GPUs for handling large bond dimensions in tensor networks.

Memory depends on the bond dimension and number of lattice sites in the unit cell.




---

6. Refinements to Original Outline

Trotterized Time Evolution:

Explicit use of second-order Trotter decomposition for continuous-time dynamics.


Specific Numerical Techniques:

Belief propagation on infinite tensor networks (BP-iTNS).

Fourier analysis of the time-evolved state to extract quasiparticle masses.


Focus on Confined Subspace:

A minimal model is derived for the low-energy quasiparticles, reducing computational complexity.




---

This method faithfully reproduces the confinement dynamics observed in the original study, providing a robust framework for exploring quantum-classical simulations in structured lattices. Let me know if you'd like detailed coding examples or further clarification!
