# Coding Theory Visual Lab

**From Reliable Communication to Security-Aware System Design**

A computational companion to Chapter 1 of *Error Control Coding* by Shu Lin and Daniel J. Costello Jr.

## What this project demonstrates

The central example is the binary repetition code

\[
\mathcal C=\{000,111\},\qquad (n,k)=(3,1),\qquad R=1/3.
\]

The notebook includes:

1. A digital communication system block diagram.
2. A 3D visualization of the binary code space and Hamming decoding regions.
3. Code rate / bandwidth expansion, generator and parity-check matrices, and syndrome-based error detection.
4. ML versus MAP decoding over a binary symmetric channel.
5. Exact BSC error probabilities and Monte Carlo verification.
6. Binary erasure channel analysis.
7. BPSK constellation and time-domain waveform visualizations.
8. BER vs. Eb/N0 for uncoded BPSK, hard-decision repetition decoding and soft-ML decoding.
9. A numerically evaluated BPSK-constrained Shannon limit.
10. Finite-BER and asymptotic coding-gain comparisons.
11. Random/burst error experiments and interleaving.
12. A simple Gilbert-Elliott channel model.
13. An idealized FEC vs. ARQ goodput comparison.
14. A security demonstration: why channel coding is not cryptographic authentication.
15. Optional interactive sliders for BSC and AWGN parameters.

## Run in Google Colab

1. Download `Coding_Theory_Visual_Lab_TESTED.ipynb` (the version with saved figures and outputs) or `Coding_Theory_Visual_Lab.ipynb` (clean version).
2. Open [Google Colab](https://colab.research.google.com/).
3. Select **File → Upload notebook** and upload the `.ipynb`.
4. Select **Runtime → Run all**.

No GPU, paid API, external dataset or internet download is needed for the core notebook. The core requirements are NumPy, pandas, SciPy, Matplotlib and IPython. Interactive sliders are optional and use ipywidgets.

## Important technical notes

- BPSK mapping: `0 -> +sqrt(Es)`, `1 -> -sqrt(Es)`.
- Real AWGN variance per symbol: `N0/2`.
- Energy normalization: `Es = R * Eb`.
- For this `(3,1)` repetition code, soft-ML BER equals uncoded BPSK BER when compared at equal `Eb/N0`, so its soft-decision coding gain is 0 dB.
- The BPSK-constrained Shannon threshold is computed numerically by Gauss-Hermite quadrature. The `R=1/2` result is checked against the approximately `0.188 dB` value in the textbook.
- The ARQ comparison is deliberately idealized: perfect packet-error detection and no feedback overhead or delay.
- HMAC is included only to distinguish cryptographic integrity from error-control coding. The demonstration key is temporary and must never be used in production.

## Expected sanity-check values

| Quantity | Expected value |
|---|---:|
| Code rate | 1/3 |
| Minimum Hamming distance | 3 |
| Guaranteed correction capability | 1 bit |
| Guaranteed detection capability | 2 bits |
| BSC decoded error probability | `3p^2 - 2p^3` |
| BPSK-constrained Shannon threshold at R=1/2 | about 0.187 dB |
| BPSK-constrained Shannon threshold at R=1/3 | about -0.495 dB |
| Asymptotic soft-decision coding gain | 0 dB |
| Asymptotic hard-decision coding-gain estimate | about -3.01 dB |

The notebook also reports exact finite-BER gains for this short repetition code; those practical operating-point values should not be conflated with the distance-based asymptotic estimate.

## Scope

This is an educational simulation, not a production communication protocol or security implementation. The repetition code is intentionally simple and inefficient. More advanced codes (Hamming, BCH, Reed-Solomon, convolutional, Turbo and LDPC) are natural extensions for later chapters.
