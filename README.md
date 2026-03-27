# MR-OOD: Visualization & Reporting Suite
This repository contains the tools and Jupyter Notebooks used to generate data statistics and produce high-quality visualizations for the MR Out-of-Distribution (OOD) anomaly detection project.

## Features
- **Data Diagnostics**: Verify NIfTI consistency across different channel formats (1-channel vs. 2.5D).
- **Statistical Reporting**: Generate patient and slice distribution analysis for dataset versioning.
- **Preprocessing Pipeline**: Automated body-masking, 224x224 resizing, and anatomical cropping for standardized reporting.
- **Comparative Visualization**: High-resolution, 3-panel reporting of raw MRI, Ground Truth, and Model Predictions.

---

## File Overview

### Python Scripts
- **`visualize.py`**: A command-line tool designed to generate standardized 3-panel comparison plots. It automates anatomical alignment, 90° rotation, and lateral cropping to ensure focus on the relevant regions of interest.

### Jupyter Notebooks
- **`channel_test.ipynb`**: Diagnostic tool to verify NIfTI image consistency and distinguish between 2.5D and 1-channel data formats.
- **`dataset_stats.ipynb`**: Generates bar charts comparing patient and slice distributions across ID/OOD splits and dataset versions.
- **`mask_refinement.ipynb`**: Visualization of the mask refinement procedure and morphological operations.
- **`discussion_visualization.ipynb`**: Research notebook for testing Ground Truth masks against predictions from multiple anomaly detection models.

---

## Usage: Visualization Script

The `visualize.py` script is used to generate figures for the discussion section of the report. It produces a 1x3 grid for a specific slice or all slices containing anomalies.

### Command Example
```bash
python visualize.py \
  --mr_path /path_to_mr/1PA079/mr.nii.gz \
  --predicted_mask_path /path_to_prediciton/PA079.nii.gz \
  --ground_truth_path /path_to_ground_truth/PA079.nii.gz \
  --output_directory ./results_visualization \
  --model_name "RD4AD" \
  --saving_format png \
  --patient_slice 47
