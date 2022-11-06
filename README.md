# Pushing the frontiers of density functionals by solving the fractional electron problem
with transformer (or multilayer perceptron)

## Overview
### Background
### Problem
enhance efficiency and accuarcy. (design a new functional.)
### Approach
train a new functional that obeys two classes of mathematical constraints with fractional electrons.
only the $E_{ex}$ term is learned
#### dataset
fixed densities of reactant and product (by B3LYP) -> reaction energy (by experiment or CCSD(T)/CBS) 

#### Code demo
[Colab notebook](https://colab.research.google.com/drive/1wl7wB1vNYKgYIdsWwKryCs-DX1lZWURv?usp=sharing)
#### Architecture (formal pseudocode)

### Significance
correctly described bond breaking for charged and closed-shell neutral molecules
charge delocalization in a DNA base pair
magnetic properties of a compressed hydrogen chain
reaction barrier heights for a ring-opening intermediate with diradical character

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
### Q2

## Resource (need 5 other than the paper)
[1] DM21 repo https://github.com/deepmind/deepmind-research/tree/master/density_functional_approximation_dm21

[2] Comment on the paper from John P. Predew https://www.science.org/doi/10.1126/science.abm2445

[3] The doubt from Gerasimov et al. https://www.science.org/doi/10.1126/science.abq3385

[4] The author's reponse of the doubt https://www.science.org/doi/10.1126/science.abq4282

[5] The deepmind blog about this paper https://www.deepmind.com/blog/simulating-matter-on-the-quantum-scale-with-ai

[6] A study shows the inconsistancy of DM21 on one-electron systems https://arxiv.org/pdf/2208.06482.pdf

## Video
