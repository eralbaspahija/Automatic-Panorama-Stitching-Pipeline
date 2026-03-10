# Automatic Panorama Stitching Pipeline

This project implements an automatic panorama stitching system using computer vision techniques in Python and OpenCV. The pipeline detects image features, matches them between images, estimates geometric transformations, and blends the images to produce a seamless panorama.

The implementation also allows comparison of multiple blending strategies, enabling evaluation of how different techniques affect the final stitched panorama.

---

# Features

- Automatic feature detection using SIFT
- Feature matching with FLANN and Lowe’s ratio test
- Homography estimation using RANSAC to remove outliers
- Perspective warping to align images
- Multiple image blending techniques
- Automatic black border removal
- Visualization of feature matches
- Comparison of blending methods

---

# Pipeline Overview

The panorama stitching pipeline follows these steps:

1. **Input Images**
   - Two overlapping images are provided as input (left and right).

2. **Feature Detection**
   - SIFT (Scale-Invariant Feature Transform) detects keypoints and computes descriptors.

3. **Feature Matching**
   - FLANN-based matcher finds correspondences between descriptors.
   - Lowe’s ratio test filters unreliable matches.

4. **Homography Estimation**
   - RANSAC estimates a robust transformation between the two images.

5. **Image Warping**
   - The right image is warped to align with the left image.

6. **Image Blending**
   - Different blending strategies combine the images smoothly.

7. **Black Border Removal**
   - The final panorama is cropped to remove empty areas.

---

# Blending Methods Implemented

The project compares four blending techniques:

## 1. None (Simple Overlay)
Directly overlays the left image onto the warped right image.

## 2. Linear Blending
Applies a linear interpolation in the overlap region.

## 3. Feather Blending
Uses distance transforms to weight pixels based on their distance from edges.

## 4. Multiband Blending
Uses Gaussian and Laplacian pyramids to blend images at multiple spatial frequencies, producing smoother transitions.

---

# Installation

Clone the repository:
git clone https://github.com/eralbaspahija/Automatic-Panorama-Stitching-Pipeline.git

Install dependencies:
pip install opencv-python numpy matplotlib


If using SIFT with OpenCV:
pip install opencv-contrib-python


---

# Running the Project

The script will:

1. Load two images
2. Run the stitching pipeline
3. Compare blending methods
4. Save the results in the `output/` folder


---

# Example Usage

Load images:
img_left = cv2.imread("img/002.jpg")
img_right = cv2.imread("img/003.jpg")


# Results

The system successfully stitches overlapping images and demonstrates how different blending techniques affect the quality of the panorama. Among the tested methods, multiband blending typically produces the smoothest transitions between images.
<img width="794" height="332" alt="image" src="https://github.com/user-attachments/assets/5c5e7f43-1612-4946-8e05-cb14e7ae3d80" />
<img width="1526" height="1181" alt="image" src="https://github.com/user-attachments/assets/b9218ccd-5133-46ec-9136-fee0356d7618" />


---

# Paper 
Find here our work prepared ond a pdf paper:
[Automatic Panorama Stitching Pipeline.pdf](https://github.com/user-attachments/files/25867045/Automatic.Panorama.Stitching.Pipeline.pdf)

