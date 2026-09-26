# Exact Controllability of Protein-Folding Networks

Computational analysis of **controllability in complex networks**, with a focus on protein structure and protein-folding networks.

This project investigates how the topology of a complex interaction network determines which nodes must be controlled in order to steer the system toward a desired state. The analysis combines concepts from **control theory, network science, dynamical systems, and computational biology**.

## Overview

Many complex systems can be represented as networks in which nodes describe interacting components and edges encode their interactions.

For a dynamical system defined on a network,

$$
\dot{\mathbf{x}} = A\mathbf{x} + B\mathbf{u},
$$

the matrix $A$ describes interactions between nodes, while $B$ determines where external control signals are applied.

A central question is:

> **Which nodes must be controlled in order to make the entire network controllable?**

This repository explores this problem computationally, particularly for **protein residue-interaction networks**, where nodes represent amino-acid residues and edges describe structural interactions between them.

The goal is to identify important **driver nodes** and investigate how network topology influences controllability and potentially relates to protein-folding properties.

## Main Topics

The project explores several aspects of network controllability:

- exact and structural controllability;
- identification of driver nodes;
- controllability of complex interaction networks;
- maximum-matching approaches;
- control-energy considerations;
- network topology and controllability;
- protein residue-interaction networks;
- comparison of alternative node-selection strategies;
- relationship between network-control properties and protein folding.

## Mathematical Background

Consider a linear time-invariant dynamical system

$$

A\mathbf{x}(t)
+
B\mathbf{u}(t),
$$

where

- $\mathbf{x}(t)\in\mathbb{R}^{N}$ is the state of the network,
- $A\in\mathbb{R}^{N\times N}$ is the interaction or adjacency matrix,
- $B$ specifies the controlled nodes,
- $\mathbf{u}(t)$ represents external control signals.

For a finite-dimensional linear system, controllability can be analyzed through the controllability matrix

$$

\begin{bmatrix}
B & AB & A^2B & \cdots & A^{N-1}B
\end{bmatrix}.
$$

The system is controllable when

$$
\operatorname{rank}(\mathcal{C}) = N.
$$

In large complex networks, directly analyzing this condition can become computationally expensive and sensitive to the precise values of the interaction weights.

Network-based approaches therefore provide additional tools for studying controllability from the underlying graph structure.

## Structural Controllability

Structural controllability asks whether a system is controllable for almost all choices of nonzero interaction strengths consistent with a given network topology.

A central computational approach is based on **maximum matching**.

For a directed representation of the network:

1. a maximum matching is identified;
2. nodes that remain unmatched are interpreted as candidate **driver nodes**;
3. external control signals applied to these nodes can structurally control the network under the corresponding assumptions.

The number and location of driver nodes therefore provide information about how easily a given network can be controlled.

## Driver Nodes

A major objective of this project is to identify nodes whose control has a disproportionate influence on the dynamics of the entire system.

Different network-control approaches can generate different sets of important nodes.

Methods investigated in this project include concepts related to:

- maximum matching;
- structural controllability;
- minimum-energy control;
- feedback vertex sets;
- minimum dominating sets.

These approaches provide complementary ways of asking which components of a network are most relevant for controlling its global dynamics.

## Protein Networks

Proteins provide a natural example of a high-dimensional interacting system.

A protein structure can be represented as a graph

$$
G=(V,E),
$$

where

- $V$ represents amino-acid residues;
- $E$ represents interactions or spatial contacts between residues.

The resulting residue-interaction network captures structural information about the protein while allowing graph-theoretic and control-theoretic methods to be applied.

The computational workflow can be summarized as

```text
Protein structure
       ↓
Residue-interaction network
       ↓
Adjacency / interaction matrix
       ↓
Network controllability analysis
       ↓
Driver-node identification
       ↓
Network-control metrics
       ↓
Comparison with protein-folding properties
```

## Research Questions

The project is motivated by questions such as:

- How many nodes must be externally controlled to control a protein interaction network?
- Where are the corresponding driver nodes located?
- How does network topology affect controllability?
- Do different controllability criteria identify similar important residues?
- How does the required control effort depend on network structure?
- Are network-control properties associated with protein-folding behavior?

## Control Energy

Controllability alone determines whether a target state can theoretically be reached.

In practice, another important quantity is the amount of control effort required.

A quadratic control cost can be written as

$$
E =
\int_0^T
\mathbf{u}^{\mathrm T}(t)
\mathbf{u}(t)
,dt.
$$

For a controllable linear system, minimum-energy control can be analyzed using the controllability Gramian,

$$

\int_0^T
e^{A(T-\tau)}
BB^{\mathrm T}
e^{A^{\mathrm T}(T-\tau)}
,d\tau.
$$

The Gramian provides information not only about whether the system is controllable but also about how difficult different directions in state space are to reach.

This distinction is important for complex biological networks: two networks may both be controllable while requiring very different amounts of control effort.

## Computational Workflow

The analysis follows a general pipeline:

```text
Network construction
        ↓
Graph characterization
        ↓
Controllability formulation
        ↓
Maximum-matching / driver-node analysis
        ↓
Alternative node-selection strategies
        ↓
Control-energy analysis
        ↓
Statistical comparison across networks
        ↓
Biological interpretation
```

## Methods

The project combines techniques from several areas.

### Control Theory

- controllability analysis;
- controllability matrices;
- controllability Gramians;
- minimum-energy control;
- linear dynamical systems.

### Network Science

- graph representations;
- adjacency matrices;
- maximum matching;
- driver-node identification;
- network topology analysis.

### Computational Biology

- protein residue-interaction networks;
- structural representation of proteins;
- comparison of network properties across proteins;
- analysis of relationships between network structure and folding behavior.

### Numerical Analysis

- matrix computations;
- eigenvalue and rank analysis;
- numerical linear algebra;
- optimization;
- statistical comparison and visualization.

## Technologies

The project uses scientific-computing tools for numerical and network analysis, including Python-based workflows for:

- numerical linear algebra;
- graph analysis;
- optimization;
- statistical analysis;
- data visualization;
- interactive computational experiments.

Typical libraries useful for reproducing the analysis include:

```text
NumPy
SciPy
NetworkX
Matplotlib
pandas
Jupyter
```

## Getting Started

Clone the repository:

```bash
git clone https://github.com/laya-laya/Exact-controllability.git
cd Exact-controllability
```

A Python environment for the numerical analyses can be created with:

```bash
python -m venv .venv
source .venv/bin/activate
```

On Windows:

```bash
.venv\Scripts\activate
```

Install the main scientific-computing dependencies:

```bash
pip install numpy scipy pandas matplotlib networkx jupyter
```

Then start Jupyter:

```bash
jupyter notebook
```

## Why Controllability Matters

Network topology does more than determine which components interact.

It also determines how perturbations and control signals propagate through the system.

Controllability analysis therefore provides a framework for connecting

[
\text{network structure}
\quad\longrightarrow\quad
\text{dynamical influence}
\quad\longrightarrow\quad
\text{system-level behavior}.
]

In biological systems, this perspective can help identify structurally important components that have a strong influence on collective dynamics.

## Project Context

This project was developed as part of work at the intersection of **systems biology, control theory, and complex systems**.

The broader objective was to use mathematical and computational tools to investigate how the interaction structure of biological networks influences their dynamical behavior and controllability.

## Author

**Laya Parkavousi**

Computational physicist working on complex systems, nonlinear dynamics, network science, control theory, scientific computing, and data-driven modeling.

GitHub: [@laya-laya](https://github.com/laya-laya)

## License

If you reuse or extend this work, please refer to the license provided with the repository.
