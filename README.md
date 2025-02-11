# Face Recognition Project

## Overview

This project implements a basic face recognition system using OpenCV and Haar cascades. It detects faces in images using the `haarcascade_frontalface_default.xml` classifier and draws rectangles around the detected faces.

## Features

*   **Face Detection:** Detects faces in images using the Haar cascade classifier.
*   **Image Processing:** Reads images from a directory, converts them to grayscale, and applies the face detection algorithm.
*   **Visual Output:** Displays the images with rectangles around the detected faces.

## Requirements

*   Python 3.x
*   OpenCV (`cv2`)
*   Glob
  
Download the `haarcascade_frontalface_default.xml` file from the [OpenCV repository](https://raw.githubusercontent.com/opencv/opencv/master/data/haarcascades/haarcascade_frontalface_default.xml) and place it in the same directory as the script.

*  Ensure you have a directory with `.jpg` images for testing.

## Usage

1.  Place the `Face-Recognition.ipynb` file, the `haarcascade_frontalface_default.xml` file, and the images you want to test in the same directory.
2.  Open the `Face-Recognition.ipynb` file using Jupyter Notebook or JupyterLab.
3.  Run the cells in the notebook. The script will:

    *   Read all `.jpg` images from the directory.
    *   Detect faces in each image.
    *   Display the images with rectangles around the detected faces for 2 seconds each.
  
## Code Explanation

import cv2, glob
Get all .jpg images from the current directory
gimage = glob.glob("*.jpg")
Load the Haar cascade classifier for face detection
detect = cv2.CascadeClassifier('haarcascade_frontalface_default.xml')
Check if the cascade file loaded successfully
if detect.empty():
print(f"Error: Unable to load cascade file: haarcascade_frontalface_default.xml")
exit()
Iterate through each image
for timage in gimage:
# Read the image
image = cv2.imread(timage)
# Convert the image to grayscale
grayimg = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
# Detect faces in the grayscale image
face = detect.detectMultiScale(grayimg, 1.25, 3)
text
# Draw rectangles around the detected faces
for (x, y, w, h) in face:
    cv2.rectangle(image, (x, y), (x+w, y+h), (0, 255, 0), 2)

# Display the image with detected faces
cv2.imshow("Detect images", image)
# Wait for 2 seconds
cv2.waitKey(2000)

# Close all open windows
cv2.destroyAllWindows()
text

*   **Import Libraries:** Imports the necessary libraries (`cv2` for OpenCV and `glob` for file handling).
*   **Load Haar Cascade:** Loads the `haarcascade_frontalface_default.xml` file, which is a pre-trained Haar cascade classifier for face detection.
*   **Image Loading and Processing:**
    *   Reads all `.jpg` images from the current directory.
    *   Converts each image to grayscale because the Haar cascade classifier works on grayscale images.
    *   Uses the `detectMultiScale` function to detect faces in the grayscale image. This function returns a list of rectangles representing the detected faces.
*   **Drawing Rectangles:** Iterates through the detected faces and draws a rectangle around each face on the original color image.
*   **Displaying Images:** Displays the image with the detected faces for 2 seconds and then closes the window.

## Troubleshooting

*   **Error: Unable to load cascade file:** Ensure that the `haarcascade_frontalface_default.xml` file is in the same directory as the script and that the path is correct.
*   **No faces detected:** Adjust the `scaleFactor` and `minNeighbors` parameters in the `detectMultiScale` function.  `scaleFactor` (1.25 in the example) affects how much the image size is reduced at each image scale, and `minNeighbors` (3 in the example) affects how many neighboring rectangles each candidate rectangle should have to retain it.

