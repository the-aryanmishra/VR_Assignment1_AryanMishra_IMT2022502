# VR_Assignment1_AryanMishra_IMT2022502


This repository contains two parts for **VR Assignment 1**:

1. **Coin Detection, Segmentation, and Counting**  
2. **Panorama Creation**

Both parts are implemented in separate Jupyter notebooks:  
- `coins.ipynb`  
- `panorama(1).ipynb`

---
## Repository Structure

VR_Assignment1_[YourName]_[YourRollNo]/
├── coins.ipynb # Notebook for coin detection/segmentation/counting
├── panorama(1).ipynb # Notebook for panorama creation
├── README.md
├── images/
│ ├── coins_input.jpg # Input image with scattered coins
│ ├── coin_detection_output.jpg # Detected coins with outlines
│ ├── coin_segmentation.jpg # Segmented coins
│ ├── coin_count.jpg # Final count visualization
│ ├── panoramaA.jpg # Overlapping image A
│ ├── panoramaB.jpg # Overlapping image B
│ ├── panoramaC.jpg # Overlapping image C
│ └── panorama_result.jpg # Final stitched panorama
└── requirements.txt

---

## 1. Requirements and Setup

### Dependencies
- **Python 3.7+**  
- **Jupyter Notebook/Lab**  
- **OpenCV** (`opencv-contrib-python` for SIFT features)  
- **NumPy**  
- **Matplotlib**

Install dependencies:
```bash
pip install opencv-contrib-python numpy matplotlib jupyter
