# Near-Field Coupling and Surface Current Distribution Analysis for Reconfigurable Antenna

This repository provides the analysis code used for the near-field coupling and surface current distribution evaluation of a reconfigurable antenna system. The code processes exported `.aedtplt` files from **Ansys HFSS** and implements two quantitative analysis procedures:

1. **Electrical Field Analysis Model (_ROI-based near-field evaluation_)**
  - Parse scalar and vector `.aedtplt` files exported from Ansys HFSS
  - Extract electric-field data inside a selected region of interest (ROI)
  - Compute:
    - peak electric field
    - mean electric field
    - standard deviation of electric field
    - weighted near-field score

2. **Current Distribution Analysis Model (_PIN diode-region current concentration and flow-direction evaluation_)**
  - Extract surface current magnitude and vector data near PIN diode regions
  - Compute:
      - current concentration
      - flow-direction index
  - Compare different reconfigurable modes quantitatively

These tools are developed to support the **electromagnetic interpretation** of radiation and coupling behavior under different reconfigurable modes: 
The electrical field (E-field) distributions of Tx–Rx antenna system with a homogeneous phantom and the
surface current distribution (J-surf) of the Rx antenna are evaluated.


## Electrical Field Analysis Model



## Analysis Overview

### 1. Near-Field Coupling Evaluation

The near-field analysis evaluates the electric-field distribution within a predefined ROI for each reconfigurable mode and cut-plane.

The following metrics are calculated:

- **E_peak**: maximum electric-field magnitude in the ROI
- **E_mean**: average electric-field magnitude in the ROI
- **E_std**: standard deviation of the electric-field magnitude in the ROI

These metrics are then normalized and combined into a weighted score:

- higher **E_peak** and **E_mean** are treated as beneficial
- lower **E_std** is treated as beneficial after reverse normalization

The final score is used to compare the near-field behavior of different modes.

### 2. Surface Current Distribution Evaluation

The surface current analysis focuses on the local regions around PIN diodes for each reconfigurable mode.

Two metrics are extracted:

- **J_Pi**: average surface-current magnitude inside the PIN region
- **V_Pi**: average directional projection of the vector surface current onto a reference direction

These metrics are used to distinguish the different reconfigurable modes in terms of both local current concentration and current-flow tendency.

## Input Files

The code expects `.aedtplt` files exported from **Ansys HFSS**.

Typical inputs include:

- scalar electric-field files
- scalar surface-current magnitude files
- vector surface-current files

## Required Inputs

Depending on the analysis, the user should define:

- reconfigurable mode index
- cut-plane index
- region of interest (ROI)
- PIN diode regions
- weighting factors for near-field scoring
- reference direction vector for current-flow evaluation

## Repository Structure

Example structure:

.
├── data/
│   ├── efield/
│   ├── mag_jsurf/
│   └── vec_jsurf/
├── scripts/
│   ├── nearfield_analysis.py
│   ├── current_analysis.py
│   └── utils.py
├── results/
│   ├── figures/
│   └── tables/
└── README.md

You may modify the folder structure depending on your project organization.

## Usage

### Near-field analysis

Run the near-field evaluation script to:

- parse scalar E-field `.aedtplt` files
- select data points inside the ROI
- compute `E_peak`, `E_mean`, and `E_std`
- normalize the extracted metrics
- calculate the overall near-field score

### Surface current analysis

Run the current analysis script to:

- parse scalar `Mag_Jsurf` and vector `Vec_Jsurf` `.aedtplt` files
- select data points inside each PIN region
- compute current concentration
- compute flow-direction index

## Output

Typical outputs include:

- extracted field/current metrics
- normalized scores
- comparison tables across modes
- scatter plots or bubble plots
- current-distribution summaries near PIN regions

## Example Applications

This code can be used for:

- reconfigurable antenna mode comparison
- near-field coupling evaluation
- surface current interpretation near switching elements
- electromagnetic analysis supporting antenna performance discussion

## Notes

- The code is intended for **post-processing** of HFSS-exported data.
- The `.aedtplt` export format may vary depending on HFSS settings and version.
- Users may need to adjust the file parser according to their export format.
- ROI and PIN-region definitions should match the coordinate system used in the HFSS model.
