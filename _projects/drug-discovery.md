---
layout: page
title: Quantum Generative Models for Drug Discovery
description: Hybrid quantum–classical generative models for de novo molecular design, targeting the KRAS G12D oncology target.
importance: 2
category: work
related_publications: false
---

At [Norma](https://norma.co.kr/)'s Quantum AI Team I lead a research line on **hybrid quantum–classical generative models** for *de novo* drug design, targeting **KRAS G12D** inhibitor candidates. *(Internal project — no public repository.)*

**Pipeline.** A seq2seq autoencoder (~**99.5%** validation token accuracy) compresses molecules (SMILES) into a compact latent space; a **quantum-noise-driven Wasserstein GAN** — in which a PennyLane parameterized circuit (ZZ feature map + entangling layers) reshapes the generator's noise prior — learns that latent distribution and proposes new molecules. From 30,000 samples the pipeline produced **18,343 unique valid molecules**, scored by QED / SA / logP.

**Method, reported honestly.** In a focused follow-up I diagnosed that a baseline GAN was placing samples ~1.8× off the data manifold despite matching the marginal distribution, and designed a **manifold-proximity hinge loss** that raised decode-validity from **18.7% → 32.65%** while preserving ~98% uniqueness. A controlled experiment that swapped *only* the generator's noise source for a 16-qubit Pauli-propagation-surrogate quantum circuit gave **no validity gain** over the classical baseline on a single seed — written up as an honest negative result rather than a quantum-advantage claim.

**Beyond simulation.** The project also includes a neural-network **quantum error-mitigation** model on QAOA/VQE circuits and circuit execution on **IBM's `ibm_fez`** quantum hardware with zero-noise extrapolation.

*Initiated during the KQIC Quantum Internship (NIA, 4th cohort) and continued at Norma; part of an NRF Korea Quantum Computing Challenge effort.*
