# EXPERIMENT 7 – Record-HOUGH TRANSFORM
# Name: DHIVYASHREE R
# REGNO: 212225040077

## Aim

To implement a basic lane/line detection pipeline using OpenCV by detecting edges using the Canny operator and identifying lines using the Hough Transform.

## Software Required

- Anaconda – Python
- Jupyter Notebook
- OpenCV (cv2)
- NumPy
- Matplotlib

## Program

### Step 1: Import Libraries

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt
```

### Step 2: Read the Image

```python
# Step 2: Load the image using imread() from cv2 module
image = cv2.imread('me.jpeg')  # Replace 'image.jpg' with your image path
```

### Step 3: Convert to Grayscale

```python
# Step 3: Convert the image to grayscale
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
```

### Step 4: Display the Original Image

```python
# Input image and grayscale image
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title("Input Image")
plt.axis('off')
```

### Step 5: Display the Grayscale Image

```python
plt.imshow(gray_image, cmap='gray')
plt.title("Grayscale Image")
plt.axis('off')
```

### Step 6: Edge Detection Using Canny

```python
# Step 4: Using Canny operator from cv2, detect the edges of the image
edges = cv2.Canny(gray_image, 50, 150)
```

### Step 7: Display Canny Edge Output

```python
# Canny Edge Detector output
plt.imshow(edges, cmap='gray')
plt.title("Canny Edge Detector")
plt.axis('off')
```

### Step 8: Detect Lines Using Hough Transform

```python
# Step 5: Using the HoughLinesP(), detect line coordinates for every point in the image
# The parameters of HoughLinesP are: image, resolution, threshold, minLineLength, maxLineGap
lines = cv2.HoughLinesP(edges, 1, np.pi / 180, 100, minLineLength=50, maxLineGap=10)
```

### Step 9: Draw Detected Lines

```python
# Step 6: Draw detected lines on the original image
if lines is not None:
    for line in lines:
        x1, y1, x2, y2 = line.ravel()[:4]
        cv2.line(image, (int(x1), int(y1)),
                 (int(x2), int(y2)), (0, 255, 0), 2)
else:
    print("No lines detected")
```

### Step 10: Display Final Output

```python
# Display the result of Hough Transform (Image with lines)
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title("Result of Hough Transform")
plt.axis('off')
```

## Output

# 1. Original input image
<img width="227" height="410" alt="image" src="https://github.com/user-attachments/assets/764c6b80-b008-4fe7-a165-15767b21a568" />

# 2. Grayscale image
<img width="227" height="410" alt="image" src="https://github.com/user-attachments/assets/b5b9401d-f4b2-4533-9b72-e3f536f08905" />

# 3. Canny edge detected image
<img width="227" height="410" alt="image" src="https://github.com/user-attachments/assets/e020744d-e0dc-4d8c-8d57-6897b3a6877d" />

# 4. Final image with Result of hough-transform
<img width="244" height="410" alt="image" src="https://github.com/user-attachments/assets/6fa0910e-7427-43b9-b9e1-6829180a1026" />


## Result

Thus, the basic lane/line detection pipeline was implemented successfully using OpenCV. Edges were detected using the Canny operator, and line segments were detected using the Hough Transform and highlighted on the original image.
