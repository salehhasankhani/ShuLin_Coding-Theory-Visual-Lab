# Coding Theory Visual Lab

**A Visual and Computational Companion to _Error Control Coding_**

A chapter-by-chapter computational and visual exploration of channel coding and reliable digital communication, inspired by *Error Control Coding* by **Shu Lin and Daniel J. Costello Jr.**

The project turns core coding-theory concepts into executable Python experiments, mathematical demonstrations, simulations, and visualizations.

---

## Project Goals

The main goal is to connect:

**Theory → Mathematical Model → Python Implementation → Visualization → Simulation → Interpretation**

Instead of presenting coding theory only through equations, this project builds a visual laboratory for exploring concepts such as:

- Codewords and code spaces
- Hamming distance
- Encoding and decoding
- Error detection and correction
- Maximum-Likelihood (ML) and MAP decoding
- Binary symmetric and erasure channels
- BPSK and AWGN
- BER and \(E_b/N_0\)
- Coding gain
- Shannon limits
- Random and burst errors
- Interleaving
- Gilbert-Elliott channels
- FEC and ARQ
- The distinction between error control and cryptographic authentication

---

## Repository Structure

The repository is organized **chapter by chapter** so that each implementation can be connected directly to the corresponding material in the textbook.

```text
ShuLin_Coding-Theory-Visual-Lab/
│
├── README.md
├── requirements.txt
│
├── chapter_1/
│   ├── Visual_Lab_ch1.ipynb
│   └── Visual_Lab_ch1.py
│
├── chapter_2/
│   └── ...
│
├── chapter_3/
│   └── ...
│
└── ...
```

At the current stage, **Chapter 1** is implemented. Additional chapters will be added progressively.

Each completed chapter is intended to contain:

- A Jupyter Notebook (`.ipynb`)
- A Python source file (`.py`)
- Visual demonstrations
- Numerical experiments
- Reproducible simulations

---

# Chapter 1 — Fundamentals of Error Control Coding

Chapter 1 establishes the basic concepts used throughout the rest of the project.

### Files

**Jupyter Notebook**

```text
chapter_1/Visual_Lab_ch1.ipynb
```

**Python source**

```text
chapter_1/Visual_Lab_ch1.py
```

The notebook is developed for a standard **Jupyter Notebook** environment. It is not dependent on Google Colab or GPU hardware for the core experiments.

---

## What Chapter 1 Demonstrates

### 1. Digital Communication System

The notebook begins with a visual representation of a digital communication system:

```text
Information
     ↓
  Encoder
     ↓
   Channel
     ↓
  Decoder
     ↓
Recovered Information
```

The system-level diagram is connected to the mathematical representation of messages, codewords, channel errors, and decoded information.

---

### 2. Binary Repetition Code

The central example is the binary repetition code

\[
\mathcal{C}=\{000,111\}
\]

with

\[
(n,k)=(3,1)
\]

and code rate

\[
R=\frac{k}{n}=\frac{1}{3}.
\]

This intentionally simple code is used to develop an intuitive understanding of redundancy, distance, detection, correction, and decoding.

---

### 3. Code Space and Hamming Distance

The binary code space is visualized to demonstrate:

- Binary vectors
- Codewords
- Hamming distance
- Nearest-neighbor decoding
- Decoding regions
- Minimum distance
- Error detection
- Error correction

For the repetition code,

\[
d_{\min}=3.
\]

Therefore, the guaranteed error-correction capability is

\[
t=\left\lfloor\frac{d_{\min}-1}{2}\right\rfloor=1.
\]

Thus, the code can guarantee correction of one bit error and detection of up to two bit errors.

---

### 4. Generator and Parity-Check Matrices

The notebook introduces the matrix representation of binary linear codes, including:

- Generator matrices
- Parity-check matrices
- Encoding
- Parity checks
- Syndromes
- Error detection

These concepts provide the algebraic foundation for more advanced block codes in later chapters.

---

### 5. Maximum-Likelihood and MAP Decoding

Two important statistical decoding principles are demonstrated:

- **Maximum-Likelihood (ML) decoding**
- **Maximum a posteriori (MAP) decoding**

The experiments illustrate how decoding decisions depend on the received vector, channel model, crossover/error probability, and—under MAP decoding—the prior probability of the transmitted message.

