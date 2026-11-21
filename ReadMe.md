# Gates.mac

This document provides an overview of the `gates.mac` file, which is part of the Quantum Maximas project.

## Table of Contents
- [Introduction](#introduction)
- [Installation](#installation)
- [Usage](#usage)
- [Matrices](#matrices)
- [Functions](#functions)
- [Examples](#examples)
- [Contributing](#contributing)
- [License](#license)

## Introduction
`gates.mac` is a script that defines various quantum gates and their operations. It is used in the Quantum Maximas project to simulate quantum computations.

## Installation
To use `gates.mac`, you need to have Maxima installed on your system. You can download and install Maxima from [here](https://maxima.sourceforge.io/download.html).

## Usage
To load and use the `gates.mac` file in Maxima, follow these steps:

1. Open Maxima.
2. Load the `gates.mac` file:
   ```maxima
   load("path/to/gates.mac");
   ```

States are column matrices (kets) and row matrices (bras). Apply a gate with Maxima's matrix product `.` and build multi-qubit operators with `kronecker_product`. Qubits are ordered left to right, so `ket01` is |0⟩⊗|1⟩ and q[0] is the leftmost qubit.

## Matrices

### Quantum States
- `ket0`: |0⟩ state vector
- `ket1`: |1⟩ state vector
- `ket00`: |00⟩ state vector
- `ket01`: |01⟩ state vector
- `ket10`: |10⟩ state vector
- `ket11`: |11⟩ state vector
- `bra0`: ⟨0| state vector
- `bra1`: ⟨1| state vector
- `ketplus`: |+⟩ state vector (superposition state)
- `ketminus`: |−⟩ state vector (superposition state)
- `braplus`: ⟨+| state vector (superposition state)
- `braminus`: ⟨−| state vector (superposition state)

### Quantum Gates
- `I`: Identity gate
- `X`: Pauli-X (NOT) gate
- `Y`: Pauli-Y gate
- `Z`: Pauli-Z gate
- `H`: Hadamard gate
- `S`: Phase gate
- `SX`: Square root of X gate (`SX . SX = X`)
- `T`: T gate (π/8 gate)
- `M`: Z-basis measurement observable (same matrix as `Z`)
- `R`: Phase shift gate, parameterized by the symbol `%theta`
- `CZ`: Controlled-Z gate
- `Ix4`: 4x4 Identity gate
- `CX`: Controlled-X (CNOT) gate (q[0] = control, q[1] = target)
- `AX`: Anti-controlled-X gate (flips q[1] when q[0] = |0⟩)
- `XC`: Controlled-X with reversed roles (q[0] = target, q[1] = control)
- `SWAP`: SWAP gate
- `CCX`: Toffoli (CCNOT) gate
- `FREDKIN`: Fredkin (CSWAP) gate
- `TOFFOLI`: Toffoli (CCNOT) gate, same as `CCX`

Two-qubit single-gate operators:
- `XoI`, `IoX`: X⊗I and I⊗X
- `ZoI`, `IoZ`: Z⊗I and I⊗Z
- `HoI`, `IoH`: H⊗I and I⊗H

### Bell States
- `BELL` (alias `B`): Bell state generation circuit, `CX . (H⊗I)`
- `BELL00` (alias `B00`): |Φ+⟩ = (|00⟩ + |11⟩)/√2
- `BELL01` (alias `B01`): |Ψ+⟩ = (|01⟩ + |10⟩)/√2
- `BELL10` (alias `B10`): |Φ−⟩ = (|00⟩ − |11⟩)/√2
- `BELL11` (alias `B11`): |Ψ−⟩ = (|01⟩ − |10⟩)/√2

## Functions
The `gates.mac` file includes the following functions, which return the matching matrices:

- `hadamard()`: Returns the Hadamard gate `H`.
- `pauli_x()`: Returns the Pauli-X gate `X`.
- `pauli_y()`: Returns the Pauli-Y gate `Y`.
- `pauli_z()`: Returns the Pauli-Z gate `Z`.
- `cnot()` / `c_not()`: Returns the CNOT gate `CX`.

## Examples
Here are some examples of how to use the functions in `gates.mac`:

```maxima
/* Load the gates.mac file */
load("path/to/gates.mac");

/* Get the Hadamard, Pauli-X and CNOT gates */
Had : hadamard();
PX : pauli_x();
CNOT : cnot();

/* Put |0⟩ into superposition: gives |+⟩ */
H . ket0;

/* Prepare the Bell state |Φ+⟩ from |00⟩ */
CX . kronecker_product(H, I) . ket00;
```

## Contributing
Contributions are welcome! Please open an issue or a pull request.

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
