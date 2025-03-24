# QCPY - Quantum Computing for Python

QCPY is an open-source Python library designed for simulating and visualizing quantum circuits. It provides an intuitive interface for building quantum algorithms, exploring quantum mechanics concepts, and leveraging GPU acceleration for quantum simulations.

## 📌 Features
- Construct and manipulate quantum circuits
- Apply quantum gates (Pauli, Hadamard, T, Controlled, etc.)
- Simulate quantum states and amplitudes
- GPU-accelerated quantum computations
- Visualize circuits with Q-spheres, Bloch spheres, and state vector diagrams

## 📖 Documentation
This README provides a high-level overview. For in-depth documentation, visit the following sections:

- [Introduction & Prerequisites](prerequisites.md)
- [Installation Guide](installation.md)
- [Usage Guide](usage.md)
- [Quantum Gates Reference](gates.md)
- [API Documentation](api_reference.md)
- [Visualization Guide](visualization.md)
- [Tutorial for First Quantum Circuit](tutorial.md)
- [Deutsch-Jorza Algorithm Example](deutsch-jorza.md)

---

## 🛠️ Installation

To install QCPY, use `pip`:

```sh
pip install qcpydev
```

To use QCPY in your Python project, import the library:

```python
from qcpy import quantumcircuit
```

For more setup details, visit the [Installation Guide](installation.md).

---

## 🚀 Getting Started

### Creating a Quantum Circuit

You can create a simple quantum circuit using the `QuantumCircuit` class:

```python
from qcpy import QuantumCircuit

qc = QuantumCircuit(qubits=3)
qc.h(0)  # Apply Hadamard gate to qubit 0
qc.cx(0, 1)  # Apply CNOT gate with control 0 and target 1
print(qc.state)  # Print quantum state
```

For advanced examples, see the [Usage Guide](usage.md).

---

## 📚 Learning Quantum Computing

New to quantum computing? Start with the [Introduction & Prerequisites](prerequisites.md), covering:
- What are qubits?
- Basic quantum gates (Hadamard, Pauli, CNOT, etc.)
- Concepts of superposition and entanglement

Explore the **[Quantum Gates Reference](gates.md)** for a deeper understanding.

---

## 🎨 Visualizing Quantum Circuits

QCPY includes built-in visualization tools:

```python
from qcpy import QuantumCircuit, visualize

qc = QuantumCircuit(qubits=3)
qc.h([0, 1, 2])

visualize.qsphere(qc)  # Display Q-Sphere representation
```

More visualization methods are detailed in the [Visualization Guide](visualization.md).

---

## 🤝 Contributions

We welcome contributions! See our [Contributing Guide](CONTRIBUTING.md) for more details.

For questions, discussions, or support, [join our community on Discord](https://discord.gg/jWxYXFzraK).

---

## 📜 License

QCPY is released under the MIT License. See the [LICENSE](LICENSE) file for details.
