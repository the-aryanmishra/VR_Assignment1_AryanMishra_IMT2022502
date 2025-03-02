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
