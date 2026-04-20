# Image Processing Case Studies

This repository contains two **case studies** for the first part of the Image
Processing course:

1. `parking_case/` - **Parking lot monitoring**
2. `nuclei_case/` - **Nuclei segmentation**

Each case study must be implemented using **classical image processing only**:
no machine learning.

Students must design a **robust pipeline** based on the physics of the image,
filtering, histograms, thresholding, morphology, and segmentation algorithms
seen in the lectures and labs.

---

## 1. Software environment

You are strongly encouraged to use a **Python virtual environment**.

### 1.1. Create and activate a virtual environment

**Linux / macOS**:

```bash
python3 -m venv venv
source venv/bin/activate
```

**Windows (PowerShell)**:

```
python -m venv venv
venv\Scripts\Activate.ps1
```

### 1.2. Install dependencies

From the root of the repository (where "`requirements.txt`" is located):

```bash
pip install --upgrade pip
pip install -r requirements.txt
```

You should now be able to open Python and import the main libraries:

```python
import numpy as np
import skimage
import matplotlib
# etc.
```

---

## 2. Project structure and execution

Each case study has the following structure:

```
<case_name>/
|-- data/         # raw images (and masks when available)
|-- doc/          # final report
|-- results/      # masks, overlays, CSV metrics, etc.
|-- src/
    |-- eval_tools.py  # metrics
    |-- main.py        # entry point of your pipeline
    |-- preprocess.py  # global preprocessing
    |-- roi_utils.py   # ROI helpers (parking case only)	
    |-- segment.py     # segmentation of ROIs
    |-- viz_utils.py   # helper functions for visualization
```

### Running the pipeline (example)

From the root of the repo, after activating your virtual environment:

```bash
cd parking_case
python -m src.main --data-dir data/CNRPark-EXT --output-dir results
```

or for the nuclei case:

```bash
cd nuclei_case
python -m src.main --data-dir data/MoNuSeg --output-dir results
```

---

## 3. What you are expected to deliver

The pipeline currently does:

1. Recursively scans the "`data`" directory for images.
2. Applies:
   - `load_image()`
   - `preprocess_image()`
   - `segment_image()`
3. Saves:
   - binary masks ("`results/masks`")
   - overlays ("`results/overlays`")

You must implement:

1. A working pipeline (Python scripts in "`src/`").
2. A set of results: masks, overlays, and a CSV file with evaluation metrics.
3. A short report (3-5 pages) in "`doc/`" explaining:
   - your pipeline (step by step),
   - your design choices,
   - quantitative results,
   - limitations and possible improvements.

---

## 4. Tips

- Start by making the pipeline work on 1–2 images before scaling to the full dataset.
- Save intermediate results (preprocessed images, masks) in "`results/`" to debug easily.
- Use "`viz_utils.py`" to quickly visualize overlays and check if segmentation is reasonable.
- Keep your code modular and clean: small functions, clear parameters, comments.
