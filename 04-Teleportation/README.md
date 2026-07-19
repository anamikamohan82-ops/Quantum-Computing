# 04 - Quantum Teleportation

Quantum Teleportation is one of the most important protocols in quantum computing. It enables the transfer of an unknown quantum state from one qubit to another without physically moving the qubit itself.

> **Note:** Quantum teleportation transfers the *state* of a qubit, not the physical qubit.

---

## Overview

Quantum teleportation relies on three key principles of quantum mechanics:

- Quantum Entanglement
- Quantum Measurement
- Classical Communication

The protocol allows a sender (Alice) to transmit an unknown quantum state to a receiver (Bob) using:

- One entangled qubit pair
- Two classical bits of information
- Quantum gates and measurements

---

## Topics Covered

- Introduction to Quantum Teleportation
- Bell States
- Quantum Entanglement
- Alice and Bob Protocol
- Quantum Measurement
- Classical Communication
- Quantum Circuit Implementation
- Teleportation using Qiskit

---

## Learning Objectives

After completing this lesson, I will be able to:

- Explain the concept of quantum teleportation.
- Understand the role of entanglement in communication.
- Build a teleportation circuit using Qiskit.
- Simulate the protocol using IBM Quantum tools.
- Interpret the measurement outcomes.

---

## Files

- `quantum_teleportation.ipynb` – Complete Qiskit implementation
- `quantum_teleportation.py` – Python version (optional)
- `images/` – Circuit diagrams and screenshots (optional)

---

## Circuit Components

The teleportation protocol uses:

- Hadamard (H) Gate
- CNOT (CX) Gate
- Measurement
- Conditional X Gate
- Conditional Z Gate

---

## Workflow

1. Prepare the quantum state to be teleported.
2. Create an entangled Bell pair.
3. Alice performs Bell-state measurements.
4. Alice sends two classical bits to Bob.
5. Bob applies correction gates (X and Z).
6. Bob reconstructs the original quantum state.

---

## Technologies Used

- Qiskit
- Google Colab

---

## Applications

- Secure Quantum Communication
- Quantum Networks
- Distributed Quantum Computing
- Quantum Internet
- Quantum Cryptography

---

## References

- IBM Quantum Learning
- Qiskit Documentation
- Nielsen & Chuang – *Quantum Computation and Quantum Information*

---

⭐ This folder contains theory notes, Qiskit implementations, practice exercises, and visualizations related to Quantum Teleportation.
