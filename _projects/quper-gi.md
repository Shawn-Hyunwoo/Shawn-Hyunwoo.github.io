---
layout: page
title: QuPer-GI — Variational Quantum Algorithm for Graph Isomorphism
description: A from-scratch PennyLane reproduction of the QuPer VQA (arXiv:2505.05981) for graph isomorphism, with an original subgraph-isomorphism extension.
img: assets/img/projects/quper-gi.png
importance: 1
category: research
related_publications: false
---

**QuPer-GI** is a from-scratch **PennyLane** implementation of the **QuPer** variational quantum algorithm ([arXiv:2505.05981](https://arxiv.org/abs/2505.05981)) applied to the **graph isomorphism (GI)** problem.

🔗 **Code:** [github.com/Shawn-Hyunwoo/QUPER_GI_Implementation](https://github.com/Shawn-Hyunwoo/QUPER_GI_Implementation)

A variational circuit on **2q + 2m qubits** (O(log N)) with a Bruhat-decomposition ansatz emits a doubly-stochastic matrix, which is optimized against a classical Frobenius cost and projected to a hard permutation.

**What's in it**

- **Validated against the paper's own results:** committed tests exhaustively reproduce the circuit-span counts of arXiv:2505.05981 (q=2: Borel 8 / Bruhat 24), and an audit script reproduces q=3 (Borel 64 / Bruhat 1,344) — exact match.
- **Reproduced the GI scaling behavior** of the paper (small planted instances solve; larger N plateaus) and diagnosed the stall as a classical-optimizer landscape trap — via multi-start success and a non-collapsing gradient-norm trajectory — rather than a barren plateau.
- **Original extension:** a subgraph-isomorphism (monomorphism / induced) training pipeline reusing the same circuit, solving planted instances up to **N=64** (monomorphism) and N=16 (induced).
- **25 tests, all passing.** Two research journals document the work self-critically, explicitly noting that all experiments are exact classical simulation (≤20 qubits) and that no quantum advantage is demonstrated at this scale.
