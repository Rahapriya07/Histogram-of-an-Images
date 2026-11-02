# EXPERIMENT No.3 – HISTOGRAM PROCESSING
## Name : Raha Priya Dharshini M
## Reg no.: 212224240124
## Aim
To perform histogram processing on an image using OpenCV and Python. To display the original image histogram and apply histogram equalization to improve image contrast in grayscale and colour images.

## Procedure
1. Import the required libraries such as OpenCV and Matplotlib.
2. Read the input image (`myfoto.jpg`) using OpenCV.
3. Convert the original image into grayscale.
4. Display the grayscale image and plot its histogram using `plt.hist()`.
5. Apply histogram equalization using `cv2.equalizeHist()`.
6. Display the equalized grayscale image and its histogram.
7. Read the original image in colour format.
8. Convert the image from BGR to HSV colour space.
9. Apply histogram equalization to the Value (V) channel.
10. Convert the equalized image back to BGR and display the original and equalized colour images for comparison.


## Code
```

import cv2
import numpy as np
import matplotlib.pyplot as plt

img = cv2.imread('myfoto.jpg', cv2.IMREAD_COLOR)

if img is None:
    raise FileNotFoundError("myfoto.jpg not found")

gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)

plt.figure(figsize=(8, 6))
plt.imshow(gray, cmap='gray')
plt.title('Original Grayscale Image')
plt.axis('off')
plt.show()

plt.figure(figsize=(10, 6))
plt.hist(gray.ravel(), 256, range=[0, 256])
plt.title('Original Image Histogram')
plt.xlabel('Pixel Intensity')
plt.ylabel('Frequency')
plt.show()

gray_eq = cv2.equalizeHist(gray)

plt.figure(figsize=(8, 6))
plt.imshow(gray_eq, cmap='gray')
plt.title('Histogram Equalized Image')
plt.axis('off')
plt.show()

plt.figure(figsize=(10, 6))
plt.hist(gray_eq.ravel(), 256, range=[0, 256])
plt.title('Equalized Histogram')
plt.xlabel('Pixel Intensity')
plt.ylabel('Frequency')
plt.show()

plt.figure(figsize=(15, 6))

plt.subplot(1, 2, 1)
plt.hist(gray.ravel(), 256, range=[0, 256])
plt.title('Original Image Histogram')
plt.xlabel('Pixel Intensity')
plt.ylabel('Frequency')

plt.subplot(1, 2, 2)
plt.hist(gray_eq.ravel(), 256, range=[0, 256])
plt.title('Equalized Image Histogram')
plt.xlabel('Pixel Intensity')
plt.ylabel('Frequency')

plt.tight_layout()
plt.show()

img_hsv = cv2.cvtColor(img, cv2.COLOR_BGR2HSV)

img_hsv[:, :, 2] = cv2.equalizeHist(img_hsv[:, :, 2])

color_eq = cv2.cvtColor(img_hsv, cv2.COLOR_HSV2BGR)

plt.figure(figsize=(8, 6))
plt.imshow(cv2.cvtColor(color_eq, cv2.COLOR_BGR2RGB))
plt.title('Equalized Colour Image')
plt.axis('off')
plt.show()

plt.figure(figsize=(15, 6))

plt.subplot(1, 2, 1)
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.title('Original Color Image')
plt.axis('off')

plt.subplot(1, 2, 2)
plt.imshow(cv2.cvtColor(color_eq, cv2.COLOR_BGR2RGB))
plt.title('Equalized Color Image')
plt.axis('off')

plt.tight_layout()
plt.show()
```
## Output Screenshots

### 1. Original Grayscale Image
<img width="1372" height="546" alt="image" src="https://github.com/user-attachments/assets/dba8dd4a-542c-4449-8e83-43ec19aee440" />


### 2. Original Image Histogram
<img width="1352" height="692" alt="image" src="https://github.com/user-attachments/assets/44411d3d-71f1-47ef-a8c5-383606359066" />


### 3. Equalized Grayscale Histogram
<img width="1347" height="678" alt="image" src="https://github.com/user-attachments/assets/a4b02d12-40d2-4a82-8d01-991f86e648cc" />


### 4. Original and Equalized Colour Image
<img width="1342" height="546" alt="image" src="https://github.com/user-attachments/assets/711bc8da-45d0-42b2-8292-063294dad93d" />

### Equalized Color Image Histogram
<img width="1351" height="682" alt="image" src="https://github.com/user-attachments/assets/6f515f8d-a660-4561-9905-7b2d800af897" />

## Result
Thus, histogram processing and histogram equalization were successfully performed on grayscale and colour images using OpenCV. The histograms were plotted and the original and equalized images were displayed for comparison.