---

### 6. Binary Symmetric Channel

The **Binary Symmetric Channel (BSC)** is modeled explicitly.

The notebook studies the effect of the crossover probability

\[
p
\]

on communication and decoding performance.

For the `(3,1)` repetition code under ML decoding, the exact decoded bit-error probability is

\[
P_b=3p^2-2p^3.
\]

The analytical result is also checked using Monte Carlo simulation.

---

### 7. Binary Erasure Channel

The **Binary Erasure Channel (BEC)** is introduced to distinguish between:

- an incorrect received bit, and
- an erased or unavailable bit.

Numerical experiments illustrate how erasures affect reliable communication.

---

### 8. BPSK and AWGN

The discrete channel models are extended to a continuous-amplitude communication setting.

The notebook visualizes:

- BPSK constellation points
- Transmitted symbols
- AWGN
- Noisy received signals
- Decision boundaries
- Time-domain waveforms

The BPSK mapping is

\[
0\rightarrow+\sqrt{E_s},
\qquad
1\rightarrow-\sqrt{E_s}.
\]

For a real AWGN channel, the noise variance per dimension is

\[
\frac{N_0}{2}.
\]

---

### 9. BER versus \(E_b/N_0\)

The notebook compares BER performance as a function of

\[
\frac{E_b}{N_0}.
\]

The comparison includes:

- Uncoded BPSK
- Hard-decision repetition decoding
- Soft maximum-likelihood decoding

Energy normalization accounts explicitly for code rate:

\[
E_s=R E_b.
\]

For the `(3,1)` repetition code, soft ML decoding at equal information-bit \(E_b/N_0\) does not produce an asymptotic coding gain over uncoded BPSK.

This does **not** mean that repetition coding is useless. It illustrates the important distinction between:

- redundancy,
- finite-BER performance,
- and asymptotic coding gain.

---

### 10. BPSK-Constrained Shannon Limit

The notebook numerically evaluates the BPSK-constrained Shannon threshold.

Numerical integration is used to estimate the \(E_b/N_0\) threshold associated with a given code rate.

As a sanity check, the implementation reproduces approximately:

\[
0.187\ \mathrm{dB}
\]

for

\[
R=\frac{1}{2}.
\]

For the repetition-code rate

\[
R=\frac{1}{3},
\]

the corresponding threshold is approximately:

\[
-0.495\ \mathrm{dB}.
\]

---

### 11. Finite-BER and Coding-Gain Analysis

The notebook distinguishes between:

- asymptotic coding gain,
- finite-BER operating-point performance,
- distance-based theoretical estimates.

This distinction is important for short codes, where useful finite-BER behavior should not automatically be interpreted as an asymptotic coding gain.

For the repetition code, an asymptotic hard-decision coding-gain estimate of approximately

\[
-3.01\ \mathrm{dB}
\]

is also shown.

---

### 12. Random and Burst Errors

The notebook investigates two different error patterns:

- Random errors
- Burst errors

The experiments demonstrate why the statistical structure of channel errors matters in error-control-system design.

---

### 13. Interleaving

An interleaving experiment demonstrates how rearranging the order of transmitted bits can transform a burst-error pattern into a more distributed error pattern.

This provides an intuitive computational explanation of why interleaving can improve the effectiveness of error-correcting codes on bursty channels.

---

### 14. Gilbert-Elliott Channel

A simple **Gilbert-Elliott channel** model is included to represent a channel whose error behavior changes between different states.

This provides a bridge between the memoryless BSC model and channels exhibiting:

- Error bursts
- Temporal correlation
- State-dependent error behavior

---

### 15. FEC versus ARQ

The notebook includes an idealized comparison between:

- **Forward Error Correction (FEC)**
- **Automatic Repeat reQuest (ARQ)**

The comparison focuses on communication goodput.

The ARQ model deliberately assumes:

- Perfect error detection
- No feedback overhead
- No feedback delay

Therefore, this experiment is intended as an educational model rather than a complete production-system performance analysis.

---

### 16. Error Control Coding Is Not Cryptographic Authentication

The final demonstration connects channel coding with security-aware system design.

The key distinction is:

> Error-control coding protects communication against channel errors; it does not provide cryptographic authentication.

An HMAC demonstration is included only to make this distinction concrete.

