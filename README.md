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


## How to Run

1. Open the script in MATLAB.
2. Update the path variables at the top:
   ```matlab
   objDir    = '.../Images/Segmented2';
   imageFile = '.../Images/SF2253.tif';
   objFile   = '.../Images/ObjectSegm3/SF2253_Simple Segmentation.tif';
   ```
3. Run the script.
   - **Section 1:** Review the `output` cell array for infiltration metrics.
   - **Section 2:** Locate `original.png`, `image1.png`, `image2.png`, and `image3.png` in the working directory.

---

## Requirements

- MATLAB R2022b or newer
- Image Processing Toolbox (for `imread`, `imwrite`)
- Computer Vision Toolbox (for `insertObjectMask`)
- [Optional] Bio-Formats (`bfmatlab`) for non-standard TIFFs

---

## Notes & Tips

- To preserve intermediate variables, comment out the `clear` statements at the end of Section 1.
- Batch QC generation by looping over filenames in Section 2.
- Adjust `Opacity` and `LineWidth` in `insertObjectMask` for finer visualization control.

---

## Author

Anthony Tao
