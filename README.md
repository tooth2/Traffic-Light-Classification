# Traffic-Light-Classification
A open-cv and CNN(Tensorflow) implementation to detect Traffic light (red, yellow, green) state

This project is to build a classifier for images of traffic lights usingg Open CV(1) and CNN(2) for given a dataset of traffic light images in which one of three lights is illuminated: red, yellow, or green.

The tasks will be broken down into a few sections:
0. Loading and visualizing the data : load in the images of traffic lights and visualize some of them
1. Pre-processing: The input images and output labels need to be standardized. This way, all the standardized input images are processed in the same classification pipeline, and output when you eventually classify a new image.
2. Feature extraction: extract some features from each image that will help distinguish the different types of images, and use those features to classify the traffic light images into three classes: Red, Yellow, or Green
3. Accuracy : Classification and visualizing errors that uses features to classify any traffic light image. This function will take in an image and output a label. 4. Evaluate your model: The accuracy of the classifier must be >90% accurate and never classify any red lights as green; improve the accuracy of the classifier by changing existing features or adding new features. 

Here are some sample images from the dataset (from left to right: red, green, and yellow traffic lights):

## The Data Set
This traffic light dataset consists of 1484 number of color images in 3 categories - red, yellow, and green. As with most human-sourced data, the data is not evenly distributed among the types. 
- 904 red traffic light images
- 536 green traffic light images
- 44 yellow traffic light images
Note: All images come from this MIT self-driving car course and are licensed under a Creative Commons Attribution-ShareAlike 4.0 International License.

## Traning and Testing Data
All 1484 of the traffic light images are separated into training and testing datasets.
- 80% of these images are training images
- 20% are test images, which will be used to test the accuracy
- All images are pictures of 3-light traffic lights with one light illuminated.

### Pre-process the data
- One hot encoded labels:  
    - Red light label: [1, 0, 0]
    - Yellow light label: [0, 1, 0]
    - Green light label: [0, 0, 1]
- Resize each image to the desired input size: 32x32px

### Feature extraction
- standardized image
- HSV color-masked image
- cropped image
- brightness feature (using HSV color space): convert RGB to HSV and identify 3 different classes of traffic light


### Apply CNN - Define Model 
|Layer (type)      |           Output Shape   |           Param #   |
=================================================================
|batch_normalization_1 |(Batch (None, 32, 32, 3)   |      12       | 
|conv2d_1 (Conv2D)    |        (None, 30, 30, 16)   |     448       |
|max_pooling2d_1 |(MaxPooling2 (None, 15, 15, 16)   |     0         |
|batch_normalization_2 |(Batch (None, 15, 15, 16)     |   64        |
| conv2d_2 (Conv2D)       |     (None, 13, 13, 32)     |   4640      |
|max_pooling2d_2| (MaxPooling2 (None, 6, 6, 32)      |    0         |
|batch_normalization_3 |(Batch (None, 6, 6, 32)     |     128       |
|conv2d_3 (Conv2D)          |  (None, 4, 4, 64)   |       18496     |
|max_pooling2d_3 |(MaxPooling2 (None, 2, 2, 64)   |       0         |
|batch_normalization_4 |(Batch (None, 2, 2, 64)       |   256       |
|global_average_pooling2d_1| ( (None, 64)        |       0         |
|dense_1 (Dense)          |    (None, 3)          |       195       |


### Result
- OpenCV test accuracy   : 96.6330%
- Deep Learning(CNN) accuracy: 100.0000%
