# Quantum Registers

Quantum registers are collections of qubits used to store and manipulate quantum information in a quantum circuit. In Qiskit, registers help organize qubits and classical bits for computation and measurement.

---

## Topics Covered

- Introduction to Quantum Registers
- QuantumRegister in Qiskit
- ClassicalRegister in Qiskit
- Creating Registers
- Naming Registers
- Multiple Registers
- Accessing Individual Qubits
- Measuring Quantum Registers
- Register Visualization

---

## Learning Objectives

After completing this section, I will be able to:

- Understand the purpose of quantum and classical registers.
- Create quantum and classical registers using Qiskit.
- Build quantum circuits using registers.
- Measure qubits and store results in classical registers.
- Work with multiple registers in a single circuit.

---

## Example

```python
from qiskit import QuantumCircuit, QuantumRegister, ClassicalRegister

# Create registers
qr = QuantumRegister(2, 'q')
cr = ClassicalRegister(2, 'c')

# Create circuit
qc = QuantumCircuit(qr, cr)

# Apply gates
qc.h(qr[0])
qc.cx(qr[0], qr[1])

# Measure
qc.measure(qr, cr)

print(qc)
```

---

## Key Concepts

### Quantum Register (`QuantumRegister`)
- Stores one or more qubits.
- Used for quantum operations.
- Represented by `QuantumRegister()`.

### Classical Register (`ClassicalRegister`)
- Stores measurement results.
- Represented by `ClassicalRegister()`.

### Quantum Circuit (`QuantumCircuit`)
- Combines quantum and classical registers.
- Defines the sequence of quantum operations.

---

## Applications

- Quantum Algorithms
- Quantum Teleportation
- Quantum Error Correction
- Grover's Search Algorithm
- Shor's Algorithm
- Quantum Machine Learning

---

## Resources

- IBM Quantum Documentation
- Qiskit Documentation
- IBM Quantum Learning Platform

---

📌 This folder contains theory notes, Qiskit notebooks, and practice exercises related to Quantum Registers.
