# Coding Theory Visual Lab

**A Visual and Computational Companion to Error Control Coding**

This project is a chapter-by-chapter computational companion to *Error Control Coding* by **Shu Lin and Daniel J. Costello Jr.**

The main goal of the project is to turn the mathematical concepts of coding theory into **executable Python experiments, visualizations, simulations, and numerical demonstrations**.

Instead of treating coding theory only as a collection of equations, this project provides a visual laboratory in which concepts such as codewords, Hamming distance, decoding, channel errors, BER, coding gain, and channel capacity can be explored computationally.

---

## Project Structure

The project is organized **chapter by chapter** so that the code and visualizations can be directly connected to the corresponding material in the textbook.

```text
Visual_Lab_ch1_GitHub_Package/
│
├── README.md
├── README_FA.md
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

Each chapter is intended to contain its own:

- Jupyter Notebook (`.ipynb`)
- Python source code (`.py`)
- Visual demonstrations
- Numerical experiments
- Simulation results

The current repository begins with **Chapter 1**, with additional chapters to be added progressively.

---

# Chapter 1 — Fundamentals of Error Control Coding

The first chapter provides the foundation for the rest of the project.

The Chapter 1 notebook is:

```text
chapter_1/Visual_Lab_ch1.ipynb
```

The corresponding Python source file is:

```text
chapter_1/Visual_Lab_ch1.py
```

The notebook is designed to be executed in a standard **Jupyter Notebook** environment.

---

## What Chapter 1 Demonstrates

### 1. Digital Communication System

A complete digital communication chain is introduced visually:

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

The notebook connects this system-level view to the mathematical representation of messages, codewords, and channel errors.

---

### 2. Binary Repetition Code

The central example in Chapter 1 is the binary repetition code:

\[
\mathcal{C}=\{000,111\}
\]

with parameters

\[
(n,k)=(3,1)
\]

and code rate

\[
R=\frac{k}{n}=\frac{1}{3}.
\]

The notebook uses this simple code to build an intuitive understanding of redundancy and error correction.

---

### 3. Code Space and Hamming Distance

The binary codewords are visualized geometrically to illustrate:

- binary vectors,
- Hamming distance,
- nearest-neighbor decoding,
- decoding regions,
- minimum distance,
- error detection,
- error correction.

For the repetition code,

\[
d_{\min}=3.
\]

Therefore:

\[
t=\left\lfloor\frac{d_{\min}-1}{2}\right\rfloor=1
\]

meaning that the code can **guarantee correction of one bit error**.

It can also **guarantee detection of up to two bit errors**.

---

### 4. Generator and Parity-Check Matrices

The notebook introduces the matrix representation of binary linear codes and demonstrates:

- generator matrices,
- parity-check matrices,
- encoding,
- parity checks,
- syndromes,
- error detection.

These concepts provide the algebraic foundation for more advanced block codes in later chapters.

---

### 5. Maximum-Likelihood and MAP Decoding

The notebook compares two important statistical decoding principles:

- Maximum-Likelihood (ML) decoding
- Maximum a posteriori (MAP) decoding

The goal is to show how the decoder's decision can depend on:

- the received vector,
- the channel model,
- the error probability,
- and, for MAP decoding, the prior probability of the transmitted message.

---

### 6. Binary Symmetric Channel

The Binary Symmetric Channel (BSC) is modeled explicitly.

The notebook studies how the crossover probability

\[
p
\]

affects decoding performance.

For the `(3,1)` repetition code with ML decoding, the exact decoded bit-error probability is:

\[
P_b=3p^2-2p^3.
\]

This result is also verified numerically using Monte Carlo simulation.

---

### 7. Binary Erasure Channel

The Binary Erasure Channel (BEC) is introduced to distinguish between:

- an incorrect received bit,
- and a missing/erased bit.

The notebook provides numerical experiments illustrating the effect of erasures on reliable communication.

---

### 8. BPSK and AWGN

The binary communication model is extended from discrete channels to a continuous-time/continuous-amplitude setting.

The notebook visualizes:

- BPSK constellation points,
- transmitted symbols,
- AWGN,
- noisy received signals,
- decision boundaries,
- time-domain waveforms.

The BPSK mapping used throughout the notebook is:

\[
0\rightarrow+\sqrt{E_s},
\qquad
1\rightarrow-\sqrt{E_s}.
\]

For a real AWGN channel, the noise variance per dimension is:

\[
\frac{N_0}{2}.
\]

---

### 9. BER versus \(E_b/N_0\)

The notebook compares bit-error-rate performance as a function of:

\[
\frac{E_b}{N_0}.
\]

The comparison includes:

- uncoded BPSK,
- hard-decision repetition decoding,
- soft maximum-likelihood decoding.

The energy normalization explicitly accounts for the code rate:

\[
E_s=R E_b.
\]

For the `(3,1)` repetition code, soft ML decoding at equal information-bit \(E_b/N_0\) does not provide an asymptotic coding gain over uncoded BPSK.

This is an important distinction between **redundancy** and **coding gain**.

---

### 10. Shannon Limit

The notebook numerically evaluates the BPSK-constrained Shannon limit.

The calculation uses numerical integration to estimate the \(E_b/N_0\) threshold required for reliable communication at a given code rate.

As a sanity check, the implementation reproduces the approximately:

\[
0.187\text{ dB}
\]

threshold for

\[
R=\frac12.
\]

For the repetition-code rate

\[
R=\frac13,
\]

the corresponding BPSK-constrained threshold is approximately:

\[
-0.495\text{ dB}.
\]

---

### 11. Finite-BER and Coding-Gain Analysis

The notebook distinguishes between:

- asymptotic coding gain,
- finite-BER performance,
- distance-based theoretical estimates.

This is important because a short code can show useful performance improvements at a particular operating point even when its asymptotic coding gain is zero.

For the repetition code, the notebook also provides an asymptotic hard-decision coding-gain estimate of approximately:

\[
-3.01\text{ dB}.
\]

The numerical finite-BER results are presented separately so that they are not confused with asymptotic theoretical quantities.

---

### 12. Random and Burst Errors

The notebook explores two qualitatively different error patterns:

- random errors,
- burst errors.

This demonstrates why the statistical structure of channel errors matters when designing an error-control system.

---

### 13. Interleaving

An interleaving experiment demonstrates how rearranging transmitted bits can transform burst errors into a pattern that is easier for an error-correcting code to handle.

The basic concept is illustrated computationally rather than treated only as a theoretical definition.

---

### 14. Gilbert-Elliott Channel

A simple Gilbert-Elliott channel model is included to represent a channel whose behavior changes between different states.

This provides a bridge between the simple memoryless BSC model and more realistic channels containing error bursts and temporal correlation.

---

### 15. FEC versus ARQ

The notebook includes an idealized comparison between:

- Forward Error Correction (FEC)
- Automatic Repeat reQuest (ARQ)

The comparison focuses on the resulting communication goodput.

The ARQ model is intentionally simplified and assumes:

- perfect error detection,
- no feedback overhead,
- no feedback delay.

Therefore, the result should be interpreted as an educational model rather than a production-system performance estimate.

---

### 16. Coding Is Not Cryptographic Authentication

The final demonstration connects coding theory to security-aware system design.

The notebook illustrates an important distinction:

> Error-control coding protects communication against channel errors; it does not provide cryptographic authentication.

An HMAC demonstration is included only to illustrate this distinction.

The example key is temporary and must **never** be reused in a production security system.

---

# Chapter 1 Sanity Checks

The following values provide quick checks that the main implementation is behaving correctly.

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

These values are intended as implementation sanity checks rather than universal performance guarantees.

---

# Running the Project

## Jupyter Notebook

The project is developed for a standard **Jupyter Notebook** environment.

Open:

```text
chapter_1/Visual_Lab_ch1.ipynb
```

and execute the notebook from top to bottom.

The notebook contains the visualizations, numerical experiments, and explanations in an executable format.

---

## Python Script

The corresponding Python source is also provided:

```text
chapter_1/Visual_Lab_ch1.py
```

This allows the experiments to be inspected, reused, modified, or executed outside the notebook environment.

---

# Requirements

The core notebook uses standard scientific Python libraries:

- NumPy
- pandas
- SciPy
- Matplotlib
- IPython

The required packages are listed in:

```text
requirements.txt
```

Install them with:

```bash
pip install -r requirements.txt
```

No GPU is required for the core Chapter 1 experiments.

No paid API, external dataset, or external internet service is required for the core simulations.

---

# Design Philosophy

This project follows three principles:

### 1. Mathematical concept → executable experiment

Each important concept is connected to a piece of executable code.

### 2. Equation → visualization

Where possible, equations are accompanied by plots, diagrams, or numerical demonstrations.

### 3. Theory → simulation → interpretation

The notebooks are structured so that the reader can move from:

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

The purpose is not simply to generate plots, but to develop an intuitive understanding of why the equations behave the way they do.

---

# Future Chapters

The repository is intentionally organized to grow with the textbook.

Future chapters can be added using the same structure:

```text
chapter_2/
chapter_3/
chapter_4/
...
```

Each chapter will contain its own computational material rather than placing the entire project into one large notebook.

This makes the repository easier to:

- navigate,
- study,
- maintain,
- reproduce,
- extend,
- and connect to the corresponding textbook chapters.

---

# Educational Scope

This repository is an educational and research-oriented computational laboratory.

The simulations are designed to demonstrate fundamental principles of error-control coding and digital communication.

They should not be interpreted as production-ready communication protocols, optimized channel codes, or security implementations.

The repetition code used in Chapter 1 is intentionally simple. More advanced coding techniques can be introduced in subsequent chapters, including:

- Hamming codes,
- BCH codes,
- Reed-Solomon codes,
- convolutional codes,
- Turbo codes,
- LDPC codes,
- and other modern error-control techniques.

---

# Citation

If you use this project for academic work, teaching, or research, please cite the underlying textbook:

**Shu Lin and Daniel J. Costello Jr., *Error Control Coding*.**

This repository is intended as a computational companion for studying the concepts presented in the textbook.
