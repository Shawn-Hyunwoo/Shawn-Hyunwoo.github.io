---
layout: page
title: Pado-Pauli — GPU-Accelerated Pauli Propagation
description: Norma's in-house Pauli Propagation toolkit for quantum algorithm simulation
img: assets/img/3.jpg
importance: 1
category: work
related_publications: false
---

**Pado-Pauli** is Norma's in-house, publicly released Python toolkit for **Pauli Propagation–based**
quantum algorithm simulation, which I co-developed on the Quantum AI Team. It simulates operator
(Heisenberg-picture) evolution efficiently and supports diverse quantum algorithms — including **QAOA**
and **VQE** — with reduced quantum resource requirements.

**Performance highlights:**

- **~5,000× higher throughput** than Julia PauliPropagation, NVIDIA cuPauliProp, and Qiskit Pauli
  Propagation, via native batched processing (unsupported in any competing SDK).
- **~1.8× faster** forward/back-propagation than NVIDIA cuPauliProp through GPU-level optimization.
- Actively used across team projects and presented as a poster ("Pado-Pauli") at Quantum Korea 2026.
