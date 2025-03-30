# Deutsch-Jozsa Algorithm

## Introduction
The **Deutsch-Jozsa algorithm** is a foundational quantum algorithm that determines whether a function `f: {0,1}^n → {0,1}` is **constant** (returns the same output for all inputs) or **balanced** (returns 0 for exactly half of all inputs and 1 for the other half). It does this exponentially faster than any classical algorithm.

In this tutorial, we’ll implement the original **Deutsch algorithm** (for `n = 1`), then describe how this scales into the more general Deutsch-Jozsa algorithm.

---

## Background: The Problem
Given a black-box function `f: {0,1} → {0,1}`, we want to determine whether it's **constant** or **balanced**. There are only four such functions:

| f(x)        | f(0) | f(1) | Type     |
|-------------|------|------|----------|
| f₁(x) = 0   | 0    | 0    | constant |
| f₂(x) = x   | 0    | 1    | balanced |
| f₃(x) = ¬x  | 1    | 0    | balanced |
| f₄(x) = 1   | 1    | 1    | constant |

Classically, you need two evaluations to decide. Quantumly, you need just **one**.

---

## Deutsch Algorithm: Step-by-Step

### Step 1: Set Up
Create a new Python file:
```bash
vim deutsch.py
```
And add the following:
```python
from qcpy import quantumcircuit, visualize, measure
```

### Step 2: Create a 2-Qubit Circuit
```python
qc = quantumcircuit(qubits=2)
```

### Step 3: Prepare the Initial State
- Set qubit 1 (the output qubit) to `|1⟩` via X gate.
- Apply Hadamard gates to both qubits to create superposition.
```python
qc.x(1)
qc.h([0, 1])
```

### Step 4: Apply the Oracle
The oracle implements one of the 4 possible f(x) functions. For example:
- **f(x) = x** → `qc.cx(0, 1)`
- **f(x) = 1** → `qc.x(1)`

To simulate a balanced function:
```python
qc.cx(0, 1)
```

### Step 5: Apply Final Hadamard Gate
Apply H to the input qubit (qubit 0) to complete the interference step:
```python
qc.h(0)
```

### Step 6: Measure the Input Qubit
```python
measure(qc)
```

### Step 7: View Results
```python
print(qc)
print(qc.state)
visualize.probability(qc)
```

---

## Expected Results
- If the measured result is **|0⟩**, then f(x) is **constant**.
- If the measured result is **|1⟩**, then f(x) is **balanced**.

---

## Full Deutsch Algorithm Example
```python
from qcpy import quantumcircuit, visualize, measure

qc = quantumcircuit(qubits=2)

qc.x(1)
qc.h([0, 1])
qc.cx(0, 1)  # Oracle for f(x) = x
qc.h(0)

measure(qc)

print(qc)
print(qc.state)
visualize.probability(qc)
```

---

## Deutsch-Jozsa Generalization
To generalize for `n > 1`, initialize `n` input qubits and one output qubit:
```python
qc = quantumcircuit(qubits=4)  # 3 inputs + 1 output
qc.x(3)
qc.h([0, 1, 2, 3])
# Apply oracle here
qc.h([0, 1, 2])
measure(qc)
```

**Interpretation:**
- If all measured bits = 0 → function is constant.
- Otherwise → function is balanced.

See the [Qiskit simulation example](https://learning.quantum.ibm.com/course/fundamentals-of-quantum-algorithms/quantum-query-algorithms) for building full Deutsch-Jozsa circuits.

---

## Notes
- The Deutsch algorithm relies on **quantum interference**.
- The output qubit is initialized to `|1⟩` to enable phase kickback via the Hadamard basis.
- The final Hadamard gate reveals the interference pattern in the input qubit.

---

For deeper background, see lecture references and the original Qiskit examples in `cs385QC_2025sp_lect14_deutsch_qiskit.py` and `cs385QC_2025sp_lect14_deutschjozsa_qiskit.py`.
