# Ten class landmark recognition project

The problem comes from a famous Kaggle competition, the Google Landmark Recognition Challenge. Training set contains over 1.2 million images spread across 14,951 classes of landmarks, varying from one to thousands of images per class. This problem of extreme classification is something that is very prevalent in the data science community today with the advancement of deep learning.

Example of image from data set of Charles Bridge, Prague:

![Alt text](/images/train/2061/779e3ce783d13c85.jpg)

I decided to reduce a scale of project by choosing ten main classes with 1000 images from each as train set, 200 images of each as validation set and 20 images of each for test set.


### Basic CNN

We build a sequential model and add convolutional layers and max pooling layers to it. We also add dropout layers in between, dropout randomly switches off some neurons in the network which forces the data to find new paths. Therefore, this reduces overfitting. We add dense layers at the end which are used for class prediction.

Max-pooling: A technique used to reduce the dimensions of an image by taking the maximum pixel value of a grid. This also helps reduce overfitting and makes the model more generic. The example below show how 2 x 2 max pooling works

Exaple of 3 layers network on the image below:

![Alt text](/cnn-schema1.jpeg)


## Transfer Learning - predictions using weights from ImageNet (VGG16)

Transfer learning is using pre-trained CNN architecture. When we train our own data on the top of the pre-trained parameters, we can easily reach to the target accuracy.

Different CNN architectures could be found in the Keras library — for example VGG16, VGG19, Inception, etc. While VGG19 and Inception are more heavier architectures (number of parameters to train), training VGG16 was doable in the time frame that we had.

The architecture of VGG16: the input layer takes an image in the size of (224 x 224 x 3), and the output layer is a softmax prediction on 1000 classes. From the input layer to the last max pooling layer (labeled by 7 x 7 x 512) is regarded as the feature extraction part of the model, while the rest of the network is regarded as the classification part of the model.

![alt text](https://s3.ap-south-1.amazonaws.com/techleer/309.jpg)
