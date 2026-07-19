# Deutsch Algorithm

The Deutsch Algorithm is one of the first quantum algorithms that demonstrates how a quantum computer can solve a problem faster than a classical computer.

## Objective

Determine whether a function is:

- **Constant** – The function returns the same output for every input.
- **Balanced** – The function returns different outputs for different inputs.

## Key Concepts

- Qubits
- Superposition
- Hadamard Gate (H)
- Oracle
- Quantum Interference
- Measurement

## How It Works

1. Prepare two qubits.
2. Apply Hadamard gates to create superposition.
3. Pass the qubits through the oracle.
4. Apply another Hadamard gate.
5. Measure the first qubit.
6. Determine whether the function is constant or balanced.

## Classical vs Quantum

| Classical Computer | Quantum Computer |
|--------------------|------------------|
| Requires **2 queries** | Requires **1 query** |

## Files

- `deutsch_algorithm.ipynb` – Qiskit implementation
- `deutsch_algorithm.py` – Python code (optional)
- `images/` – Circuit diagrams and outputs (optional)

## Technologies Used

- Python
- Qiskit
- IBM Quantum Platform
- Google Colab

## Learning Outcomes

After completing this lesson, I will be able to:

- Understand the Deutsch Algorithm.
- Explain the difference between constant and balanced functions.
- Build the Deutsch Algorithm circuit in Qiskit.
- Execute and analyze the circuit results.

---

⭐ This folder contains theory notes, Qiskit implementation, and practice exercises for the Deutsch Algorithm.
