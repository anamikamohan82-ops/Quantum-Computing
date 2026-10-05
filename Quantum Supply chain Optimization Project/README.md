# Supply Chain Optimization using Qiskit

## Project Overview

This project implements a supply chain optimization model using **Qiskit Optimization** to determine the most cost-effective way to operate warehouses and distribute products to customers.

The objective is to minimize the total operational cost by selecting which warehouses to open and assigning each customer to an appropriate warehouse while satisfying warehouse capacity constraints.

The optimization problem is formulated as a **Quadratic Program (QP)** with binary decision variables and solved using Qiskit's `MinimumEigenOptimizer` with a classical `NumPyMinimumEigensolver`.

## Problem Statement

A supply chain network consists of three potential warehouses (A, B and C) and three customers (C1, C2 and C3).

Each warehouse has:
- A fixed opening cost.
- A limited capacity.
- A different cost of serving each customer.

The goal is to minimize the total cost while ensuring that:
- Every customer is assigned to exactly one warehouse.
- A customer can only be served by an open warehouse.
- The total assigned demand does not exceed the capacity of any warehouse.

## Technologies Used

- Python
- Qiskit
- Qiskit Optimization
- Qiskit Algorithms
- NumPy
- Google Colab

## Mathematical Formulation

### Decision Variables

- `x_A`, `x_B`, `x_C`: Binary variables indicating whether a warehouse is open (1) or closed (0).
- `y_A_C1`, `y_A_C2`, etc.: Binary variables indicating whether a customer is assigned to a particular warehouse.

### Objective Function

Minimize the total warehouse opening and customer assignment costs:

\[
\begin{aligned}
\min Z ={}& 8x_A+6x_B+5x_C\\
&+2y_{A,C1}+5y_{A,C2}+3y_{A,C3}\\
&+4y_{B,C1}+2y_{B,C2}+y_{B,C3}\\
&+3y_{C,C1}+4y_{C,C2}+2y_{C,C3}
\end{aligned}
\]

### Constraints

**1. Customer assignment**

Each customer must be assigned to exactly one warehouse.

\[
y_{A,Cj}+y_{B,Cj}+y_{C,Cj}=1
\]

for each customer \(j\).

**2. Warehouse opening**

A customer can only be assigned to a warehouse if it is open.

\[
y_{i,j}\leq x_i
\]

**3. Warehouse capacity**

The total demand allocated to a warehouse cannot exceed its capacity.

- Warehouse A: capacity 40
- Warehouse B: capacity 30
- Warehouse C: capacity 20

Customer demands are:
- C1: 20
- C2: 15
- C3: 10

**4. Binary restrictions**

All decision variables are binary:

\[
x_i,y_{i,j}\in\{0,1\}
\]

## Methodology

1. Define the supply chain optimization problem using Qiskit's `QuadraticProgram`.
2. Create binary decision variables for warehouse opening and customer assignments.
3. Define the objective function to minimize total costs.
4. Add customer assignment, warehouse linking and capacity constraints.
5. Solve the optimization problem using `MinimumEigenOptimizer` and `NumPyMinimumEigensolver`.
6. Extract the optimal warehouse decisions, customer assignments and objective value.
7. Interpret the results to identify the most cost-effective warehouse configuration.

## Results

The optimization model returned the following solution for the given input costs and constraints:

| Metric | Result |
|---|---|
| Minimum total cost | 13 |
| Warehouse A | Closed |
| Warehouse B | Open |
| Warehouse C | Closed |
| Customer C1 | Warehouse B |
| Customer C2 | Warehouse B |
| Customer C3 | Warehouse B |
| Solver status | Success |

The model selects Warehouse B as the only operating warehouse and assigns all three customers to it. Its capacity of 30 is sufficient for the total demand of 45 only if interpreted otherwise, so this reported assignment needs to be checked against the stated capacity constraint before treating it as a feasible solution.

## Conclusion

This project demonstrates how a supply chain facility-location and customer-assignment problem can be represented as a binary optimization problem using Qiskit.

It provides practical experience in mathematical optimization, binary decision variables, constraint modeling and the use of Qiskit optimization algorithms.

The current implementation uses a classical exact eigensolver as a benchmark. It does not require access to quantum hardware, but the model provides a foundation for exploring QUBO formulations and quantum optimization methods in future extensions.

## Future Improvements

- Formulate and validate the problem as a QUBO.
- Experiment with QAOA for approximate optimization.
- Compare exact classical solutions with quantum-inspired and quantum algorithms.
- Extend the model to larger supply chain networks with more warehouses and customers.
- Visualize warehouse selection and customer allocation.

## Author

**Anamika Mohan**

MSc Physics | Exploring Quantum Computing and Quantum Optimization

