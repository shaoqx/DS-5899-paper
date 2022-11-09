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

Some DFT details with fast pace: Schrödinger eq -> many body problem -> H-K principle 1 2 -> K-S equation -> SCF -> functional -> Eex
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

<font color=white size=3>People have had many tries on it and the ability to generilize the model is the core problem.</font>
### Q2

## Resource (done)

[1] DM21 repo https://github.com/deepmind/deepmind-research/tree/master/density_functional_approximation_dm21

[2] Comment on the paper from John P. Predew https://www.science.org/doi/10.1126/science.abm2445

[3] The doubt from Gerasimov et al. https://www.science.org/doi/10.1126/science.abq3385

[4] The author's reponse of the doubt https://www.science.org/doi/10.1126/science.abq4282

[5] The deepmind blog about this paper https://www.deepmind.com/blog/simulating-matter-on-the-quantum-scale-with-ai

[6] A study shows the inconsistancy of DM21 on one-electron systems https://arxiv.org/pdf/2208.06482.pdf

## Video
