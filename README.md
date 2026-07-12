# Workflow Overview

This project is run in the following order.

## 1. Prepare data in Python

Run Python notebooks **1** and **2** first.

These notebooks prepare the transcriptomics, proteomics, phenotype, and other input data needed to construct the individual metabolic models.

## 2. Build and process models in MATLAB

Run the MATLAB scripts in this order:

1. **ftINIT**
   - Builds the individual-specific metabolic models.

2. **E-Flux**
   - Applies expression-based flux bounds to the models.

3. **Dietary constraints**
   - Applies dietary and physiological exchange constraints.

4. **Flux sampling**
   - Samples the feasible flux space for each individual model.

5. **Reaction presence**
   - Identifies which reactions are present in each individual model and highlights reactions that are unique to specific models.

6. **Convert MATLAB outputs to CSV**
   - Converts the required `.mat` files and sampled flux distributions into CSV files for downstream Python analysis.

## 3. Analyse results in Python

After all MATLAB steps are complete, run Python notebooks **3 through 12** in numerical order.

These notebooks analyse the presence/absence matrix, sampled flux distributions, machine-learning predictions, pathway results, individuality metrics, and related manuscript outputs.

## Execution order

```text
Python notebooks 1–2
        ↓
MATLAB: ftINIT
        ↓
MATLAB: E-Flux
        ↓
MATLAB: dietary constraints
        ↓
MATLAB: flux sampling
        ↓
MATLAB: presence/absence matrix
        ↓
MATLAB: convert .mat outputs to CSV
        ↓
Python notebooks 3–12
```

Run all scripts and notebooks from the expected project folders so that the relative paths resolve correctly.
