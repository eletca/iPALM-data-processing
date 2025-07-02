#  iPALM Data processing and ROI analysis

This repository contains a Jupyter Notebook iPALM_example_processing.ipynb for processing 3D iPALM (interferometric PhotoActivated Localization Microscopy) data, acquired on the [Janelia iPALM platform](https://www.aicjanelia.org/ipalm-techspecs). The script supports fluorescence channel separation, z-stack projection, zero level gold bead-based correction, ROI selection, and quantitative analysis of high-resolution image data. Additionally, it includes the notebook iPALM_accumulated_data.ipynb, which allows visualization of the accumulated data (from multiple cells) produced by iPALM_example_processing.ipynb

## 🔧 Features

- Loads multi-channel iPALM image stacks (TIFF format)
-   Gold bead (GB) reference stack used for:
  - Mask generation
  - Zero-level z-correction
  - Stack cleanup
-  Separates fluorescence channels (e.g., Vinculin & Vimentin)
-  Interactive region of interest (ROI) selection using `PolygonSelector`
- Z-projection over specified depth range
- Local maxima detection and  Gaussian fitting for intensity profile analysis
- CSV/TXT export of processed data and fitting results

## 📂 File and code overview
- The input should be an ASCII file (as provided by the microscope), which may contain up to 49 columns. For further data processing, only the columns 'Unwrapped Z', 'X Position', 'Y Position', and 'Label Set' will be used.
- `iPALM_example_processing.ipynb`: The main notebook for loading, cleaning, processing, and analyzing iPALM datasets.
- This file contains both gold bead data used for axial channel alignment and biologically relevant data from stained structures.
- The code loads Z-position data from two imaging channels, fits a Gaussian to each dataset, and plots both unnormalized and normalized histograms. It saves the plots and extracts key parameters (amplitude, Z-center, and spread) from the fits for further analysis.
- After loading the data, axial zero-level correction is done using gold beads. A TIFF file (e.g., "Run1-647_561_c123_sum_X21_processed_overlay_IDL.tiff") is required to apply a mask to the dataset.
- Check the orientation of the mask — rotation or flipping may be needed (for example, image = cv2.flip(image, 0) can be used to flip vertically).

## ➕ Optional post-processing: accumulated ROI analysis

The repository also includes a second notebook, `iPaLM_accumalated_data.ipynb`, for visualizing and interpreting the output data from earlier single-cell or ROI-level processing.

### Features

- Loads summary `.txt` files from the main processing notebook
- Compares z-center shifts and Gaussian widths (σ) between channels
- Separates and visualizes one-peak vs. two-peak ROI results
- Supports grouped plotting using Seaborn for clearer trends


