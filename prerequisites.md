# Introduction & Prerequisites

## What is Quantum Computing?
Quantum computing is a different field of Computer Science that leverages the principles of quantum mechanics to process information in ways that classical computers  have difficulties with. Instead of using classical bits (0 or 1), quantum computers use **qubits**, which can exist in **superposition**—meaning they can represent both 0 and 1 at the same time.

## Understanding Qubits
A qubit is the most primitive unit of quantum information. Unlike classical bits, qubits take advantage of:
- **Superposition**: A qubit can be in a state of both 0 and 1 simultaneously.
- **Entanglement**: Qubits can become correlated, meaning the state of one qubit depends on another, no matter the distance between them.
- **Measurement**: When measured, a qubit collapses into either a 0 or a 1 with a certain probability.

## Quantum Gates and Operations
Quantum gates manipulate qubits in ways that enable quantum algorithms. Here are some fundamental quantum gates:

### **Pauli Gates**
- **X (Pauli-X)**: Equivalent to a NOT gate, flipping |0⟩ to |1⟩ and vice versa.

  Matrix representation:
  \[
  X = \begin{bmatrix} 0 & 1 \\ 1 & 0 \end{bmatrix}
  \]

  Acting on a qubit state:
  \[
  X |0\rangle = |1\rangle, \quad X |1\rangle = |0\rangle
  \]

- **Y (Pauli-Y)**: Introduces a phase shift and flips the qubit.

  Matrix representation:
  \[
  Y = \begin{bmatrix} 0 & -i \\ i & 0 \end{bmatrix}
  \]

  Acting on a qubit state:
  \[
  Y |0\rangle = i|1\rangle, \quad Y |1\rangle = -i|0\rangle
  \]

- **Z (Pauli-Z)**: Introduces a phase shift without flipping the qubit.

  Matrix representation:
  \[
  Z = \begin{bmatrix} 1 & 0 \\ 0 & -1 \end{bmatrix}
  \]

  Acting on a qubit state:
  \[
  Z |0\rangle = |0\rangle, \quad Z |1\rangle = -|1\rangle
  \]

### **Hadamard Gate (H)**
Creates superposition by transforming |0⟩ into an equal mix of |0⟩ and |1⟩:

  Matrix representation:
  \[
  H = \frac{1}{\sqrt{2}} \begin{bmatrix} 1 & 1 \\ 1 & -1 \end{bmatrix}
  \]

  Acting on a qubit state:
  \[
  H |0\rangle = \frac{|0\rangle + |1\rangle}{\sqrt{2}}, \quad H |1\rangle = \frac{|0\rangle - |1\rangle}{\sqrt{2}}
  \]

```python
from qcpy import QuantumCircuit
qc = QuantumCircuit(1)
qc.h(0)
```

### **CNOT Gate (CX)**
A controlled operation that flips the target qubit if the control qubit is in state |1⟩.

  Matrix representation:
  \[
  CX = \begin{bmatrix} 1 & 0 & 0 & 0 \\ 0 & 1 & 0 & 0 \\ 0 & 0 & 0 & 1 \\ 0 & 0 & 1 & 0 \end{bmatrix}
  \]

```python
qc.cx(0, 1)
```

### **Phase Gates**
- **S Gate**: Introduces a 90-degree phase shift.

  Matrix representation:
  \[
  S = \begin{bmatrix} 1 & 0 \\ 0 & i \end{bmatrix}
  \]

- **T Gate**: Introduces a 45-degree phase shift.

  Matrix representation:
  \[
  T = \begin{bmatrix} 1 & 0 \\ 0 & e^{i\pi/4} \end{bmatrix}
  \]

### **Rotation Gates**
- **RX, RY, RZ**: Rotate the qubit state around the X, Y, and Z axes.

  Matrix representation of RZ:
  \[
  RZ(\theta) = \begin{bmatrix} e^{-i\theta/2} & 0 \\ 0 & e^{i\theta/2} \end{bmatrix}
  \]

  Acting on a qubit:
  \[
  RZ(\theta) |0\rangle = e^{-i\theta/2} |0\rangle, \quad RZ(\theta) |1\rangle = e^{i\theta/2} |1\rangle
  \]

## Why Learn Quantum Computing?
Quantum computing has the potential to revolutionize fields such as cryptography, optimization, machine learning, and materials science. Understanding these principles is essential for working with QCPY and other quantum libraries.

For more on quantum gates, see the [Quantum Gates Reference](gates.md).
