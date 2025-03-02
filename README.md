# VR_Assignment1_AryanMishra_IMT2022502


This repository contains two parts for **VR Assignment 1**:

1. **Coin Detection, Segmentation, and Counting**  
2. **Panorama Creation**

Both parts are implemented in separate Jupyter notebooks:  
- `coins.ipynb`  
- `panorama.ipynb`


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

## 2. Part 1: Coin Detection, Segmentation, and Counting
Notebook: coins.ipynb
Methods

    Detection:

        Edge detection (Canny) + Hough Circle Transform

    Segmentation:

        Thresholding + Contour analysis

    Counting:

        Simple enumeration of detected coins

How to Run

    Place input images in images/ folder.

    Update file paths in the notebook if needed.

    Run all cells sequentially.

    Outputs saved to:

        images/coin_detection_output.jpg

        images/coin_segmentation.jpg

        images/coin_count.jpg

Sample Outputs

<img src="images/coin_detection_output.jpg" width="200"> <img src="images/coin_segmentation.jpg" width="200"> <img src="images/coin_count.jpg" width="200">
3. Part 2: Panorama Creation
Notebook: panorama(1).ipynb
Methods

    Keypoint Extraction:

        SIFT features (requires OpenCV contrib)

    Feature Matching:

        FLANN-based matcher + RANSAC for homography

    Warping & Blending:

        Perspective transformation + Linear blending

How to Run

    Place panorama images (panoramaA.jpg, panoramaB.jpg, etc.) in images/.

    Run all notebook cells.

    Final panorama saved as images/panorama_result.jpg.

Sample Output
<img src="images/panorama_result.jpg" width="600">
4. Observations
Coin Detection

    Works best with non-overlapping coins and uniform lighting.

    Adjust cv2.HoughCircles() parameters for different coin sizes.

Panorama

    Requires ~30-50% overlap between images.

    Works best with rotational camera motion (minimal translation).

5. Troubleshooting

    SIFT Errors: Install opencv-contrib-python instead of regular OpenCV.

    Large File Sizes: Clear notebook outputs before commit:
    bash
    Copy

    jupyter nbconvert --clear-output --inplace *.ipynb

Contact

    Name: Your Name

    Email: your.email@domain.com

    GitHub: your_github_handle

Copy


### Steps to Use:
1. **Replace placeholders** like `YourName`, `YourRollNo`, and contact details.
2. Ensure the `images/` folder and sample files exist in your repository.
3. Run the command below to clear Jupyter notebook outputs (to reduce file size):
   ```bash
   jupyter nbconvert --clear-output --inplace coins.ipynb panorama(1).ipynb

New chat
