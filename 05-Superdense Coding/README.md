# Superdense Coding

Superdense Coding is a quantum communication protocol that allows **two classical bits of information to be transmitted by sending only one qubit**, provided that the sender and receiver share an entangled pair of qubits beforehand.

> **Key Idea:** Shared quantum entanglement doubles the classical information capacity of a single transmitted qubit.

---

## Overview

Superdense Coding demonstrates one of the most powerful applications of quantum entanglement. By using a pre-shared Bell state, Alice can encode two classical bits into a single qubit, which Bob can decode after receiving that qubit.

---

## Topics Covered

- Introduction to Superdense Coding
- Bell States
- Quantum Entanglement
- Information Encoding
- Information Decoding
- Quantum Circuit Implementation
- Qiskit Simulation

---

## Learning Objectives

After completing this lesson, I will be able to:

- Explain the concept of Superdense Coding.
- Understand how entanglement increases communication efficiency.
- Encode two classical bits into a single qubit.
- Decode the transmitted information using quantum gates.
- Implement Superdense Coding using Qiskit.

---

## Communication Protocol

### Step 1: Create an Entangled Bell Pair

Alice and Bob share an entangled Bell state.

### Step 2: Alice Encodes Information

Depending on the two classical bits she wants to send, Alice applies one of the following operations:

| Classical Bits | Quantum Gate |
|----------------|--------------|
| 00 | Identity (I) |
| 01 | X |
| 10 | Z |
| 11 | X then Z |

### Step 3: Alice Sends One Qubit

Alice sends her qubit to Bob.

### Step 4: Bob Decodes

Bob applies:

- CNOT Gate
- Hadamard Gate

He then measures both qubits to recover the original two classical bits.

---

## Quantum Gates Used

- Hadamard (H)
- CNOT (CX)
- Pauli-X
- Pauli-Z
- Measurement

---

## Files

- `superdense_coding.ipynb` – Complete Qiskit implementation
- `superdense_coding.py` – Python version (optional)
- `images/` – Circuit diagrams and screenshots (optional)

---

## Circuit Workflow

1. Prepare a Bell State.
2. Alice encodes two classical bits.
3. Alice sends one qubit to Bob.
4. Bob decodes the message.
5. Measure both qubits.
6. Recover the original two-bit message.

---

## Technologies Used

- Python
- Qiskit
- IBM Quantum Platform
- IBM Quantum Lab
- Google Colab

---

## Applications

- Quantum Communication
- Quantum Networking
- Quantum Information Theory
- Quantum Internet
- Secure Information Transfer

---

## References

- IBM Quantum Learning
- Qiskit Documentation
- Nielsen & Chuang – *Quantum Computation and Quantum Information*

---

⭐ This folder contains theory notes, Qiskit implementations, practice exercises, and visualizations related to the Superdense Coding protocol.
