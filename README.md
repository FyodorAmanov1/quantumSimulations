# QuantumSimulations

```markdown
# Quantum Simulation of the H2, H2O, HCL and citric acid Molecules with Qiskit

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/FyodorAmanov1/quantumSimulations/blob/main/molecules_qiskit.ipynb)

This repository contains a Jupyter Notebook demonstrating quantum simulation of the H2, H2O, HCL and citric acid Molecules using Qiskit. The implementation includes Hamiltonian construction, quantum circuit optimization, and molecular orbital visualization.

## Features

- Quantum simulation of the H2, H2O, HCL and citric acid Molecules molecule using the Variational Quantum Eigensolver (VQE)
- Jordan-Wigner transformation for fermionic-to-qubit Hamiltonian conversion
- Custom quantum ansatz construction with parameterized quantum circuits
- 3D visualization of molecular orbitals
- Energy calculation and quantum algorithm optimization

## Requirements

- Python 3.7+
- Jupyter Notebook
- Qiskit (with Nature and Aer components)
- NumPy
- Matplotlib

## Installation

1. Clone the repository:
```bash
git clone https://github.com/FyodorAmanov1/quantumSimulations.git
cd quantumSimulations
```

2. Install required packages:
```bash
pip install qiskit qiskit-nature qiskit-aer qiskit-algorithms matplotlib numpy
```

## Usage

1. Launch Jupyter Notebook:
```bash
jupyter notebook
```

2. Open `molecules_qiskit.ipynb`

3. Run cells sequentially to:
   - Define the H₂ molecule Hamiltonian
   - Perform Jordan-Wigner transformation
   - Set up the VQE algorithm
   - Calculate ground state energy
   - Visualize molecular orbitals

## Code Example

### Hamiltonian Definition
```python
h2_hamiltonian = FermionicOp(
    {
        "+_0 -_0": -1.252477,
        "+_1 -_1": -0.475934,
        # ... (full Hamiltonian terms)
        "+_1 +_3 -_3 -_1": 0.697397,
    },
    num_spin_orbitals=4,
)
```

### VQE Setup
```python
ansatz = TwoLocal(rotation_blocks='ry', entanglement_blocks='cz', reps=2)
optimizer = SPSA()
vqe = VQE(Estimator(), ansatz, optimizer)
result = vqe.compute_minimum_eigenvalue(qubit_op)
```

## Result for H2

- Calculated ground state energy: `-2.507280 Hartree`
- Animated 3D visualization of molecular orbitals (saved as `h2_orbitals.gif`)

![H₂ Molecular Orbitals](h2_orbitals.gif)

## Dependencies

| Package         | Version  |
|-----------------|----------|
| Qiskit          | ≥0.44    |
| Qiskit Nature   | 0.7.2    |
| Qiskit Aer      | 0.16.1   |
| Matplotlib      | ≥3.5.0   |
| NumPy           | ≥1.17    |

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## References

1. Qiskit Nature Documentation: [https://qiskit.org/documentation/nature/](https://qiskit.org/documentation/nature/)
2. Jordan-Wigner Transformation: [Qiskit Textbook](https://learn.qiskit.org/course/algorithm-design/molecules)
3. VQE Algorithm: [Qiskit VQE Guide](https://qiskit.org/documentation/stubs/qiskit.algorithms.VQE.html)

---

**Note:** Some Qiskit components used in this notebook may show deprecation warnings. For the latest implementations, check the [Qiskit Nature Migration Guide](https://qiskit.org/documentation/nature/migration_guide.html).
```

This README provides:
1. Clear installation and usage instructions
2. Code examples for key components
3. Visualization of results
4. Dependency requirements
5. License and reference information
6. Colab integration badge

You may want to:
1. Add a `LICENSE` file
2. Update the repository URL in the installation instructions
3. Adjust the license type if needed
4. Add additional badges for build status or documentation
5. Include contribution guidelines in a separate CONTRIBUTING.md file
