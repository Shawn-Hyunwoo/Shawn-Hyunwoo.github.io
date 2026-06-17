---
layout: page
title: Pado-Pauli — GPU-Accelerated Pauli Propagation
description: A GPU-accelerated, autodiff-enabled Pauli Propagation surrogate for fast variational quantum algorithm simulation, co-developed and publicly released at Norma.
img: assets/img/projects/pado-pauli.png
importance: 1
category: work
related_publications: false
---

**Pado-Pauli** is a GPU-accelerated, autodiff-enabled **Pauli Propagation surrogate** that I co-developed on the Quantum AI Team at [Norma](https://norma.co.kr/) and that we released publicly under AGPLv3.

🔗 **Code:** [github.com/Norma-Q/Pauli-Propagation---GPU-acceleration](https://github.com/Norma-Q/Pauli-Propagation---GPU-acceleration)

It propagates observables backward through a circuit in the Heisenberg picture, compiling a circuit **once** into a reusable sparse-tensor surrogate that can then be evaluated many times — exactly the workload shape of **VQE** and **QAOA**. The engine pairs a compiled **C++ backend (a PyTorch C++ extension)** with **native PyTorch autograd**, so gradients flow straight through expectation-value evaluation, with GPU work running on PyTorch CUDA tensors.

**Highlights**

- **~35–49× faster** on the GPU path than on the CPU path for medium-scale circuits, while keeping coefficient-truncation error **below 1e-4**.
- **Native batched evaluation** of embedding inputs (useful for quantum-native supervised learning), plus quasi-probability sampling and multi-GPU evaluation.
- Ships **nine tutorial notebooks** (CPU-vs-GPU timing, embedding-based training, QCBM on a TFIM ground state, MaxCut-QAOA) and a QAOA experiment suite with graph instances scaling up to **100 qubits**.

I authored ~80% of the commits and am the primary author of the core engine, the experiment suite, and the public README. Head-to-head benchmarks against other Pauli-propagation implementations are reported in a paper in preparation.

*Accepted as a poster ("Pado-Pauli") at the Conference on Quantum Information, Quantum Korea 2026.*
