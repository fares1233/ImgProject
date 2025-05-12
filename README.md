# Image Enhancement Techniques

This repository contains explanations and implementations of advanced image processing techniques, focusing on contrast enhancement and image detail improvement. The project includes multiple methods for enhancing image quality, especially in challenging conditions like low or uneven lighting.

# Requirements

- Python 3.x
- NumPy
- OpenCV (cv2)
- Matplotlib (for visualization)
- skimage
- 
# Techniques
 
## visual documentation
  ![alt text](/visual.jpg)

## Log Transformation

Log transformation is a point operation that applies the logarithmic function to each pixel in an image. It enhances low-intensity (dark) pixels while compressing high intensity (bright) pixels.
This makes it useful for images with a wide range of brightness levels.

**Mathematical Formula:**

s = c \* log(1 + r)

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

**Import required libraries**

- np.array(image).astype(np.float64): Converts the image into a numerical array of float values.
- np.log1p(img_array): Applies the natural log transformation (log(1 + x)) to brighten dark areas.
- c : The constant c controls the intensity of the enhancement.
- Normalization: Scales the result to the 0–255 range suitable for images.
- Returns a new image with log transformation applied.

**images**

- np.array(image).astype(np.float64): Converts the image into a numerical array of float values.
- np.log1p(img_array): Applies the natural log transformation (log(1 + x)) to brighten dark areas.
- c : The constant c controls the intensity of the enhancement.
- Normalization: Scales the result to the 0–255 range suitable for images.
- Returns a new image with log transformation applied.
  ![alt text](/log1.jpg)

- Splits the enhanced image into red, green, and blue channels.
- Equalizes each channel to improve contrast.
- Merges them back to form the final enhanced image.
  ![alt text](/log2.jpg)
- **results**
  ![alt text](/fullMark.jpg)

## CLAHE (Contrast Limited Adaptive Histogram Equalization)

CLAHE is an advanced image processing technique used to enhance the contrast of images, especially in localized regions, while limiting noise amplification.

**Key Features:**

- **Adaptive**: Unlike traditional histogram equalization, CLAHE divides the image into small regions (tiles) and performs histogram equalization on each tile individually
- **Contrast Limited**: To prevent overamplification of noise, CLAHE clips the histogram at a predefined limit before redistributing pixel values
- **Better Local Contrast**: Works well for images with varying lighting conditions

**How CLAHE Works**

1. Divide the Image into small tiles (e.g., 8×8 or 16×16).
2. Compute Histogram for each tile.
3. Clip the Histogram at a specified limit (prevents noise amplification).
4. Redistribute Pixel Values to enhance contrast.
5. Interpolate neighboring tiles to avoid blocky artifacts.

**images**

- Apply Global and local equalization
  ![alt text](/clahe1.jpg)

  **results**
  ![alt text](/claheRes.jpg)

## Gamma Transformation

Gamma transformation is a non-linear operation used to encode and decode luminance or tristimulus values in images. It is particularly useful for correcting the brightness of an image. The operation can brighten or darken an image depending on the gamma value (γ).

This transformation is commonly used in image enhancement to adjust the contrast of images with different lighting conditions.

**Mathematical Formula:**

s = c \* r^γ

Where:

- s: Output pixel value (transformed)
- r: Input pixel value (normalized)
- c: Scaling constant (often set to 1)
- γ (gamma): Gamma value that controls the enhancement
  - γ < 1 → brightens the image
  - γ > 1 → darkens the image

**Application Process:**

1. Read the image
2. Normalize the pixel values to the range [0, 1]
3. Apply the gamma transformation formula
4. Rescale the output back to appropriate range (e.g., 0–255 for 8-bit images)

**images**

1.  gamma = self.technique_params["gamma"]["value"]
    o Retrieves the user-defined gamma value from the UI slider
    o This value determines the intensity of the correction (range: 0.1-3.0)
    o Values < 1 brighten the image, values > 1 darken the image
2.  inv_gamma = 1.0 / gamma
    o Calculates the inverse of gamma for the power-law transformation
3.  lut = np.array([((i / 255.0) ** inv_gamma) * 255 for i in range(256)]).astype("uint8")
    o Creates a lookup table (LUT) for all possible pixel values (0-255)
    o Applies the gamma formula: output = input^(1/gamma)
    o Normalizes input values to range 0-1, applies power function, then scales back to 0-255
    o Converts the result to 8-bit unsigned integer format
    o This pre-computation makes the transformation more efficient
4.  return cv2.LUT(img, lut)
    o Applies the lookup table to the entire image in one operation
    o This is faster than processing each pixel individually
    o Returns the gamma-corrected image
  ![alt text](/gamm1.jpg)

- **results**
  ![alt text](/gammaRes.jpg)



## Team members

1. Fares Metwally Elshafey
2. Marwan Atef Mahmoud
3. Youssef Mohamed Sherif
4. Yomna Mohammed Fathi
5. Youssef Mahmoud Fawzy
6. Maryam Tariq Abdul Ghani