The demonstration key is temporary and must never be reused in a production security system.

---

# Chapter 1 Sanity Checks

The following values provide quick implementation checks:

| Quantity | Expected value |
|---|---:|
| Code type | Binary repetition code |
| Code parameters | `(3,1)` |
| Code rate | `1/3` |
| Minimum Hamming distance | `3` |
| Guaranteed correction capability | `1` bit |
| Guaranteed detection capability | `2` bits |
| BSC decoded error probability | \(3p^2-2p^3\) |
| BPSK-constrained Shannon threshold at \(R=1/2\) | approximately `0.187 dB` |
| BPSK-constrained Shannon threshold at \(R=1/3\) | approximately `-0.495 dB` |
| Asymptotic soft-decision coding gain | `0 dB` |
| Asymptotic hard-decision estimate | approximately `-3.01 dB` |

These values are intended as implementation sanity checks, not as universal performance guarantees.

---

# Running the Project

## Jupyter Notebook

The project is developed and tested as a standard **Jupyter Notebook** workflow.

Open:

```text
chapter_1/Visual_Lab_ch1.ipynb
```

Then execute the notebook from top to bottom.

The notebook contains:

- Explanatory text
- Mathematical equations
- Python implementations
- Visualizations
- Numerical experiments
- Simulation results

The main parameters are defined in the code so that experiments can be reproduced and modified without requiring interactive widgets.

---

## Python Source

The corresponding Python source file is:

```text
chapter_1/Visual_Lab_ch1.py
```

The `.py` file provides a script-based version of the notebook implementation and can be used to inspect, modify, or reproduce the experiments outside the notebook.

---

# Requirements

The core Chapter 1 implementation uses standard scientific Python libraries:

- NumPy
- pandas
- SciPy
- Matplotlib
- IPython

Dependencies are listed in:

```text
requirements.txt
```

Install them with:

```bash
pip install -r requirements.txt
```

No GPU is required for the core experiments.

No paid API, external dataset, or external internet service is required for the core simulations.

---

# Reproducibility

The project is designed with reproducibility in mind.

Where Monte Carlo simulation is used, random seeds are specified in the code where appropriate.

Analytical results are included alongside numerical simulations whenever possible so that simulation output can be compared against known theoretical behavior.

---

# Design Philosophy

The project follows three main principles.

### 1. Mathematical concept → executable experiment

Important theoretical concepts are connected to executable Python implementations.

### 2. Equation → visualization

Where appropriate, mathematical relationships are accompanied by plots, diagrams, or numerical demonstrations.

### 3. Theory → simulation → interpretation

The workflow is:

```text
Theory
  ↓
Mathematical Model
  ↓
Python Implementation
  ↓
Visualization
  ↓
Numerical Experiment
  ↓
Interpretation
```

The purpose is not simply to generate figures, but to develop an intuitive understanding of the behavior behind the equations.

---

# Future Chapters

The repository is intentionally structured to grow with the textbook.

Future chapters will follow the same organization:

```text
chapter_2/
chapter_3/
chapter_4/
...
```

Each chapter will contain its own computational material rather than placing the entire project into one large notebook.

This makes the repository easier to:

- Navigate
- Study
- Maintain
- Reproduce
- Extend
- Relate to the corresponding textbook material

---

# Educational Scope

This repository is an educational and research-oriented computational laboratory.

The simulations are intended to demonstrate fundamental principles of error-control coding and digital communication.

They should not be interpreted as:

- Production-ready communication protocols
- Optimized channel-code implementations
- Complete physical-layer models
- Production security implementations

The repetition code in Chapter 1 is intentionally simple. Later chapters can introduce more advanced error-control techniques, including:

- Hamming codes
- BCH codes
- Reed-Solomon codes
- Convolutional codes
- Turbo codes
- LDPC codes
- Other modern error-control codes

---

# Reference

The main textbook motivating this project is:

**Shu Lin and Daniel J. Costello Jr., _Error Control Coding_.**

This repository is intended as a computational companion for studying and visualizing the concepts introduced in the textbook.

---

## Author

**Saleh Hasankhani**

GitHub: [@salehhasankhani](https://github.com/salehhasankhani)

---

## License

This repository is intended for educational and research use.

Please respect the copyright of the referenced textbook and any third-party material used as inspiration or reference.
