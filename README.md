# PkTron v9.0.6

<div align="center">

<img src="https://raw.githubusercontent.com/YOUR_USERNAME/pktron/main/docs/logo.png" width="180"/>

### Advanced Quantum Computing Framework

[![Python](https://img.shields.io/badge/Python-3.9+-blue.svg)]()
[![License](https://img.shields.io/badge/License-MIT-green.svg)]()
[![Version](https://img.shields.io/badge/Version-9.0.6-orange.svg)]()
[![Platform](https://img.shields.io/badge/Platform-Windows%20%7C%20Linux%20%7C%20macOS-success.svg)]()

**Compiler • Simulation • Runtime • Noise Modeling • Quantum Algorithms • HPC**

Developed by **CETQAP – Centre of Excellence for Technology Quantum and AI Pakistan**

---

⭐ If you find PkTron useful, please consider giving this repository a star.

</div>

---

# What's New in v9.0.6

PkTron 9.0.6 introduces major improvements to quantum circuit compilation, hardware-aware optimization, runtime execution, noise learning, and binary circuit serialization.

## New Features

### PkDag

A Directed Acyclic Graph (DAG) representation of quantum circuits for compiler development.

Features

- Topological ordering
- Predecessor queries
- Successor queries
- In-place node substitution
- Custom transpiler pass development

Designed to mirror the interface of Qiskit's C-API QkDag while remaining a pure Python implementation.

---

### TranspileStage

Build custom transpiler stages without rebuilding the complete compilation pipeline.

Supports

- Modular optimization passes
- Compiler research
- Custom transformations
- DAG-based workflows

---

### CouplingMap

Hardware connectivity model with graph utilities.

Features

- Device connectivity
- BFS shortest-path distance
- Neighbor lookup
- Hardware routing support

Example

```python
from pktron.transpiler import CouplingMap

coupling = CouplingMap([
    (0,1),
    (1,2),
    (2,3)
])

print(coupling.distance(0,3))
```

---

### Target

Rich quantum hardware description.

Supports

- Gate error rates
- Qubit T1 values
- Qubit T2 values
- Readout errors
- Hardware capabilities

Example

```python
target = Target.from_coupling_map(coupling)
```

---

### VF2Layout

Performs VF2-based subgraph isomorphism to determine efficient logical-to-physical qubit mappings.

Benefits

- Better hardware placement
- Reduced routing overhead
- Improved execution fidelity

---

### VF2PostLayout

Performs post-routing optimization using hardware calibration data.

Automatically searches for lower-error qubit mappings using Target information.

---

### GridsynthDecomposer

Single-qubit Clifford+T decomposition for Rz rotations.

Capabilities

- Exact synthesis for Clifford+T angles
- π/4 → T
- π/2 → S
- Approximate synthesis for arbitrary rotations
- Maximum operator norm error approximately 0.10
- Automatic verification against the ideal rotation

---

### RuntimeExecutor

New quantum runtime execution engine.

Unlike AsyncExecutor, RuntimeExecutor executes quantum jobs using a backend-oriented workflow.

Example

```python
job = runtime.run(program)

print(job.status())

result = job.result()
```

Supports

- Job submission
- Job monitoring
- Result retrieval

---

### PauliNoiseLearnerV2

Incremental quantum noise model refinement.

New

```python
learner.update(calibration_data)
```

Features

- Exponential Moving Average updates
- Incremental calibration
- Preserves historical knowledge
- Continuous hardware adaptation

---

### QPYCodec

Exact binary quantum circuit serialization.

Supports

- Lossless circuit storage
- Binary encoding
- Portable serialization

---

### FastQPYCodec

Optimized serializer for repetitive workloads.

Instead of storing repeated gates multiple times, FastQPYCodec stores them once and references them.

Benchmark Results

| Workload | Payload Size |
|-----------|-------------|
| Standard QPY | 100% |
| FastQPYCodec | **Up to 45× smaller** |

*Measured using the included `benchmark_qpy` benchmark on repetitive circuits. Serialization speed is comparable to the standard codec; the primary benefit is reduced payload size.*

---

# Installation

```bash
pip install pktron
```

Upgrade

```bash
pip install --upgrade pktron
```

---

# Supported Modules

- Quantum Circuit Builder
- Quantum Algorithms
- Quantum Simulator
- Noise Simulation
- Runtime Execution
- Hardware Targeting
- Compiler Infrastructure
- Quantum Machine Learning
- Error Mitigation
- Circuit Serialization
- HPC Utilities
- Visualization

---

# Example

```python
from pktron import QuantumCircuit

qc = QuantumCircuit(2)

qc.h(0)
qc.cx(0,1)

print(qc)
```

---

# Why PkTron?

✅ Pure Python Framework

✅ Modern Quantum Compiler

✅ Hardware-Aware Optimization

✅ Runtime Execution

✅ Adaptive Noise Learning

✅ Efficient Binary Serialization

✅ Research Friendly

✅ Open Source

---

# Documentation

Documentation continues to expand with every release.

Explore:

- Compiler
- Runtime
- Noise Models
- Algorithms
- Serialization
- Hardware Targets
- Examples

---

# Contributing

Contributions are welcome.

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Open a Pull Request

---

# Citation

If you use PkTron in your research, please cite the project appropriately.

---

# License

MIT License

---

# Developed By

**CETQAP**
**Centre of Excellence for Technology Quantum and AI Pakistan**

Advancing Quantum Computing Research, Education, and Innovation.

---

## Star the Repository ⭐

If PkTron helps your research or projects, please consider giving the repository a ⭐ on GitHub.

Every star helps support future development.
