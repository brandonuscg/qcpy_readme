# Introduction & Prerequisites

## What is Quantum Computing?
Quantum computing is a revolutionary field that leverages the principles of quantum mechanics to process information in ways that classical computers cannot. Instead of using classical bits (0 or 1), quantum computers use **qubits**, which can exist in **superposition**—meaning they can represent both 0 and 1 simultaneously.

## Understanding Qubits
A qubit is the fundamental unit of quantum information. Unlike classical bits, qubits take advantage of:
- **Superposition**: A qubit can be in a state of both 0 and 1 simultaneously.
- **Entanglement**: Qubits can become correlated, meaning the state of one qubit depends on another, no matter the distance between them.
- **Measurement**: When measured, a qubit collapses into either a 0 or a 1 with a certain probability.

## Quantum Gates and Operations
Quantum gates manipulate qubits in ways that enable quantum algorithms. Here are some fundamental quantum gates:

### **Pauli Gates**
- **X (Pauli-X)**: Equivalent to a NOT gate, flipping |0⟩ to |1⟩ and vice versa.
- **Y (Pauli-Y)**: Introduces a phase shift and flips the qubit.
- **Z (Pauli-Z)**: Introduces a phase shift without flipping the qubit.

### **Hadamard Gate (H)**
Creates superposition by transforming |0⟩ into an equal mix of |0⟩ and |1⟩:

```python
from qcpy import QuantumCircuit
qc = QuantumCircuit(1)
qc.h(0)
```

### **CNOT Gate (CX)**
A controlled operation that flips the target qubit if the control qubit is in state |1⟩.

```python
qc.cx(0, 1)
```

### **Phase Gates**
- **S Gate**: Introduces a 90-degree phase shift.
- **T Gate**: Introduces a 45-degree phase shift.

### **Rotation Gates**
- **RX, RY, RZ**: Rotate the qubit state around the X, Y, and Z axes.

## Why Learn Quantum Computing?
Quantum computing has the potential to revolutionize fields such as cryptography, optimization, machine learning, and materials science. Understanding these principles is essential for working with QCPY and other quantum libraries.

For more on quantum gates, see the [Quantum Gates Reference](gates.md).

