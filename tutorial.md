# Tutorial: Creating Your First Quantum Circuit

## Introduction
This tutorial walks you through setting up and running your first quantum circuit using QCPY. You will:
1. Create a 2-qubit quantum circuit.
2. Apply a Hadamard gate to the first qubit.
3. Apply a CNOT gate, using the first qubit as control and the second as target.
4. Measure the circuit.

## Step 1: Setting Up Your Python File
Create a new Python file, e.g., `my_first_qc.py`, and start by importing QCPY:

```python
from qcpy import QuantumCircuit
```

## Step 2: Creating a Quantum Circuit
Now, define a quantum circuit with 2 qubits:

```python
qc = QuantumCircuit(qubits=2)
```

## Step 3: Applying Quantum Gates
First, apply a **Hadamard gate** to qubit 0 to create superposition:

```python
qc.h(0)  # Apply Hadamard gate to qubit 0
```

Next, apply a **CNOT (CX) gate** with qubit 0 as control and qubit 1 as target:

```python
qc.cx(0, 1)  # Apply CNOT gate
```

## Step 4: Measuring the Circuit
To obtain results, add a measurement step:

```python
qc.measure()
```

## Step 5: Running the Circuit
Finally, execute the quantum circuit and print the results:

```python
results = qc.run(shots=1024)
print(results)
```

## Expected Outcome
Running the script should output measurement results, showing a 50/50 probability of measuring `00` or `11` due to entanglement.

Example output:
```
{'00': 512, '11': 512}
```

Congratulations! 🎉 You've successfully created and executed your first quantum circuit using QCPY.

For more advanced tutorials, check out the [Usage Guide](usage.md).
