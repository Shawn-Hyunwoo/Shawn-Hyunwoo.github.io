---
layout: page
title: PADO-Pauli — GPU-Accelerated Pauli Propagation
description: A GPU-accelerated, differentiable Pauli-propagation engine for fast variational quantum algorithm simulation, co-developed and publicly released at Norma.
img: assets/img/projects/pado-pauli.png
importance: 1
category: work
related_publications: false
---

**PADO-Pauli** is a GPU-accelerated, autodiff-enabled **Pauli Propagation surrogate** that I co-developed on the Quantum AI Team at [Norma](https://norma.co.kr/) and that we released publicly under AGPLv3.

📄 **Paper:** [arXiv:2610.17755](https://arxiv.org/abs/2610.17755) &nbsp;·&nbsp; 🔗 **Code:** [github.com/Norma-Q/PADO-Pauli](https://github.com/Norma-Q/PADO-Pauli)

It propagates observables backward through a circuit in the Heisenberg picture, compiling a circuit **once** into reusable sparse tensor maps that can then be evaluated many times — exactly the workload shape of **VQE**, **QAOA** and quantum machine learning. The engine pairs a compiled **C++ backend (a PyTorch C++ extension)** with **native PyTorch autograd**, so gradients flow straight through expectation-value evaluation into any classical layer, with GPU work running on CUDA and ROCm.

**Highlights**

- **Zero filtering** removes propagated Pauli terms that cannot contribute to the result: ~1.5× faster batched evaluation and 1.4–3.0× lower steady-state memory, with no change to any result.
- **Against NVIDIA cuPauliProp** on one A100 80 GB: **2.7–10.1× faster evaluation**, 3.3–13.3× faster forward and backward passes, **206× higher throughput** on batched inputs, and **3.1× less GPU memory** at 16 qubits (14.5 vs. 45.4 GB) — completing a setting in which cuPauliProp ran out of device memory.
- **Beyond 100 qubits:** reproduces IBM's 127-qubit kicked-Ising utility experiment on a single AMD MI300X with under 0.7 GB of GPU memory (RMS deviation 0.032 from the hardware data). Accuracy is checked against exact statevector simulation up to 28 qubits.
- **Native batched evaluation** of embedding inputs (useful for quantum-native supervised learning), truncation by Pauli weight and coefficient size, noise channels, and quasi-probability sampling.
- **Scaling out:** a hybrid CPU-storage / GPU-compute mode for problems beyond one GPU's memory, a multi-GPU prototype on an 8-GPU NVIDIA Blackwell node, and an initial port to the **Tenstorrent Blackhole p150a NPU**.
- Ships **nine tutorial notebooks** (CPU-vs-GPU timing, embedding-based training, QCBM on a TFIM ground state, MaxCut-QAOA) and a QAOA experiment suite with graph instances scaling up to **100 qubits**.

I authored ~80% of the commits and am the primary author of the core engine, the experiment suite, and the public README. PADO-Pauli is also the classical surrogate behind our [SAFE ma-QAOA](https://arxiv.org/abs/2605.23377) method.

_Presented as posters at IEEE Quantum Week (QCE 2026, Toronto; two-page paper in the Poster Track) and the ML4QT Symposium 2026 (Waterloo)._
