#  iPALM Data Processing and ROI Analysis

This repository contains a Jupyter Notebook for processing 3D iPALM (interferometric PhotoActivated Localization Microscopy) data, acquired on the [Janelia iPALM platform](https://www.aicjanelia.org/ipalm-techspecs). The script supports fluorescence channel separation, z-stack projection, gold bead-based correction, ROI selection, and quantitative analysis of high-resolution image data.

## 🔧 Features

- Loads multi-channel iPALM image stacks (TIFF format)
- ✨ Gold bead (GB) reference stack used for:
  - Mask generation
  - Zero-level z-correction
  - Stack cleanup
-  Separates fluorescence channels (e.g., Vinculin & Vimentin)
-  Interactive region of interest (ROI) selection using `PolygonSelector`
- Z-projection over specified depth range
- Local maxima detection and **Gaussian fitting** for intensity profile analysis
- CSV/TXT export of processed data and fitting results


## 📂 File Overview

- `iPALM_example_processing.ipynb`: The main notebook for loading, cleaning, processing, and analyzing iPALM datasets.

## ➕ Optional Post-Processing: Accumulated ROI Analysis

The repository also includes a second notebook, `iPaLM_accumalated_data.ipynb`, for visualizing and interpreting the output data from earlier single-cell or ROI-level processing.

### Features

- Loads summary `.txt` files from the main processing notebook
- Compares z-center shifts and Gaussian widths (σ) between channels
- Separates and visualizes one-peak vs. two-peak ROI results
- Supports grouped plotting using Seaborn for clearer trends

### Example Input Files

- `output_data.txt`: Contains `ROI_ind, z_center_ch1, sd_ch1, z_center_ch2, sd_ch2, ...`
- `output_data_2_peak.txt`: For ROIs where two peaks were fit
- `output_z_700nm.txt`: Full detailed export for downstream inspection

### Example Plots

- Z-center comparison between Vinculin and Vimentin
- Distributions of standard deviations (σ) per channel
- ROI classification by fit mode


