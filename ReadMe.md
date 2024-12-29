# Gates.mac

This document provides an overview of the `gates.mac` file, which is part of the Quantum Maximas project.

## Table of Contents
- [Introduction](#introduction)
- [Installation](#installation)
- [Usage](#usage)
- [Matrices] (#matrices)
- [Functions](#functions)
- [Examples](#examples)
- [Contributing](#contributing)
- [License](#license)

## Introduction
`gates.mac` is a script that defines various quantum gates and their operations. It is used in the Quantum Maximas project to simulate quantum computations.

## Installation
To use `gates.mac`, you need to have Maxima installed on your system. You can download and install Maxima from [here](http://maxima.sourceforge.net/download.html).

## Usage
To load and use the `gates.mac` file in Maxima, follow these steps:

1. Open Maxima.
2. Load the `gates.mac` file:
  ```maxima
  load("path/to/gates.mac");
  ```

## Matrices
 Quantum States:
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
 
  Quantum Gates:
  - `I`: Identity gate
  - `X`: Pauli-X (NOT) gate
  - `Y`: Pauli-Y gate
  - `Z`: Pauli-Z gate
  - `H`: Hadamard gate
  - `S`: Phase gate
  - `SX`: Square root of X gate
  - `T`: T gate (π/4 gate)
  - `M`: Measurement gate (Z-basis)
  - `R`: Rotation gate (parameterized by θ)
  - `CZ`: Controlled-Z gate
  - `Ix4`: 4x4 Identity gate
  - `CX`: Controlled-X (CNOT) gate
  - `AX`: Anti controlled-X gate
  - `XC`: Another form of controlled-X gate (q[0]=X,q[1]=C)
  - `SWAP`: SWAP gate
  - `CCX`: Toffoli (CCNOT) gate
  - `FREDKIN`: Fredkin (CSWAP) gate
  - `TOFFOLI`: Toffoli (CCNOT) gate
  Bell States:
  - `BELL`: Bell state generation circuit
  - `BELL00`: Bell state |Φ+⟩
  - `BELL01`: Bell state |Φ−⟩
   - `BELL10`: Bell state |Ψ+⟩
   - `BELL11`: Bell state |Ψ−⟩

## Functions
The `gates.mac` file includes the following functions:

- `hadamard()`: Defines the Hadamard gate.
- `pauli_x()`: Defines the Pauli-X gate.
- `pauli_y()`: Defines the Pauli-Y gate.
- `pauli_z()`: Defines the Pauli-Z gate.
- `cnot()`: Defines the CNOT gate.

## Examples
Here are some examples of how to use the functions in `gates.mac`:

```maxima
/* Load the gates.mac file */
load("path/to/gates.mac");

/* Create a Hadamard gate */
H : hadamard();

/* Create a Pauli-X gate */
X : pauli_x();

/* Create a CNOT gate */
CNOT : cnot();
```

## Contributing
Contributions are welcome! Please read the [contributing guidelines](CONTRIBUTING.md) for more information.

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.