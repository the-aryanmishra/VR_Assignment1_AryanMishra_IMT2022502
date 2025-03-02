# VR_Assignment1_AryanMishra_IMT2022502

## Overview

This repository contains two separate Python Notebooks:

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

---

## Methods and Approach

### Part 1: Coin Detection, Segmentation, and Counting

1. **Edge Detection**  
   - Load the input image of scattered Indian coins.  
   - Convert the image to grayscale.  
   - Use a smoothing filter or Gaussian blur to reduce noise.  
   - Apply **Canny edge detection** to detect circular coin boundaries.
   - Morphological closing to fill gaps in edges 
   - Use contour-finding methods (e.g., OpenCV `findContours`) to outline the coins.

2. **Segmentation**  
   - Perform a region-based segmentation technique to isolate individual coins.
   - We have shown 3 different ways of doing so where we observe that all 3 methods work but method (b) gives a lot of vacant space also in the segmented output. Both Method(a) and method(c) seem to be giving the best results.
   - Each coin’s boundary is refined and labeled as a separate region.

3. **Coin Counting**  
   - After segmentation, count the total number of detected coins by counting the unique detected regions.

### Part 2: Image Stitching (Panorama)

1. **Keypoint Extraction**  
   - Read multiple overlapping images.  
   - Detect keypoints using **SIFT**.  
   - Compute descriptors for each keypoint.

2. **Image Alignment and Homography**  
   - Match descriptors across overlapping images.  
   - Filter matches (e.g., Lowe’s ratio test).  
   - Estimate a homography transformation that aligns the overlapping areas.

3. **Stitching**  
   - Warp one image onto the plane of the other using the estimated homography.  
   - Blend the overlapped region to reduce visible seams.
   - The above is done using Stitcher from the OpenCV module.
   - The Stitcher essentially matche descriptors across overlapping images, filters matches(e.g., Lowe’s ratio test) and finally estimates a homography transformation that aligns the overlapping areas.
   - Cylindrical warper function turned out to be the best for our requirement.
   - Remove the black borders from the stitched image.
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
3. Run the notebook cell by cell:
   - The code will read the input image.
   - Perform edge detection, segmentation, and coin counting.
   - Display intermediate steps (edge map, segmented coins).
   - Display the final detection overlay and the coin count.

**Panorama Notebook**
	-	Place your overlapping images for panorama creation in the same folder or in a subfolder.
	-	Open panorama.ipynb in Jupyter Notebook:
 ```bash
jupyter notebook panorama.ipynb
```
3.	Run the notebook cell by cell:
	-	The code will detect keypoints in each image.
	-	Match the keypoints and find homography.
	-	Stitch the images together and display the final panorama. 

## Results and Visual Outputs

### Coins Detection and Segmentation

- **Input image:**

  <img width="542" alt="coin_image2" src="https://github.com/user-attachments/assets/41d20bad-baa6-44a1-8073-0d278a3433ba" />

- **Edges:**

  <img width="309" alt="edges" src="https://github.com/user-attachments/assets/19f1c81b-40ba-4376-8671-8187a60d3b45" />

- **Detected coins:**

  <img width="309" alt="detected coins" src="https://github.com/user-attachments/assets/8b74c462-dcd9-464c-a6ed-32cb2194ed31" />

- **Coin Segmentation:**

  <img width="320" alt="coin9" src="https://github.com/user-attachments/assets/26f88c4a-6587-4b76-835f-50ddd9683350" />
  <img width="328" alt="coin8" src="https://github.com/user-attachments/assets/ea356777-61d8-432b-9b0f-9a903096946e" />
  <img width="328" alt="coin7" src="https://github.com/user-attachments/assets/09495aca-1f07-4573-8569-159b9877bdcc" />
  <img width="328" alt="coin6" src="https://github.com/user-attachments/assets/5795040f-e7f9-444a-a250-8c1881382e70" />
  <img width="328" alt="coin5" src="https://github.com/user-attachments/assets/c033f14e-e925-47ea-bb86-5dfc6143869c" />
  <img width="328" alt="coin4" src="https://github.com/user-attachments/assets/de2943ce-634f-4db0-83e7-5a402404a04f" />
  <img width="328" alt="coin3" src="https://github.com/user-attachments/assets/0b270be1-5738-4f22-b1be-361e8dbe81d3" />
  <img width="328" alt="coin2" src="https://github.com/user-attachments/assets/88be7623-0a66-43f2-870d-fd2cf4ab71c9" />
  <img width="328" alt="coin1" src="https://github.com/user-attachments/assets/b7c22ea3-79b0-47f6-a427-1b9fb4b24101" />

- **Coin Count:**

  <img width="513" alt="coins_count" src="https://github.com/user-attachments/assets/1eee9b31-e3d6-4193-a6cb-734f13d612ae" />

	
 ### Panorama Creation

- **Input images:**
![imageA](https://github.com/user-attachments/assets/c4fc048a-9977-4c3c-bf43-8dc9e69b803d)
![imageB](https://github.com/user-attachments/assets/69c35de3-6aed-4415-ad4c-7f06e764b99a)
![imageC](https://github.com/user-attachments/assets/54c7c955-76d7-4051-ad97-95a1fa010101)

- **Keypoints:**

  <img width="639" alt="a_keypoints" src="https://github.com/user-attachments/assets/6d8d0706-9584-48b3-8a35-a10ecf36812f" />
  <img width="639" alt="b_keypoints" src="https://github.com/user-attachments/assets/6aaedd96-06d2-420e-a438-b427c2d50272" />
  <img width="639" alt="c_keypoints" src="https://github.com/user-attachments/assets/b3cf6c58-d57a-4117-a6e9-1ce24cd6349f" />

The dots in the images indicate the keypoints and the circles centered around the keypoints indicate the scale(or size) of the respective  features, and also encode their orientation (the direction in which the feature is most distinctive).


- **Stitched Panorama:**
  ![panorama_result](https://github.com/user-attachments/assets/bb4cd0f1-3f19-47df-934b-a750f81d5683)

 
 ## Observations
1.	Edge Detection Sensitivity
	-	A well-chosen threshold in the Canny edge detector is crucial. If thresholds are too high/low, coins might be over-segmented or missed.
	2.	Segmentation Challenges
	-	If coins overlap or if the lighting is uneven, segmentation can be more difficult.
	-	Morphological operations (e.g., dilation/erosion) help isolate coins.
	3.	Counting Accuracy
	-	The detection method works best when coins do not heavily overlap. Minor overlaps are generally still handled by contour segmentation.
	4.	Panorama Stitching Accuracy
	-	Quality of the final panorama depends on the amount of overlap and distinct features.
	-	Blending artifacts can occur if exposure differs significantly between images.
	5.	Performance
	-	For real-time or large-scale images, efficient implementations or GPU support might be desired.
