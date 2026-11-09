# Poly/ML Greybox Fuzzing (x86-64)

Greybox fuzzing of the [Poly/ML](https://www.polyml.org/) Standard ML compiler on x86-64, aimed at finding **crashes** and **miscompilation bugs**.

Poly/ML is the compiler that builds and runs the [Isabelle/HOL](https://isabelle.in.tum.de/) proof assistant, so a bug in its code generator can silently undermine the trust we place in machine-checked proofs. This project adapts existing Poly/ML compiler fuzzing tools into a coverage-guided (greybox) setup with a harness designed to surface those bugs.

> **Status:** early development — this repository currently contains project scaffolding only.

## Goals

- **Harness:** build a fuzzing harness that feeds generated Standard ML programs to Poly/ML and captures compiler and runtime behaviour.
- **Greybox transformation:** adapt existing Poly/ML fuzzing tools so that input generation is guided by coverage feedback from an instrumented compiler build.
- **Crash detection:** detect compiler crashes, assertion failures, hangs, and runtime faults in compiled code.
- **Miscompilation detection:** detect programs whose compiled behaviour differs from their expected behaviour (e.g. via differential testing across optimisation settings or reference outputs).
- **Triage:** minimise, deduplicate and document any bugs found.

## Target

|                     |              |
| ------------------- | ------------ |
| Compiler            | Poly/ML      |
| Architecture        | x86-64       |
| Language under test | Standard ML  |
| Downstream system   | Isabelle/HOL |

## Repository layout (planned)

```
.
├── harness/      # Fuzzing harness: runs Poly/ML on generated inputs, collects results
├── generators/   # Adapted program generators / mutators
├── oracles/      # Crash and miscompilation checks
├── scripts/      # Build, run and triage helpers
├── corpus/       # Seed Standard ML programs
├── results/      # Crashes, miscompilations and minimised test cases (not committed)
└── docs/         # Design notes, meeting slides, report material
```

## Getting started

Setup instructions will be added once the build pipeline is in place. Expected prerequisites:

- Linux on x86-64
- A C/C++ toolchain
- Poly/ML built from source (with coverage instrumentation for greybox fuzzing)
- A coverage-guided fuzzing engine (to be decided)

## Context

This is an individual BSc project at King's College London, _Proof Assistant Reliability and Testing_ (variant 7: x86).

Supervisor: Dr Karine Even-Mendoza · Co-supervisor: Dr Mohammad Mansour

