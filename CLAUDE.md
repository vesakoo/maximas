# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A small Maxima (computer algebra system) library for symbolic quantum-computing calculations. The entire codebase is a single file, `gates.mac`, that defines quantum states and gates as global Maxima matrices. `ReadMe.md` documents the public names.

## Running

There is no build, lint, or test suite. Maxima is installed via Homebrew (`/opt/homebrew/bin/maxima`). To check that the file loads and to evaluate expressions non-interactively:

```sh
maxima --very-quiet --batch-string='load("gates.mac")$ BELL00; CX . kronecker_product(H,I) . ket00;'
```

Interactively: `maxima`, then `load("gates.mac");`.

## Conventions in gates.mac

- Everything is a top-level global binding (`name: matrix(...)`). Loading the file overwrites any existing bindings with the same names. Single-letter names such as `I`, `X`, `H`, `S`, `T`, `M`, `R` and `B` are among them.
- States are column matrices (kets) and row matrices (bras). Apply gates with Maxima's non-commutative product `.` and build multi-qubit operators with `kronecker_product(A,B)`.
- Qubit ordering is big-endian: `ket01` = |0⟩⊗|1⟩. In `CX` the first (left/top) qubit is the control, in `XC` the second qubit is the control, and `AX` flips the target when the control is |0⟩.
- Two-qubit helpers follow the pattern `XoI` = X⊗I and `IoX` = I⊗X (likewise for `Z` and `H`).
- Aliases: `B` = `BELL`, `B00`…`B11` = `BELL00`…`BELL11`. `CCX` and `TOFFOLI` are the same matrix.
- Accessor functions: `pauli_x()`, `pauli_y()`, `pauli_z()`, `hadamard()`, and `cnot()` / `c_not()`. These return the global matrices.
- Complex and symbolic constants use Maxima syntax: `%i`, `%pi`, `%theta` (the free parameter of `R`).
- `BELLxy = BELL . ketxy` follows the Nielsen & Chuang β_xy convention: `BELL01` is |Ψ+⟩ and `BELL10` is |Φ−⟩.
- `M` is the Z observable (same matrix as `Z`), not a measurement operation.

When you add a gate or state, update both the header comment in `gates.mac` and the lists in `ReadMe.md`, which mirror each other. Check matrix identities with Maxima rather than by hand. For example, `is(ratsimp(rectform(SX.SX)) = X);` confirms a gate, and `ratsimp(rectform(G . conjugate(transpose(G))))` should give the identity for any gate `G`.
