# Image Enhancement Techniques

This repository contains explanations and implementations of advanced image processing techniques, focusing on contrast enhancement and image detail improvement. The project includes multiple methods for enhancing image quality, especially in challenging conditions like low or uneven lighting.

# Techniques

# Log Transformation

Log transformation is a point operation that applies the logarithmic function to each pixel in an image. It enhances low-intensity (dark) pixels while compressing high intensity (bright) pixels. 
This makes it useful for images with a wide range of brightness levels.

**Mathematical Formula:**

s = c * log(1 + r)

Where:
- s: Output pixel value (transformed)
- r: Input pixel value (original)
- c: Scaling constant (often set to normalize the output)
- The addition of 1 avoids log(0), which is undefined

**Application Process:**
1. Read the image
2. Normalize the pixel values
3. Apply the log transformation formula
4. Rescale the output to appropriate range (typically 0-255 for 8-bit images)

**Best Used For:**
- Enhancing darker details in images
- High dynamic range images

# CLAHE (Contrast Limited Adaptive Histogram Equalization)

CLAHE is an advanced image processing technique used to enhance the contrast of images, especially in localized regions, while limiting noise amplification.

**Key Features:**
- **Adaptive**: Unlike traditional histogram equalization, CLAHE divides the image into small regions (tiles) and performs histogram equalization on each tile individually
- **Contrast Limited**: To prevent overamplification of noise, CLAHE clips the histogram at a predefined limit before redistributing pixel values
- **Better Local Contrast**: Works well for images with varying lighting conditions

# How CLAHE Works
1.	Divide the Image into small tiles (e.g., 8×8 or 16×16).
2.	Compute Histogram for each tile.
3.	Clip the Histogram at a specified limit (prevents noise amplification).
4.	Redistribute Pixel Values to enhance contrast.
5.	Interpolate neighboring tiles to avoid blocky artifacts.


# Requirements

- Python 3.x
- NumPy
- OpenCV (cv2)
- Matplotlib (for visualization)

# Team members
1. Fares Metwally Elshafey                                          
2. Marwan Atef Mahmoud
3. Youssef Mohamed Sherif
4. Yomna Mohammed Fathi
5. Youssef Mahmoud Fawzy
6. Maryam Tariq Abdul Ghani                                                      
