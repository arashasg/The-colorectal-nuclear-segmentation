
In this project, I’ve used transfer learning and U-net to implement a model for medical image segmentation.

# Model:
In this project, I used the U-net model, a well-known model for medical image segmentation. What’s more, I used transfer learning. I used Resnet as the backbone of my U-net with pretrained parameters of image-net.
## Dataset:
The colorectal nuclear segmentation and phenotypes (CoNSeP) dataset consist of 41 H&E stained image tiles, each of size 1,000×1,000 pixels at 40× objective magnification. The images were extracted from 16 colorectal adenocarcinomas (CRA) WSIs, each belonging to an individual patient, and scanned with an Omnyx VL120 scanner within the department of pathology at University Hospitals Coventry and Warwickshire, UK.


## Implementation pipeline

First of all, I could make the dataset fit the input layer of Resnet. Given the fact that each image in our dataset is 1,000x1,000 pixels, I divided each image into sixteen 256*256 images. Each image has an eight-pixels-overlap with its adjacent parts.
  ![alt text](https://github.com/arashasg/The-colorectal-nuclear-segmentation/blob/make_readme/images/Capture.PNG?raw=true)
    In addition, I used Image Generator to augment the data. What is challenging about using image generator is that I could use segmentation label corresponding to each image too. So, I used the seed number the same as the seed number I used for the image itself. Plus that, I used zooming in and out for data augmentation too. Image generator uses the average value of pixels when the image is zoomed in, and I used the round value of each segmentation label to make it represent a class in segmentation.
    Finally, I used the segmentation-models library, a library based on the Keras framework, and trained my model using preprocessed data.
  
  
## Results
After 100 epochs, we reached an accuracy of 87 percent and an IOU of 49 percent. In the image below, you can see one of the outputs of the model.
 ![alt text](https://github.com/arashasg/The-colorectal-nuclear-segmentation/blob/make_readme/images/result.PNG?raw=true)
