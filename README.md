# Medical-Image-classification

## About this project : 
### Using Computer vision and Convolutional neural networks to identify Double Contours in X-ray images.

## What is a double contour ? 
### A double contour is a hyperechoic band over the superficial margin of the anechoic hyaline cartilage, which is highly specific for gout.

## Steps followed in the jupyter notebook:

### Before starting I used an online tool to split the images into equal parts to increase the amount of data.
### This is the site I used : https://products.aspose.app/pdf/split-image

### 1. Let's start by doing what you should always do when starting a new project. Create a new environment and import all the libraries using the "requirements.txt" file.


### 2. After importing our libraries we are ready for preprocessing our data and extract features from them. We use the popular "open cv" module for this.


### 3. After extracting our edge features from the brightest pixels of the image data, we can store them in a seperate file and create a dataframe to structure the data. Hence making it easier to handle them. In this case we are only considering pixels with intensity greater than 150.


### 4. Now we are at one of the most important steps of training any machine learning and deep learning model, cross-validation. But since we only have 15 images it doesn't seem like a good idea to split them further. That's where the next step comes in.


### 5. when we don't have ample amount of data we use a technique called "Data Augmentation". Data Augmentation is a technique that slightly modifies already exsisting image data and creates copies of them which is new data for our model to work with. We can use the ImageDataGenerator mmodule for this.


### 6. We are finally ready to do some training. As mentioned before we plan to use a Convolutional neural network since it specializes in dealing with image data, we can start with a simple model and start experimenting with all the hyperparameters and fine-tune our model. 
In this case I used a CNN with 2 layers with a kernel size of 16, 32 respectively. 
I used a sigmoid activation function instead of softmax since it's a binary classification problem.
As for the loss function I used the "Binary crossentropy" and for the optimizer I used the "Adam" optimizer with a learning rate of 0.0001.
I also used different weights of 5:1 for both classes since it's an imbalanced dataset. 
After setting all these parameters the model is trained with a maximum of 50 epochs.

We can also use callbacks like learning rate reduction and early stopping to automate some hyperperameter tuning which I did here.


### 7. After some experimentation we can save the model using the pickle module, but since we only trained with just a small amount of image data, this might not be reliable. But we can still use this as a blueprint to train again when we have access to more image data.

### 8. After we train the model we can vizualise our models metrics like Loss and accuracy using the matplotlib library and vizualise progression of our model training with each epoch.

### 9. Finally, when everything seems to work, we can build a custom function that takes in a file path and returns whether it contains a Double Contour or not.
