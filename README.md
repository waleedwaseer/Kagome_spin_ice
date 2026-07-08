# Engineering Nonlinear Magnon Scattering in Artificial Spin Ice via Vertex Dipolar Control

This repository contains the MuMax3 simulation code and post-processing scripts used to study nonlinear magnon scattering in kagome artificial spin ice (ASI), with a focus on how nano-island geometry — width, leg symmetry, and edge curvature — controls harmonic and subharmonic generation under strong microwave drive.

> **Note:** The associated manuscript is currently under review. This repository will be updated with the full citation and DOI once the paper is published.

## Overview

Artificial spin ice is a two-dimensional lattice of interacting nanomagnets that provides a reconfigurable platform for magnonics. The commonly used geometric control parameters (island length, width, aspect ratio) simultaneously change the island footprint, inter-island dipolar spacing, and shape anisotropy, which makes it hard to tune the nonlinear response independently of the linear spectrum and lattice density.

This project uses micromagnetic simulations of kagome ASI under strong microwave drive to explore geometric routes for controlling nonlinear magnon scattering, in particular:

- **Width scaling:** Wider nano-islands increase dipolar interaction volume and strengthen the nonlinear spin-wave response, but also shift the linear eigenfrequencies and footprint.
- **Leg asymmetry:** Elongating one leg of the vertex creates imbalanced dipolar fields that suppress coherent dynamics and reduce harmonic content.
- **Edge curvature (dumbbell tips):** Rounding the island tips concentrates demagnetizing and exchange fields near the island ends, driving a transition from integer-harmonic-only spectra (sharp tips) to subharmonic-rich spectra — all without changing the island footprint or inter-element spacing.
- **Field-angle dependence:** The angular dependence of the second-harmonic amplitude inverts between sharp and dumbbell geometries, giving an experimentally accessible signature accessible to broadband FMR measurements.

The central result is that **tip curvature acts as a footprint-preserving design knob** for engineering nonlinear magnon scattering in ASI.

## Requirements

- [MuMax3](https://mumax.github.io/) (GPU-accelerated micromagnetic simulator)
- A CUDA-capable NVIDIA GPU
- Python 3.x for post-processing (numpy, scipy, matplotlib) for FFT spectra, field maps, and figure generation

## Simulation Setup

The system is a kagome ASI array of elongated Permalloy nano-islands (rounded rectangles / stretched ovals). The geometry is systematically varied across island width, leg length, and tip edge radius.

Default material and simulation parameters (Permalloy, unless otherwise stated):

| Parameter | Symbol | Value |
|-----------|--------|-------|
| Saturation magnetization | Ms | 800 kA/m |
| Exchange constant | A | 13 pJ/m |
| Gilbert damping | alpha | 0.01 |
| Cell size | — | 2.5 x 2.5 x 1 nm^3 |
| Sample size | — | 1250 x 1250 x 15 nm^3 |
| Island width range | w | 20–110 nm |
| Island length range | l | 260–310 nm |
| Thickness | — | 15 nm (constant) |

## Workflow

1. **Ground-state relaxation** — Relax each geometry from an initial magnetization (m = (1, 0, 0)) with no external bias; verify macrospin behavior via hysteresis loops.
2. **Resonance spectrum** — Apply a sinc-pulse excitation to extract the spin-wave resonance spectrum and identify edge and bulk modes.
3. **Nonlinear driving** — Apply single-frequency sinusoidal microwave fields to study integer harmonics and subharmonics as a function of geometry and drive amplitude.
4. **Parametric excitation** — Drive at f = 2f_X to probe the subharmonic (parametric / Suhl-instability) response of the target mode X.
5. **Edge-curvature study** — Compare sharp vs. dumbbell tips, mapping the curvature–drive parameter space and quantifying demagnetization/exchange energy changes.
6. **Field-angle dependence** — Vary the applied-field orientation to map the angular signature of the second harmonic and subharmonic branches.
7. **Post-processing** — Compute FFT spectra, field-frequency maps, angle-frequency maps, and synthetic MFM images.

## Repository Contents

- Scripts for building kagome ASI geometries (width, leg-asymmetry, and dumbbell-tip variants)
- Ground-state relaxation and hysteresis-loop drivers
- Microwave excitation drivers for resonance spectra, nonlinear scattering, and parametric pumping
- Post-processing scripts for FFT / spectral analysis and field-map generation

Please refer to the individual scripts for detailed, per-geometry parameters.

## Code Availability

The codes for kagome ASI generation and microwave excitation are available in this repository:
https://github.com/waleedwaseer/Kagome_spin_ice

## Citation

A citation will be added here upon publication. The manuscript is currently under review.

## Acknowledgments

This work was supported by the National Key R&D Program of China (Grant No. 2025YFA1411302), the National Natural Science Foundation of China (Grant Nos. 12374103 and 12434003), and the Sichuan Science and Technology Program (No. 2025NSFJQ0045).

## Contact

For questions regarding the code or the study, please open an issue in this repository or contact the corresponding author.
