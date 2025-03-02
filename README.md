# VR_Assignment1_AryanMishra_IMT2022502


# VR Assignment 1 - Coin Detection & Segmentation and Panorama Creation

## Overview

This repository contains two separate Python/Jupyter Notebook projects:

1. **Coin Detection, Segmentation, and Counting** (`coins.ipynb`):
   - Detects Indian coins in an image using edge detection
   - Segments each coin from the background
   - Counts the total number of coins
   - Shows the final detection and segmentation results

2. **Image Stitching** (`panorama.ipynb`):
   - Extracts keypoints from a set of overlapping images
   - Matches keypoints and aligns images
   - Stitches them to create a single panoramic image

The assignments are based on the requirements outlined in **Part 1** (coin detection and segmentation) and **Part 2** (image stitching) of the problem statement.

---

## Table of Contents
1. [Methods and Approach](#methods-and-approach)  
2. [Installation and Requirements](#installation-and-requirements)  
3. [Running the Notebooks](#running-the-notebooks)  
   - [Coin Detection Notebook](#coin-detection-notebook)  
   - [Panorama Notebook](#panorama-notebook)  
4. [Results and Visual Outputs](#results-and-visual-outputs)  
   - [Coins Detection and Segmentation](#coins-detection-and-segmentation)  
   - [Panorama Creation](#panorama-creation)  
5. [Observations](#observations)  
6. [Repository Structure](#repository-structure)  
7. [Credits](#credits)  

---

## Methods and Approach

### Part 1: Coin Detection, Segmentation, and Counting

1. **Edge Detection**  
   - Load the input image of scattered Indian coins.  
   - Convert the image to grayscale, if needed.  
   - Use a smoothing filter or Gaussian blur to reduce noise.  
   - Apply **Canny edge detection** to detect circular coin boundaries.  
   - Use contour-finding methods (e.g., OpenCV `findContours`) to outline the coins.

2. **Segmentation**  
   - Perform a region-based segmentation technique (e.g., **Watershed** or **Thresholding** + **Morphology**) to isolate individual coins.  
   - Each coin’s boundary is refined and labeled as a separate region.

3. **Coin Counting**  
   - After segmentation, count the total number of detected coins by counting the unique detected regions.

### Part 2: Image Stitching (Panorama)

1. **Keypoint Extraction**  
   - Read multiple overlapping images.  
   - Detect keypoints using **ORB** or **SIFT** (depending on library availability).  
   - Compute descriptors for each keypoint.

2. **Image Alignment and Homography**  
   - Match descriptors across overlapping images.  
   - Filter matches (e.g., Lowe’s ratio test).  
   - Estimate a homography transformation that aligns the overlapping areas.

3. **Stitching**  
   - Warp one image onto the plane of the other using the estimated homography.  
   - Blend the overlapped region to reduce visible seams.  
   - Create a final stitched image (the panorama).

---

## Installation and Requirements

1. **Python 3.7+**  
2. **Jupyter Notebook** (optional but recommended for running `.ipynb` files interactively)  
3. **Packages**:  
   - `opencv-python`  
   - `numpy`  
   - `matplotlib`  
   - `scikit-image` (optional, depending on exact segmentation approach)  
   - Any other libraries explicitly imported in the notebooks (e.g., `imutils` if used)

To install the dependencies, run:
```bash
pip install opencv-python numpy matplotlib scikit-image
```
## Running the Notebooks

Clone or download this repository, then open a terminal in the repository folder.

**Coin Detection Notebook**
	1.	Place your coin image (containing multiple Indian coins) in the same folder or in an images/ subfolder.
	2.	Open coins.ipynb in Jupyter Notebook:
 ```bash
jupyter notebook coins.ipynb
```
3.	Run the notebook cell by cell:
	•	The code will read the input image.
	•	Perform edge detection, segmentation, and coin counting.
	•	Display intermediate steps (edge map, segmented coins).
	•	Display the final detection overlay and the coin count.

**Panorama Notebook**
	1.	Place your overlapping images for panorama creation in the same folder or in a subfolder.
	2.	Open panorama.ipynb in Jupyter Notebook:
 ```bash
jupyter notebook panorama.ipynb
```
3.	Run the notebook cell by cell:
	•	The code will detect keypoints in each image.
	•	Match the keypoints and find homography.
	•	Stitch the images together and display the final panorama.

## Results and Visual Outputs

**Coins Detection and Segmentation**
	•	Detected Coins: An image with outlines (e.g., circles or contours) around each coin.
	•	Coin Segmentation: Each coin is isolated (e.g., each coin might be shown in a different labeled mask or bounding box).
	•	Coin Count: The total number of coins is printed (e.g., Total coins detected: 12).

**Panorama Creation**
	•	Stitched Panorama: The final panorama image is displayed, showing how multiple images were merged seamlessly.
 
 ## Observations
1.	Edge Detection Sensitivity
	•	A well-chosen threshold in the Canny edge detector is crucial. If thresholds are too high/low, coins might be over-segmented or missed.
	2.	Segmentation Challenges
	•	If coins overlap or if the lighting is uneven, segmentation can be more difficult.
	•	Morphological operations (e.g., dilation/erosion) help isolate coins.
	3.	Counting Accuracy
	•	The detection method works best when coins do not heavily overlap. Minor overlaps are generally still handled by contour segmentation.
	4.	Panorama Stitching Accuracy
	•	Quality of the final panorama depends on the amount of overlap and distinct features.
	•	Blending artifacts can occur if exposure differs significantly between images.
	5.	Performance
	•	For real-time or large-scale images, efficient implementations or GPU support might be desired.
