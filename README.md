# Graph Bootstrap Reproduction

## Overview

This repository provides an implementation to reproduce the simulation results from:

**"[Bootstrapping Exchangeable Random Graphs" (Green & Shalizi)](https://projecteuclid.org/journals/electronic-journal-of-statistics/volume-16/issue-1/Bootstrapping-exchangeable-random-graphs/10.1214/21-EJS1896.full)**.


The goal is to study bootstrap-based uncertainty quantification for graph statistics,  
specifically **motif densities**, under exchangeable random graph models.

We focus on evaluating:

- Coverage probability of confidence intervals
- Width of confidence intervals

for different bootstrap methods.

---

## Scope

This repository includes:

- Empirical graphon bootstrap (fully implemented)
- Histogram (block model) bootstrap (optional / partially reproducible)
- Simulation under multiple graphon models
- Evaluation using motif densities

---

## Methods

### Graph model

Graphs are generated from a graphon model:

$$
A_{ij} \sim \text{Bernoulli}(h_n(U_i, U_j)), \quad U_i \sim \text{Uniform}(0,1)
$$

where

$$
h_n(u,v) = \rho_n \cdot w(u,v), \quad \int w(u,v)\,du\,dv = 1
$$

---

### Motif density

Motifs considered:

- Edge (K2)
- Triangle
- 2-star
- 4-cycle

---

## Simulation Setup

### Parameters

- Sample size:
  
  n \in \{25, 50, 75, \dots, 400\}
  

- Sparsity levels:
  $
  \rho_n \in \{0.02, 0.1, 0.25\}
  $

- Bootstrap replications: 100  
- Monte Carlo repetitions: 1000  
- Nominal confidence level: 0.7  

- Bootstrap sample size: $m = n$

---

### Graphon models

#### Gaussian

$$
w(u,v) \propto \exp\left(-\frac{(u-v)^2}{2(1/5)^2}\right)
$$

#### 2-block SBM

- Within block: high probability
- Between block: low probability

#### Horseshoe

$$
w(u,v) \propto \frac{1}{(u-v)^2 + 0.01}
$$

All graphons are normalized to satisfy:
$$
\int w(u,v)\,du\,dv = 1
$$

---

## Evaluation

### Coverage probability

For each simulation:

$$
\text{Coverage} = \mathbf{1}(\theta \in CI)
$$

We report average coverage across Monte Carlo runs.

---

### Confidence interval width

$$
\text{Width} = CI_{\text{upper}} - CI_{\text{lower}}
$$

---

### Confidence interval construction

We use **percentile bootstrap**:

$$
CI = [q_{\alpha/2}, q_{1-\alpha/2}]
$$

with $\alpha = 0.3$.

---

## Installation

### Python environment

```bash
pip install numpy scipy networkx tqdm matplotlib
