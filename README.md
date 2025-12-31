## Dynamic Cost–Efficiency Trade-off

<img src=".\figures\Dynamic-Cost-Efficiency-Tradeoff-Framework.jpg" alt="framework" style="zoom:10%;" />

This repository contains the code and documentation for the Dynamical Cost–Efficiency Trade-off framework, a pipeline for characterizing how whole-brain effective connectivity (EC) reorganizes under an explicit spatial distance constraint. Starting from parcel-wise BOLD time series and inter-regional distances, we fit a distance-constrained linear dynamical model to estimate a directed, weighted EC matrix, where long-range connections are selectively penalized via spatial distance regularization. By sweeping a single hyperparameter $\lambda$, the method yields a continuum of EC solutions that smoothly interpolates between low-cost, local architectures and high-efficiency, integrative architectures. For each solution, we compute communication cost and functional efficiency, producing an empirical cost–efficiency spectrum. We additionally provide a multi-objective genetic algorithm to approximate the Pareto-optimal front, enabling quantitative comparisons between empirical networks and theoretically attainable solutions. Together, these tools offer a simple and reproducible way to study network reconfiguration and construction principles of brain connectivity under explicit communication cost constraints.

## Requirements

**Operating Systems**: Windows 10, Ubuntu 20.04

**Python Version**: 3.12+

**Dependencies**: See `requirements.txt` file for details.

**Non-standard Hardware Requirements**: No non-standard hardware is required.

**Note on PyTorch**: We recommend installing the GPU version of PyTorch, especially if you plan to use large datasets. Fitting distance-constrained linear dynamical model can be computationally intensive and may take an extended period when running on CPU.

## Installation

1. Clone the repository: `git clone https://github.com/ncclab-sustech/Dynamic-Cost-Efficiency-Tradeoff`.
2. Navigate to the project directory: `cd Dynamic-Cost-Efficiency-Tradeoff`.
3. Install dependencies: `pip install -r requirements.txt`.

Typical installation time is approximately 5 minutes on a "normal" desktop computer.

## How to run

All code is provided as Jupyter notebooks and can be executed cell-by-cell. We provide three core demo notebooks in `demos/` that illustrate the main pipeline, and five reproduction notebooks in `notebooks/` that recreate the main result figures in the paper. After installing dependencies (see `requirements.txt`), open the notebooks in VS Code and run them sequentially.

## Demo examples

The `demos/` folder contains three self-contained notebooks that illustrate the core pipeline on minimal, runnable examples.

**demos/demo_01_subject_to_W.ipynb**: This demo uses resting-state fMRI from a single HCP subject, parcellated with the MMP atlas. Given the parcel time series and inter-regional distances, it fits the distance-constrained ridge regression model and returns an estimated EC matrix. It also reports two quick sanity checks: prediction $R^2$ and the correlation between model FC and empirical FC.

**demos/demo_02_W_to_metrics.ipynb**: This demo shows how to compute the graph-theoretic measures used in the paper from an estimated EC matrix, including communication cost, functional efficiency, local efficiency, modularity, small-worldness, and other related metrics.

**demos/demo_03_pareto.ipynb**: This demo runs a multi-objective genetic algorithm (GA) to approximate the Pareto front under simultaneous cost and efficiency objectives. It implements standard GA operators including crossover and mutation, and enforces constraints such as keeping network density fixed during evolution to ensure fair comparisons across candidate solutions.

## Reproduction notebooks

**notebooks/fig02_reproduce.ipynb**: Reproduce the main results in Fig. 2 (A distance-constrained linear dynamical model captures brain dynamics and inter-regional relationships).

**notebooks/fig03_reproduce.ipynb**: Reproduce the main results in Fig. 3 (Changes in communication cost and functional efficiency with increasing spatial distance constraint).

**notebooks/fig04_reproduce.ipynb**: Reproduce the main results in Fig. 4 (Comparison between human EC and Pareto-front solutions from a genetic algorithm).

**notebooks/fig05_reproduce.ipynb**: Reproduce the main results in Fig. 5 (Shifts of cost–efficiency trade-off from resting state to cognitive task states).

**notebooks/fig06_reproduce.ipynb**: Reproduce the main results in Fig. 6 (Task-evoked alterations in cost–efficiency trade-off of the depressive brain).

## Contact

For any questions/comments, please contact [NCC Lab](https://www.sustech.edu.cn/en/faculties/liuquanying.html).

## Copyright

Copyright © 2025 NCC Lab, Southern University of Science and Technology, Shenzhen, China.