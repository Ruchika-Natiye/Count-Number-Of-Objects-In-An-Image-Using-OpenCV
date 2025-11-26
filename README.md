# Count-Number-Of-Objects-In-An-Image-Using-OpenCV

## 🪙 Coin Counter using OpenCV
A simple and effective computer vision project to detect and count multiple objects (coins) in an image using OpenCV, Python, and contour detection.This project demonstrates the complete image-processing pipeline including grayscale conversion, blurring, edge detection, contour extraction, and visualization.

## 🚀 Features
✔ Detects and counts coins or circular objects

✔ Uses Canny Edge Detection

✔ Uses contour detection (cv2.findContours)

✔ Displays each stage of processing

✔ Ready for custom images

## 🧠 How It Works (Pipeline)
* Load the image

* Convert to grayscale to simplify pixel information

* Apply Gaussian Blur to reduce noise

* Detect edges using Canny

* Dilate edges to strengthen contour connectivity

* Find contours using OpenCV

* Draw contours on the image

* Count coins based on number of contours detected

## | Technology  | Purpose                              |
| -------------- | ------------------------------------ |
| **Python**     | Main programming language            |
| **OpenCV**     | Image processing & contour detection |
| **NumPy**      | Numerical operations                 |
| **Matplotlib** | Visualization                        |

## 🔍 Overview
This project uses classical image-processing techniques such as:

* Grayscale conversion
* Gaussian blurring
* Canny edge detection
* Contour detection
* Object counting

## Code Breakdown
Import libraries
```python
import cv2
import numpy as np
import matplotlib.pyplot as plt
```
Read the image by using "cv2.imread(image-name)" & convert this image into grayscale image using "cv2.cvtColor(image-name,cv2.COLOR_BGR2GRAY)" commands.
```python
image = cv2.imread('coins.jpg')
gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
plt.imshow(gray, cmap='gray')
```

![img]()

For counting, we have to detect the edges but before detecting the edges we have to make the image blur to avoid the noises. Use "cv2.GaussianBlur(image-name, Kernal size, std. deviation)". 
```python
blur = cv2.GaussianBlur(gray, (11, 11), 0)
plt.imshow(blur, cmap='gray')
```

![img]()

Now we will detect edges using a canny algorithm, 2nd & 3rd parameters in cv2.canny() function are threshold values. a value between 30 & 150 are consider as an edge for this image.
```python
canny = cv2.Canny(blur, 30, 150, 3)
plt.imshow(canny, cmap='gray')
```

![img]()

We can see that edges are not connected. We need to connect the edges, have to make more thiker & visible. 
```python
dilated = cv2.dilate(canny, (1, 1), iterations=0)
plt.imshow(dilated, cmap='gray')
```

![img]()

Now we have to calculate the contour in the image & convert the image into RGB from BGR & then draw the contours.
```python
(cnt, hierarchy) = cv2.findContours(dilated.copy(), cv2.RETR_EXTERNAL, cv2.CHAIN_APPROX_NONE)
rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)
cv2.drawContours(rgb, cnt, -1, (0, 255, 0), 2)
plt.imshow(rgb)
```

![img]()

Printing the result
```python
 Printing the result
```

![img]()

## ⭐ Support
If you like this project, please ⭐ star the repository and share it!
