## Title:

Multi-Region Image Segmentation using Otsu Thresholding (Computer Vision)

## Executive Summary:

This project implements a computer vision image segmentation algorithm using Otsu’s thresholding method. The program converts RGB images into grayscale, computes pixel intensity histograms, and automatically determines optimal threshold values that separate the image into meaningful regions.

Unlike binary thresholding, the algorithm supports multi-region segmentation (2, 3, and 4 regions), allowing the image to be partitioned into multiple intensity-based groups. The segmented output highlights different object regions using color mapping, enabling visual interpretation of structural components within an image.

The project demonstrates how classical computer vision techniques can automatically extract structure from images without supervised learning.

## Methodology:
### 1) Image Preprocessing
Each image is first converted from RGB to grayscale using luminance weighting:
- Red weight: 0.299
- Green weight: 0.587
- Blue weight: 0.114

This preserves brightness perception similar to human vision.

### 2) Histogram Generation
A normalized intensity histogram is calculated:
- 256 intensity levels (0–255)
- Probability distribution of pixel brightness

This histogram represents how brightness values are distributed across the image.


<img width="360" height="280" alt="basket_balls bmp_histogram" src="https://github.com/user-attachments/assets/92485998-631b-4074-a3fc-88fd8eacfaed" />
<img width="360" height="280" alt="data13 bmp_histogram" src="https://github.com/user-attachments/assets/b3e973e9-3157-46a3-a679-676f20d3463a" />
<img width="360" height="280" alt="tiger1 bmp_histogram" src="https://github.com/user-attachments/assets/154c0190-8a0d-4611-a3a1-a900c50d4ad2" />

### 3) Otsu Thresholding
The algorithm determines optimal thresholds by minimizing intra-class variance.

For each candidate threshold:
- Split pixels into groups
- Compute weight of each group
- Compute mean intensity
- Compute variance
- Choose threshold with minimum weighted variance

The method is extended to support:
- 2 regions -> 1 threshold
- 3 regions -> 2 thresholds
- 4 regions -> 3 thresholds

**2 Region:**
<img width="683" height="329.5" alt="2_Region_basket_balls-out" src="https://github.com/user-attachments/assets/6a1fcba2-6c6a-402d-a0e4-de4be560ee1c" />

### 4) Image Segmentation
Pixels are assigned to regions based on thresholds and color-coded:
- Region 1 -> Yellow
- Region 2 -> Red
- Region 3 -> Green
- Region 4 -> Blue

This produces a segmented image highlighting different structures.

### 5) Output Generation
For each image:
- Apply segmentation for multiple region counts
- Save segmented outputs in an output directory
- Print threshold values and group variances

## Skills:
- **Computer Vision:** Image segmentation, Thresholding algorithms, Histogram analysis
- **Algorithms:** Otsu’s method, Variance minimization, Multi-class partitioning
- **Programming:** Python, NumPy array processing, PIL image handling, File automation
- **Mathematics:** Probability distributions, Variance calculation, Optimization methods

## Results
- Successfully segments images into meaningful intensity regions
- Automatically detects thresholds without manual tuning
- Works for multiple segmentation levels (2–4 regions)
- Demonstrates effectiveness of statistical image partitioning
