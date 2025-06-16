# README: Infiltration Analysis & QC Image Generation

This repository contains two main MATLAB script sections (in a single `.m` file) for histological image processing:

1. **Infiltration Analysis** – quantify infiltration versus lung tissue areas from segmented TIFF images.  
2. **QC Image Generation** – create overlay and background-removed QC images using raw RGB histology and corresponding segmentation masks.

---

## Script Overview

The script is divided into two code sections (demarcated by `%%`):

### Section 1: Infiltration Analysis

**Purpose:**  
- Iterate through a folder of segmentation images (greyscale TIFFs where pixel labels are: `1=infiltrate`, `2=lung`, `3=background`).  
- Compute:
  - **Infiltrate-to-lung ratio** = (number of infiltrate pixels) / (number of lung pixels)  
  - **Total lung area** = infiltrate pixels + lung pixels  
  - **Infiltrate percent of lung** = (infiltrate pixels / total lung area) × 100  
- Store results in a cell array `output`, with one row per image:  
  ```matlab
  { filename, infilt2lungRatio, totalLungArea, infiltPercOfLung }
