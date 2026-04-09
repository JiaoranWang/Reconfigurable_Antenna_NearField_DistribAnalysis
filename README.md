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

### Contents

| Type | File | Purpose |
|---|---|---|
| input file | `[000] E-XZ.aedtplt` | HFSS-exported electric-field data on the XZ cut-plane for mode `[000]` |
| input file | `[000] Mag_Jsurf.aedtplt` | HFSS-exported surface-current magnitude data for mode `[000]` |
| input file| `[000] Vec_Jsurf.aedtplt` | HFSS-exported surface-current vector data for mode `[000]` |

| Type | File | Purpose |
|---|---|---|
| Process code | `e_field_aedtplt_reconfiguration.py` | Script for processing `.aedtplt` data |
| Process code | `e_field_process.py` | Script for ROI-based E-field score calculation/plotting |
| Process code | `j_surface_aedtplt_reconfiguration.py` | Script for reading and processing surface-current magnitude and vector `.aedtplt` data |



The format of .aedtplt is list in ANSYS HFSS Exporting Field Plots, and data processing 
(https://ansyshelp.ansys.com/public/Views/Secured/Electronics/v242/en/Subsystems/HFSS/Content/ReportsandPostProc/ExportingFieldPlots.htm)





## Electrical Field Analysis Model

<img width="752" height="462" alt="image" src="https://github.com/user-attachments/assets/0f227068-d04f-4d70-9c8b-35664f8f0a14" />



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

The .py processing code structure is:

<img width="700" height="1400" alt="image" src="https://github.com/user-attachments/assets/18572d21-4d07-4f20-948c-dc7b4b55e4dd" />



## Current Distribution Analysis Model

The surface current analysis focuses on the local regions around PIN diodes for each reconfigurable mode.

Two **metrics** are extracted:

- **J_Pi**: average surface-current magnitude inside the PIN region
- **V_Pi**: average directional projection of the vector surface current onto a reference direction

These metrics are used to distinguish the different reconfigurable modes in terms of both local current concentration and current-flow tendency.

The .py processing code structure is following the algorithm:

<img width="746" height="842" alt="image" src="https://github.com/user-attachments/assets/95b676ae-f1d9-4555-af56-93516bb2556e" />

The calculated figure like: 

<img width="1193" height="536" alt="image" src="https://github.com/user-attachments/assets/807943b0-85c9-4b43-877e-2457faa1f892" />









