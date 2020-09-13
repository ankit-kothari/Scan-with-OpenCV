[Google Colaboratory](https://colab.research.google.com/drive/18-qfthoIIMOv0RBEEGksfrp8hNM2wxau?usp=sharing)

## Loading the Image

1. Load the image
2. The default setting of the color mode in OpenCV comes in the order of BGR, which is different from that of Matplotlib. Therefore to see the image in GRAYSCALE mode, we need to convert it from BGR to GRAYSCALE as follows.
3. Convert it into a grayscale image

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a6450c50-33d3-42f2-89b3-5c0649615efe/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a6450c50-33d3-42f2-89b3-5c0649615efe/Untitled.png)

original image

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ff5c7f85-2eab-4b0c-88d9-9b753d510ea0/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ff5c7f85-2eab-4b0c-88d9-9b753d510ea0/Untitled.png)

grayscale image

## Blurring the Image

- The goal of blurring is to perform noise reduction.
- There are several techniques used to achieve blurring effects in OpenCV: Averaging blurring, Gaussian blurring, median blurring and bilateral filtering, **Non-Local Means Denoising**.
    - Types of Blurring

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/60902abb-0573-46a0-adc7-e7e01268e6e2/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/60902abb-0573-46a0-adc7-e7e01268e6e2/Untitled.png)

blurring the image 

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/95333fce-c01e-45e9-aa75-a0745e4abb04/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/95333fce-c01e-45e9-aa75-a0745e4abb04/Untitled.png)

de-noising the image 

## Thresholding

1. Thresholding transforms images into binary images. We need to set the threshold value and max values and then we convert the pixel values accordingly. 
2. There are five different types of thresholding: 
    - Binary,  cv2.THRESH_BINARY
    - the inverse of Binary,  cv2.THRESH_BINARY_INV
    - Threshold to zero,  cv2.THRESH_TOZERO
    - the inverse of Threshold to Zero,  cv2.THRESH_TOZERO_INV
    - and Threshold truncation.  cv2.THRESH_TRUNC
3. Adaptive thresholding, by calculating the threshold within the neighborhood area of the image, we can achieve a better result from images with varying illumination.
    - For Adaptive thresholding Image should be grayscale.
    - The parameters of adaptive thresholding are maxValue (255), adaptiveMethod , thresholdType , blockSize and C .
    - And the adaptive method here has two kinds: ADAPTIVE_THRESH_MEAN_C , ADAPTIVE_THRESH_GAUSSIAN_C

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8a380078-6b0a-4fe0-8602-62c5a72bcd6a/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8a380078-6b0a-4fe0-8602-62c5a72bcd6a/Untitled.png)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0fc170f2-a37e-4e2a-b662-3110dafe8bda/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0fc170f2-a37e-4e2a-b662-3110dafe8bda/Untitled.png)

## **Edge Detection**

1. **[Edge detection](https://en.wikipedia.org/wiki/Edge_detection)** means identifying points in an image where the brightness changes sharply or discontinuously. We can draw line segments with those points, which are called ***edges***.
2. Then, we need to provide two values: threshold1 and threshold2. Any gradient value larger than threshold2 is considered to be an edge. Any value below threshold1 is considered not to be an edge.
3. Values in between threshold1 and threshold2 are either classiﬁed as edges or non-edges based on how their intensities are “connected”.

          canny = cv2.Canny(image, threshold1,  threshold2)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a7a201d8-4f93-4818-876d-b8b0ffeaf908/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a7a201d8-4f93-4818-876d-b8b0ffeaf908/Untitled.png)

## Morphological transformations

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5ac69658-98b2-41ff-9da2-eeff64b0369c/Screen_Shot_2020-06-17_at_2.01.22_AM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5ac69658-98b2-41ff-9da2-eeff64b0369c/Screen_Shot_2020-06-17_at_2.01.22_AM.png)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f730de3b-2165-4701-a47d-d05107325b36/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f730de3b-2165-4701-a47d-d05107325b36/Untitled.png)

## Contour detection

1. The cv2.findContours function stores a  numpy array of (x,y) points that from that contour

2. Retrieval Mode:

- cv2.CHAIN_APPROX_NONE – Stores all the points along the line
- cv2.CHAIN_APPROX_SIMPLE – Stores the end points of each line (efficient)

3. Sort the contours by Area to get the top 4 contours, i.e the edges in the image forming a square

4. Using cv2. approxpolyDP  function is used to approximate the contour, (with approximation accuracy, and closed (True or False) polygon). It will give the result of the number of individual lines or end points (4 in this case as it is square)

5. Using cv2.drawContours function draw the contour shape using the  identified contour which has length 4 in this example

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/755bd87a-cd42-494d-8526-4ec4ead18fff/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/755bd87a-cd42-494d-8526-4ec4ead18fff/Untitled.png)

## Affine Transformation

- Transformations are geometric distortions enacted upon an image
- It is used to correct distortions and perspective issues.
- Affine Transformation helps to modify the geometric structure of the image, preserving parallelism of lines but not the lengths and angles. It preserves collinearity and ratios of distances.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0016a20c-fdfc-49d0-9520-ebb48c0c1681/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0016a20c-fdfc-49d0-9520-ebb48c0c1681/Untitled.png)

## Final Output

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a6450c50-33d3-42f2-89b3-5c0649615efe/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a6450c50-33d3-42f2-89b3-5c0649615efe/Untitled.png)

original image

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d3b2cad8-9d12-4fc2-a0df-9edddd2eea82/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d3b2cad8-9d12-4fc2-a0df-9edddd2eea82/Untitled.png)

scanned image
