# Bernstein–Vazirani Algorithm

## 1. Introduction

The **Bernstein–Vazirani (BV) algorithm** is a quantum algorithm used to find a hidden binary string.

It demonstrates an important idea in quantum computing:

> A quantum computer can discover a hidden `n`-bit string using only **one query** to a black-box function, whereas a classical computer needs multiple queries.

The algorithm is especially useful for understanding:

- Quantum superposition
- Quantum parallelism
- Oracle functions
- Phase kickback
- Hadamard gates
- Quantum interference
- Quantum query complexity
- Hidden information encoded in a function

The Bernstein–Vazirani problem is closely related to the **Deutsch–Jozsa algorithm**. In fact, the circuit used to solve the BV problem is essentially the Deutsch–Jozsa circuit applied to a more specific type of function.

---

# 2. The Bernstein–Vazirani Problem

Suppose we have a secret binary string:

```text
s = 1011
