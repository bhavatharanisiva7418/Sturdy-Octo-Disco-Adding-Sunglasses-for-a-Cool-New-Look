# Sturdy-Octo-Disco-Adding-Sunglasses-for-a-Cool-New-Look

Sturdy Octo Disco is a fun project that adds sunglasses to photos using image processing.

Welcome to Sturdy Octo Disco, a fun and creative project designed to overlay sunglasses on 
individual passport photos! This repository demonstrates how to use image processing 
techniques to create a playful transformation, making ordinary photos look extraordinary. 
Whether you're a beginner exploring computer vision or just looking for a quirky project to 
try, this is for you!

## Features:
1. Detects the face in an image.
2. Places a stylish sunglass overlay perfectly on the face.
3. Works seamlessly with individual passport-size photos.
4. Customizable for different sunglasses styles or photo types.

   
## Technologies Used:
1.Python
2.OpenCV for image processing
3.Numpy for array manipulations

## How to Use:
1.Clone this repository.
2.Add your passport-sized photo to the images folder.
3.Run the script to see your "cool" transformation!

## Applications:
1.Learning basic image processing techniques.
2.Adding flair to your photos for fun.
3.Practicing computer vision workflows.

## Program:

## Developed By: BHAVATHARANI S
## Register No:212223230032

```
import cv2
import numpy as np
import matplotlib.pyplot as plt

faceImage = cv2.imread('Tharini.jpg')
plt.imshow(faceImage[:,:,::-1]);plt.title("Face")

faceImage.shape

glassPNG = cv2.imread('glass.png',-1)
plt.imshow(glassPNG[:,:,::-1]);plt.title("glassPNG")

glassPNG = cv2.resize(glassPNG,(190,50))
print("image Dimension ={}".format(glassPNG.shape))

glassBGR = glassPNG[:,:,0:3]
glassMask1 = glassPNG[:,:,3]

plt.figure(figsize=[15,15])
plt.subplot(121);plt.imshow(glassBGR[:,:,::-1]);plt.title('Sunglass Color channels');
plt.subplot(122);plt.imshow(glassMask1,cmap='gray');plt.title('Sunglass Alpha channel');

faceWithGlassesNaive = faceImage.copy()
faceWithGlassesNaive[135:185,125:315]=glassBGR
plt.imshow(faceWithGlassesNaive[...,::-1])

glassMask = cv2.merge((glassMask1,glassMask1,glassMask1))
glassMask = np.uint8(glassMask/255)
faceWithGlassesArithmetic = faceImage.copy()
eyeROI= faceWithGlassesArithmetic[135:185,125:315]
maskedEye = cv2.multiply(eyeROI,(1-  glassMask ))
maskedGlass = cv2.multiply(glassBGR,glassMask)
eyeRoiFinal = cv2.add(maskedEye, maskedGlass)
plt.figure(figsize=[20,20])
plt.subplot(131);plt.imshow(maskedEye[...,::-1]);plt.title("Masked Eye Region")
plt.subplot(132);plt.imshow(maskedGlass[...,::-1]);plt.title("Masked Sunglass Region")
plt.subplot(133);plt.imshow(eyeRoiFinal[...,::-1]);plt.title("Augmented Eye and Sunglass")

faceWithGlassesArithmetic[135:185,125:315]=eyeRoiFinal
plt.figure(figsize=[20,20]);
plt.subplot(121);plt.imshow(faceImage[:,:,::-1]); plt.title("Original Image");
plt.subplot(122);plt.imshow(faceWithGlassesArithmetic[:,:,::-1]);plt.title("With Sunglasses");

```
## Output

## Uploading image

![image](https://github.com/user-attachments/assets/a28dbe86-0707-493c-9449-83b29baa1ef3)

## Glass image

 ![image](https://github.com/user-attachments/assets/aa22ff92-75df-44b8-a3b1-26f8d122d76f)

## Appliying BGR


![image](https://github.com/user-attachments/assets/b94245e4-6f39-4cec-b76c-de726117c030)

## Placing sunglass

![image](https://github.com/user-attachments/assets/05825b86-be14-4df1-b2a9-b8ce34a3303f)

## Augmented Eye and Sunglass

![image](https://github.com/user-attachments/assets/7e0616aa-a8d7-4d13-8fb1-f8d7455ed44a)

## Final output

![image](https://github.com/user-attachments/assets/4e2e6e9a-7791-4759-8a1f-b674b4259fd0)

## Result
Thus the sunglass are placed successfully


