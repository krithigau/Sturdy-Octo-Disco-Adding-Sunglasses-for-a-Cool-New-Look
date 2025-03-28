# Sturdy-Octo-Disco-Adding-Sunglasses-for-a-Cool-New-Look

Sturdy Octo Disco is a fun project that adds sunglasses to photos using image processing.

Welcome to Sturdy Octo Disco, a fun and creative project designed to overlay sunglasses on individual passport photos! This repository demonstrates how to use image processing techniques to create a playful transformation, making ordinary photos look extraordinary. Whether you're a beginner exploring computer vision or just looking for a quirky project to try, this is for you!

## Features:
- Detects the face in an image.
- Places a stylish sunglass overlay perfectly on the face.
- Works seamlessly with individual passport-size photos.
- Customizable for different sunglasses styles or photo types.

## Technologies Used:
- Python
- OpenCV for image processing
- Numpy for array manipulations

## How to Use:
1. Clone this repository.
2. Add your passport-sized photo to the `images` folder.
3. Run the script to see your "cool" transformation!

## Applications:
- Learning basic image processing techniques.
- Adding flair to your photos for fun.
- Practicing computer vision workflows.

  ## PROGRAM:
Developed by: KRITHIGA U
Register Number: 212223240076

```
# Import libraries and Load the Face Image
import cv2
import numpy as np
import matplotlib.pyplot as plt
faceImage = cv2.imread('643.JPG')
plt.imshow(faceImage[:,:,::-1]);plt.title("Face")
```

![Screenshot 2025-03-28 154221](https://github.com/user-attachments/assets/33b51c90-9e70-4e42-8b89-256a04660d52)

```
# Resize the image to fit over the eye region
glassPNG = cv2.resize(glassPNG,(190,70))
print("image Dimension ={}".format(glassPNG.shape))
```

![{2AAE967A-60D4-4E06-98DF-59B6EC38B1C2}](https://github.com/user-attachments/assets/1483e940-e2cd-4d9e-9a55-25fd2a01a87a)

```
# Resize the image to fit over the eye region
glassPNG = cv2.resize(glassPNG,(190,70))
print("image Dimension ={}".format(glassPNG.shape))

# Separate the Color and alpha channels
glassBGR = glassPNG[:,:,0:3]
glassMask1 = glassPNG[:,:,3]

# Display the images for clarity
plt.figure(figsize=[15,15])
plt.subplot(121);plt.imshow(glassBGR[:,:,::-1]);plt.title('Sunglass Color channels');
plt.subplot(122);plt.imshow(glassMask1,cmap='gray');plt.title('Sunglass Alpha channel');
```

![Screenshot 2025-03-28 155754](https://github.com/user-attachments/assets/633e8132-3884-4c82-985c-2c189ff216e8)

```
faceWithGlassesNaive = faceImage.copy()
# Replace the eye region with the sunglass image
faceWithGlassesNaive[150:220, 120:310]=glassBGR

plt.imshow(faceWithGlassesNaive[...,::-1])
```

![Screenshot 2025-03-28 155845](https://github.com/user-attachments/assets/dafd9f1b-9e24-4cc9-8448-2366ae455a84)

```
glassMask = cv2.merge((glassMask1,glassMask1,glassMask1))
glassMask = np.uint8(glassMask/255)
faceWithGlassesArithmetic = faceImage.copy()
eyeROI= faceWithGlassesArithmetic[150:220, 120:310]
maskedEye = cv2.multiply(eyeROI,(1-glassMask ))
maskedGlass = cv2.multiply(glassBGR,glassMask)
eyeRoiFinal = cv2.add(maskedEye, maskedGlass)
plt.figure(figsize=[20,20])
plt.subplot(131);plt.imshow(maskedEye[...,::-1]);plt.title("Masked Eye Region")
plt.subplot(132);plt.imshow(maskedGlass[...,::-1]);plt.title("Masked Sunglass Region")
plt.subplot(133);plt.imshow(eyeRoiFinal[...,::-1]);plt.title("Augmented Eye and Sunglass")
```

![Screenshot 2025-03-28 160004](https://github.com/user-attachments/assets/3049cc04-7199-44b7-a13c-d6a87bfc489d)

```
faceWithGlassesArithmetic[150:220, 120:310]=eyeRoiFinal
plt.figure(figsize=[20,20]);
plt.subplot(121);plt.imshow(faceImage[:,:,::-1]); plt.title("Original Image");
plt.subplot(122);plt.imshow(faceWithGlassesArithmetic[:,:,::-1]);plt.title("With Sunglasses");
```

![Screenshot 2025-03-28 112803](https://github.com/user-attachments/assets/2291beaf-89f4-4dfd-815c-d89643d9d1ab)
 

Feel free to fork, contribute, or customize this project for your creative needs!
