# Graph Bootstrap Reproduction

## 1. What is this repository for?

This repository reproduces the simulation results from the paper  
**"Bootstrapping Exchangeable Random Graphs" (Green & Shalizi)**.

The goal is to evaluate bootstrap methods (empirical graphon and histogram-based)  
in terms of **coverage probability** and **confidence interval width** for motif densities.

---

## 2. How to run

### Environment

- Python 3.10+
- Recommended libraries:
  - numpy
  - scipy
  - networkx
  - tqdm
  - matplotlib

Install dependencies:

```bash
pip install numpy scipy networkx tqdm matplotlib
```