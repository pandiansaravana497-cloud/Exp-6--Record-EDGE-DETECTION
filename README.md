# edge-detection-opencv

## Aim

To perform edge detection using Sobel, Roberts, Prewitt, Laplacian, and Canny edge detectors.

---

## Software Required

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (cv2)  
- NumPy  
- Matplotlib  

---

## ⚙️ Algorithm

### Step 1:
Import all the necessary modules for the program.

### Step 2:
Load an image using `cv2.imread()`.

### Step 3:
Convert the image to grayscale.

### Step 4:
Apply **Sobel operator** using OpenCV to detect edges.

### Step 5:
Apply **Prewitt operator** using custom kernels.

### Step 6:
Apply **Roberts operator** using custom kernels.

### Step 7:
Apply **Laplacian operator** using OpenCV.

### Step 8:
Apply **Canny edge detector** using OpenCV.

### Step 9:
Display all edge-detected images for comparison.

---
## Program
```

# Edge Detection Using OpenCV
# Operators: Sobel, Prewitt, Roberts, Laplacian and Canny

# Step 1: Import necessary modules
import cv2
import numpy as np
import matplotlib.pyplot as plt
import os

# Step 2: Load an image
image_path = "Eagle_in_Flight.jpg"

img = cv2.imread(image_path)

if img is None:
    print("Error: Image not found!")
    print("Please place Eagle_in_Flight.jpg in the project folder.")
    exit()

print("Image loaded successfully!")

# Step 3: Convert image to grayscale
gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)

print("Image converted to grayscale successfully!")

# Step 4: Apply Sobel operator
sobel_x = cv2.Sobel(gray, cv2.CV_64F, 1, 0, ksize=3)
sobel_y = cv2.Sobel(gray, cv2.CV_64F, 0, 1, ksize=3)

sobel = cv2.magnitude(sobel_x, sobel_y)
sobel = cv2.convertScaleAbs(sobel)

print("Sobel edge detection completed!")

# Step 5: Apply Prewitt operator using custom kernels
prewitt_x = np.array([
    [-1, 0, 1],
    [-1, 0, 1],
    [-1, 0, 1]
])

prewitt_y = np.array([
    [-1, -1, -1],
    [ 0,  0,  0],
    [ 1,  1,  1]
])

px = cv2.filter2D(gray, cv2.CV_32F, prewitt_x)
py = cv2.filter2D(gray, cv2.CV_32F, prewitt_y)

prewitt = cv2.magnitude(px, py)
prewitt = cv2.convertScaleAbs(prewitt)

print("Prewitt edge detection completed!")

# Step 6: Apply Roberts operator using custom kernels
roberts_x = np.array([
    [1,  0],
    [0, -1]
])

roberts_y = np.array([
    [ 0, 1],
    [-1, 0]
])

rx = cv2.filter2D(gray, cv2.CV_32F, roberts_x)
ry = cv2.filter2D(gray, cv2.CV_32F, roberts_y)

roberts = cv2.magnitude(rx, ry)
roberts = cv2.convertScaleAbs(roberts)

print("Roberts edge detection completed!")

# Step 7: Apply Laplacian operator
laplacian = cv2.Laplacian(gray, cv2.CV_64F)
laplacian = cv2.convertScaleAbs(laplacian)

print("Laplacian edge detection completed!")

# Step 8: Apply Canny edge detector
canny = cv2.Canny(gray, 100, 200)

print("Canny edge detection completed!")

# Step 9: Display all edge-detected images for comparison
images = [
    cv2.cvtColor(img, cv2.COLOR_BGR2RGB),
    gray,
    sobel,
    prewitt,
    roberts,
    laplacian,
    canny
]

titles = [
    "Original Image",
    "Grayscale Image",
    "Sobel Edge Detection",
    "Prewitt Edge Detection",
    "Roberts Edge Detection",
    "Laplacian Edge Detection",
    "Canny Edge Detection"
]

plt.figure(figsize=(15, 10))

for i in range(len(images)):
    plt.subplot(3, 3, i + 1)

    if i == 0:
        plt.imshow(images[i])
    else:
        plt.imshow(images[i], cmap="gray")

    plt.title(titles[i])
    plt.axis("off")

plt.tight_layout()

# Save comparison output
plt.savefig("Edge_Detection_Results.png", dpi=300)

plt.show()

print("\nAll edge detection operations completed successfully!")
print("Comparison image saved as Edge_Detection_Results.png")

```

## Developed By

- **Name:**PON SARAVANA PANDIAN B
- **Register No:**212225230207
---

## Output

###  Sobel Edge Detector

<img width="667" height="486" alt="image" src="https://github.com/user-attachments/assets/77fc8fcb-fc97-4f8a-a992-8c454e6c74bf" />


###  Prewitt Edge Detector

 <img width="662" height="477" alt="image" src="https://github.com/user-attachments/assets/a2e08613-7c67-4e9b-b0d5-0cbc7a37b3e6" />


###  Roberts Edge Detector

<img width="667" height="502" alt="image" src="https://github.com/user-attachments/assets/f036a281-e20a-47b1-b30f-61a0cde7c939" />


###  Laplacian Edge Detector

 <img width="677" height="475" alt="image" src="https://github.com/user-attachments/assets/086c2b65-8568-4dfa-9026-7b4d3ec3de97" />


###  Canny Edge Detector

 <img width="681" height="477" alt="image" src="https://github.com/user-attachments/assets/fd9dcfb9-517e-47ac-9e46-915f9a14122c" />


---

## Result

Thus, edges are successfully detected using Sobel, Prewitt, Roberts, Laplacian, and Canny edge detection techniques. Each method highlights edges differently based on gradient and intensity variations, improving feature extraction and analysis.
