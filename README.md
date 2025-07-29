# Detective-AI

due to restictions on git hub, we can not upload the data set to git hub. 
Data set can be found it this google drive: https://drive.google.com/drive/folders/1ZGJb7yAfj8LG1e_l6OX00y47G1no-BMg?usp=drive_link 

# How to run Detective-AI

1. Download the data set from the google drive. (you do not need to unzip the folder)
2. Run Detective-AI.ipynb in google colab
3. where you are promted to upload a file, upload the zipped data set. (This will take some time)

Training may take 2 hours

# Research Questions:


The goal of our project was to develop an AI image recognition model that can distinguish real images from AI-generated content with high accuracy. In the world today, the use of AI to generate content and images is becoming increasingly prevalent. This makes the ability to identify AI-generated images extremely useful. Internet users could fact check images online, social media companies could prevent misinformation, and real artists could get the credit they deserve for their work. Our application will allow users to upload an image and find out if it was real or fake.


# Approach:

We utilized a dataset with 30,000 real images and 30,000 AI-generated images found on Kaggle at https://www.kaggle.com/datasets/tristanzhang32/ai-generated-images-vs-real-images?select=train. For AI-generated images, 10,000 were made with Stable Diffusion, 10,000 with MidJourney, and 10,000 with DALL-E. For real images, 22,500 come from Pexels and Unsplash, while 7,500 come from WikiArt. We then reduce this data set down to 10,000 random AI-generated-images and 10,000 random real images with 20,000 total images. We then split these images into a training set of 16,000 images, validation set of 2,000 images and testing set of 2,000 images.

Our group built our model on Google Collab, using TensorFlow and Keras. TensorFlow is an open-source framework for machine learning developed by Google, and Keras is a user-friendly API for TensorFlow. Our model uses ResNet50, a well-known residual network trained on millions of images, as a base model. Residual networks are a type of deep convolutional neural network that contain residual connections, allowing information to skip layers to avoid the vanishing gradient problem.
 
This gave our model a strong foundation, which we built upon with additional layers. First, there are two convolutional layers that extract simple features such as edges and shapes. This is followed by a dense layer to learn complex objects and patterns. Then we use a dropout layer to prevent the model from overfitting to the training data. The final layer uses sigmoid activation instead of softmax because there are only two labels, real and fake, making this a binary classification problem.

# Results/Takeaways:

The model successfully predicted whether an image was real or fake 87.3% of the time and a loss of 0.5272. This means that our model was generally accurate most of the time, it is not confident in its prediction. We found that our model had a bias of labeling images as fake more than real.

One of the main issues was the wide range of images in our data set. While we were only looking for what is real and what was fake, there are differences between a real face and a real landscape. This is a potential reason for our model’s bias. To identify the difference between two things that are real and are completely different, different weights are needed to determine the difference. Since we had a wide range of images in our real and fake data set, the model tried to set weights to cover a wide range of images. It would have been more effective to limit the scope to specific identifications and explain from there.
