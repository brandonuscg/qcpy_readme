# Deutsch-Jozsa Algorithm

## Introduction
The **Deutsch-Jozsa algorithm** is one of the first quantum algorithms to demonstrate quantum speedup. It determines whether a given function \( f: \{0,1\}^n \rightarrow \{0,1\} \) is **constant** (same output for all inputs) or **balanced** (outputs 0 for half the inputs and 1 for the other half), using just a single evaluation in a quantum circuit.

This tutorial will walk you through implementing the Deutsch-Jozsa algorithm using QCPY for \( n = 1 \) (2 qubits total).

---

## Objective
Classically, you’d need to evaluate \( f(x) \) multiple times to determine whether it's constant or balanced. With the Deutsch-Jozsa algorithm, a quantum circuit can solve this in a single execution.

---

## Step-by-Step Implementation

### Step 1: Setup Your Python File
Create a new Python file:

```bash
vim deutsch_jozsa.py
```

And include the following imports:

```python
from qcpy import quantumcircuit, visualize, measure
```

### Step 2: Create the Circuit
We'll use 2 qubits:
- Qubit 0: Input
- Qubit 1: Output

```python
qc = quantumcircuit(qubits=2)
```

### Step 3: Initialize the Circuit
- Prepare the output qubit (qubit 1) in state |1⟩ using an X gate
- Apply Hadamard to both qubits to create superposition

```python
qc.x(1)
qc.h([0, 1])
```

### Step 4: Apply the Oracle
Define the oracle as either a **balanced** or **constant** function. For this example, we’ll implement a **balanced oracle** using a CNOT gate:

```python
qc.cx(0, 1)  # Balanced oracle: flips output if input is 1
```

To try a constant oracle, remove the `cx` gate or replace it with identity.

### Step 5: Apply Final Hadamard
```python
qc.h(0)
```

### Step 6: Measurement
```python
measure(qc)
```

### Step 7: View the Results
```python
print(qc)
print(qc.state)
visualize.probability(qc)
```

---

## Interpreting Results
- If the result is always `0`, the function is **constant**.
- If the result is not always `0`, the function is **balanced**.

Example output for a balanced function:
```
{'1': 1024}
```

---

## Full Code
```python
from qcpy import quantumcircuit, visualize, measure

qc = quantumcircuit(qubits=2)

qc.x(1)
qc.h([0, 1])

qc.cx(0, 1)  # Balanced oracle

qc.h(0)

measure(qc)

print(qc)
print(qc.state)

visualize.probability(qc)
```

---

## Next Steps
Try modifying the oracle to simulate different functions and see how the result changes. This is a powerful demonstration of quantum parallelism!

For more circuit examples, check out the [Tutorial](tutorial.md) and [Usage Guide](usage.md).
