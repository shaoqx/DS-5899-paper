# Pushing the frontiers of density functionals by solving the fractional electron problem
with transformer (or multilayer perceptron)
> https://www.science.org/doi/10.1126/science.abj6511

## Overview
### Background
Molecular modeling is a promising with to understand and design everything made out of molecules.

What does a molecular model looks like? atomic geometry & electronic structure

How to model a molecular? Energy calculation -> one of the method: DFT

DFT is already successful but have limitation: violation of mathematical properties in all popular approximations -> limited performance in special systems.

### Problem
Eliminate some limitation in accuracy of DFT calculation:
- Solve pathological errors from violation of exact conditions for systems with fractional electrons in existing functionals to enhance the **accuarcy**.
- from 0 to 1 in some application system.

### Approach

<details>
<summary>DFT 101</summary>

- Time-indenpendent Schrödinger Equation (TISE)

  ${\hat {H}}\Psi = E\Psi$ this gives energy

- TISE for molecule

  ${\hat {H}}\Psi =\left[{\hat {T}}+{\hat {V}}+{\hat {U}}\right]\Psi =\left[\sum _{i=1}^{N}\left(-{\frac {\hbar ^{2}}{2m_{i}}}\nabla _{i}^{2}\right)+\sum _{i=1}^{N}V(\mathbf {r} _{i})+\sum _{i<j}^{N}U\left(\mathbf {r} _{i},\mathbf {r} _{j}\right)\right]\Psi =E\Psi$

  limition in solving the many-body problem limits its solution.

- Hohenberg–Kohn theorems

  - electronic density can give wavefunction

    $\Psi_{0}=\Psi [n_{0}]$

    $O[n_{0}]={\big \langle }\Psi [n_{0}]{\big |}{\hat {O}}{\big |}\Psi [n_{0}]{\big \rangle }$
  - defines an energy functional for the system and proves that the ground-state electron density minimizes this energy functional

    $E[\rho ]=T_{s}[\rho ]+\int d\mathbf {r} \,v_{\text{ext}}(\mathbf {r} )\rho (\mathbf {r} )+E_{\text{H}}[\rho ]+E_{\text{xc}}[\rho ]$

- Self-consistent field

  $\left[-\frac{\hbar^2}{2m}\nabla^2+V_s(\vec r)\right] \phi_i(\vec r) =  \epsilon_i \phi(\vec r)$

  $n(\vec r )\equiv n_s(\vec r)=\sum_i^N \left|\phi_i(\vec r)\right|^2$

  $V_s = V +\int \frac{e^2n_s(\vec r\,')}{|\vec r-\vec r\,'|} {\rm d}^3r'+ V_{\rm XC}[n_s(\vec r)]$

  1. inital guess of $n(\vec r)$
  2. calculate $\!V_s$ from DFT functional


</details>


 -> many body problem -> H-K principle 1 2 -> K-S equation -> SCF -> functional -> Eex
Why dont directly training the geom and the energy? (because it is not one to one correlated, the same geometry could have different electronic structure)
Train a new functional that obeys two classes of mathematical constraints with fractional electrons.
only the $E_{ex}$ term is learned

#### Code demo (done)
[Colab notebook](https://colab.research.google.com/drive/1wl7wB1vNYKgYIdsWwKryCs-DX1lZWURv?usp=sharing)

#### dataset
fixed densities of reactant and product (by B3LYP) -> reaction energy (by experiment or CCSD(T)/CBS) 

#### Architecture (formal pseudocode)

### Significance (done)
- Provide a new paradigm for DFT design.
- In general, outpreforms popular hand-made functionals in all datasets.

  ![](resource/benchmark_result.png)

  Especially, 
  - in bond breaking benchmark (BBB), accuratly described systems with fractional charge (FC) and fractional spin (FS).
  - in mindless benchmark subset (MB16-43), accuratly described systems with out-of-distribution exotic geometries. (randomly generated)

  In cases where traditional DFTs are expected to be bad,
  - correctly described bond breaking for charged and closed-shell neutral molecules
    ![](resource/bond_diss.png)
  - correctly described charge delocalization in the DNA base pair
    ![](resource/DNA_pair.png)
  - magnetic properties of a compressed hydrogen chain
  - reaction barrier heights for a ring-opening intermediate with diradical character
    ![](resource/H-chain_and_barrier.png)

## Analysis
### Overlooked
speed (near dlpno-CCSD(T))
### Further development
speed
non-main group element
### Disputed part
doubt
- leaking of the training set in test set of BBB
- generalization part all have problems

response
- do leaking but have other part not leaking proving the fact
-  no examples that it is really bad at generalization.

Inconsistant performance shown by a recent study [6].
- The trend of DM21 changes several times with the increase of the atomic number

![](resource/inconsistent.png)

## Questions
### Q1
Why dont they directly learn from structure - energy data?
<details>
<summary>Answer</summary>

People have had many tries on it and the ability to generilize the model is the core problem.

</details>

### Q2


## Resource (done)

[1] DM21 repo https://github.com/deepmind/deepmind-research/tree/master/density_functional_approximation_dm21

[2] Comment on the paper from John P. Predew https://www.science.org/doi/10.1126/science.abm2445

[3] The doubt from Gerasimov et al. https://www.science.org/doi/10.1126/science.abq3385

[4] The author's reponse of the doubt https://www.science.org/doi/10.1126/science.abq4282

[5] The deepmind blog about this paper https://www.deepmind.com/blog/simulating-matter-on-the-quantum-scale-with-ai

[6] A study shows the inconsistancy of DM21 on one-electron systems https://arxiv.org/pdf/2208.06482.pdf

[7] Intro to DFT theory https://www.youtube.com/watch?v=Ez_Fm4iTUeo

## Video
