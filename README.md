
# Adaptive Thresholding in Computer Vision

Adaptive thresholding is a technique used in image processing to segment an image into foreground and background. Unlike global thresholding, which uses a single threshold value for the entire image, adaptive thresholding calculates the threshold for smaller regions of the image. This makes it particularly useful for images with varying lighting conditions.

## How Adaptive Thresholding Works

- **Global Thresholding:**
    - Applies a single threshold value to the entire image.
    - Not effective for images with non-uniform illumination.

- **Adaptive Thresholding:**
    - Calculates different threshold values for different regions of the image.
    - Handles varying lighting conditions effectively.

## Types of Adaptive Thresholding

1. **Mean Thresholding:**
    - The threshold value is the mean of the neighborhood area minus a constant \(C\).

2. **Gaussian Thresholding:**
    - The threshold value is a Gaussian-weighted sum of the neighborhood values minus a constant \(C\).

## Sample Code

Here's a Python example using OpenCV to perform adaptive thresholding:

```python
import cv2
import numpy as np

# Load the image
image = cv2.imread('input.jpg', cv2.IMREAD_GRAYSCALE)

# Apply global thresholding
_, global_thresh = cv2.threshold(image, 127, 255, cv2.THRESH_BINARY)

# Apply adaptive mean thresholding
mean_thresh = cv2.adaptiveThreshold(image, 255, cv2.ADAPTIVE_THRESH_MEAN_C, 
                                    cv2.THRESH_BINARY, 11, 2)

# Apply adaptive Gaussian thresholding
gaussian_thresh = cv2.adaptiveThreshold(image, 255, cv2.ADAPTIVE_THRESH_GAUSSIAN_C, 
                                        cv2.THRESH_BINARY, 11, 2)

# Save the results
cv2.imwrite('global_thresh.jpg', global_thresh)
cv2.imwrite('mean_thresh.jpg', mean_thresh)
cv2.imwrite('gaussian_thresh.jpg', gaussian_thresh)

# Display the results
cv2.imshow('Global Thresholding', global_thresh)
cv2.imshow('Adaptive Mean Thresholding', mean_thresh)
cv2.imshow('Adaptive Gaussian Thresholding', gaussian_thresh)
cv2.waitKey(0)
cv2.destroyAllWindows()
