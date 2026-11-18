# Geometric Transformations Using OpenCV

---

## Aim

To write a Python program using OpenCV to perform various geometric transformations on an image.

The program performs the following operations:

- Image Translation  
- Image Scaling (Resizing)  
- Image Shearing  
- Image Reflection (Flipping)  
- Image Rotation  

---

## Software Used

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (`cv2`)  
- NumPy  
- Matplotlib  

---

## Algorithm

### Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:
Read the input image in color mode.

### Step 3: Image Translation
- Create a translation matrix to shift the image  
- Move the image 50 pixels to the right and 80 pixels down  
- Apply transformation using `cv2.warpAffine()`  
- Display original and translated images  

### Step 4: Image Scaling
- Resize the image to 0.5× (downscale)  
- Resize the image to 2× (upscale)  
- Use `cv2.resize()`  
- Display original, downscaled, and upscaled images  

### Step 5: Image Shearing
- Create transformation matrices for:
  - Horizontal shearing  
  - Vertical shearing  
- Apply transformations using `cv2.warpAffine()`  
- Display original and sheared images  

### Step 6: Image Reflection
- Perform flipping using `cv2.flip()`:
  - Horizontal reflection  
  - Vertical reflection  
  - Both axes  
- Display all reflected images  

### Step 7: Image Rotation
- Create rotation matrices for:
  - 45° rotation  
  - 90° rotation  
- Use `cv2.getRotationMatrix2D()` and `cv2.warpAffine()`  
- Display original and rotated images  

---

## Program

### Developed By: Vikamuhan Reddy

### Register No: 212223240181

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Read the input image
img = cv2.imread('parrot.jpg')

if img is None:
    print("Image not found!")
else:
    # Convert BGR to RGB for displaying
    image = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

    h, w = img.shape[:2]

    # 1. Image Translation
    M = np.float32([[1, 0, 50],
                    [0, 1, 80]])

    translated = cv2.warpAffine(img, M, (w, h))

    # 2. Image Scaling
    downscaled = cv2.resize(img, None, fx=0.5, fy=0.5)
    upscaled = cv2.resize(img, None, fx=2, fy=2)

    # 3. Image Shearing
    horizontal_matrix = np.float32([
        [1, 0.5, 0],
        [0, 1, 0]
    ])

    vertical_matrix = np.float32([
        [1, 0, 0],
        [0.5, 1, 0]
    ])

    horizontal_shear = cv2.warpAffine(img, horizontal_matrix, (w, h))
    vertical_shear = cv2.warpAffine(img, vertical_matrix, (w, h))

    # 4. Image Reflection
    horizontal_flip = cv2.flip(img, 1)
    vertical_flip = cv2.flip(img, 0)
    both_flip = cv2.flip(img, -1)

    # 5. Image Rotation
    center = (w // 2, h // 2)

    M45 = cv2.getRotationMatrix2D(center, 45, 1)
    rotated45 = cv2.warpAffine(img, M45, (w, h))

    M90 = cv2.getRotationMatrix2D(center, 90, 1)
    rotated90 = cv2.warpAffine(img, M90, (w, h))

    # Function to display images
    def show_image(title, image):
        plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
        plt.title(title)
        plt.axis('off')

    # Display Translation
    plt.figure(figsize=(10, 5))
    plt.subplot(1, 2, 1)
    show_image("Original Image", img)

    plt.subplot(1, 2, 2)
    show_image("Translated Image", translated)
    plt.show()

    # Display Scaling
    plt.figure(figsize=(12, 5))
    plt.subplot(1, 3, 1)
    show_image("Original Image", img)

    plt.subplot(1, 3, 2)
    show_image("Downscaled Image", downscaled)

    plt.subplot(1, 3, 3)
    show_image("Upscaled Image", upscaled)
    plt.show()

    # Display Shearing
    plt.figure(figsize=(12, 5))
    plt.subplot(1, 3, 1)
    show_image("Original Image", img)

    plt.subplot(1, 3, 2)
    show_image("Horizontal Shearing", horizontal_shear)

    plt.subplot(1, 3, 3)
    show_image("Vertical Shearing", vertical_shear)
    plt.show()

    # Display Reflection
    plt.figure(figsize=(12, 5))
    plt.subplot(2, 2, 1)
    show_image("Original Image", img)

    plt.subplot(2, 2, 2)
    show_image("Horizontal Flip", horizontal_flip)

    plt.subplot(2, 2, 3)
    show_image("Vertical Flip", vertical_flip)

    plt.subplot(2, 2, 4)
    show_image("Both Axes Flip", both_flip)
    plt.show()

    # Display Rotation
    plt.figure(figsize=(10, 5))
    plt.subplot(1, 3, 1)
    show_image("Original Image", img)

    plt.subplot(1, 3, 2)
    show_image("45 Degree Rotation", rotated45)

    plt.subplot(1, 3, 3)
    show_image("90 Degree Rotation", rotated90)
    plt.show()
```

##  Output

### Image Translation
<img width="833" height="255" alt="image" src="https://github.com/user-attachments/assets/ddbd2992-74a1-4a5b-a241-776c01ca61ee" />


### Image Scaling
<img width="972" height="215" alt="image" src="https://github.com/user-attachments/assets/662c6121-d146-49ca-9458-e7866eafac93" />


### Image Shearing
<img width="966" height="212" alt="image" src="https://github.com/user-attachments/assets/8c98b5e4-85ae-4582-b8b3-1ac551b7a74a" />


### Image Reflection
<img width="826" height="422" alt="image" src="https://github.com/user-attachments/assets/3594c977-d352-478f-9650-9c451b717862" />


### Image Rotation
<img width="802" height="171" alt="image" src="https://github.com/user-attachments/assets/b9c3fd30-1078-473f-b12e-02d451d0b4f2" />

---

##  Result

Thus, various geometric transformations such as translation, scaling, shearing, reflection, and rotation are successfully performed using OpenCV. These transformations demonstrate how images can be spatially manipulated for different computer vision applications.
