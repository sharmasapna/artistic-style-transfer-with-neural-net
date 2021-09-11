# artistic-style-transfer-with-neural-net
This is python code for the implementation of the paper a **Neural Algorithm for Artistic Style**

#### Installation dependencies:

TensorFlow   
Scipy   
Numpy   

#### Download the VGG-19 model

#### Feel free to use the images "content_image" and "style image" as they are in dimesions in accordance with the code

#### Result obtained

 <img src="https://github.com/sharmasapna/artistic-style-transfer-with-neural-net/blob/main/images/Figure3%20obtained%20for%20NAAS%20paper.png" width="400">
 
 
 #### tensorflow2 implementation at :
 https://www.pluralsight.com/guides/artistic-neural-style-transfer-with-tensorflow-2.0:-theory
 
 
I would like to thank my team mates Abdul Rehman, Siddharth Sathyanaranayan for teaming up with me to implement this paper.
We tried to replicate the Figure 3 presented in the paper A Neural Algorithm for Artistic Style (https://arxiv.org/pdf/1508.06576v2.pdf )

Steps to follow :

1. Get images for content and style.   
2. Preprocess it.   
3. Download the pre-trained vgg19 model.   
4. Obtain the mean values of the images of the pretained model. As this is to be substracted from the image before feeding to the pretrained vgg19 model
5.  our own model from the trained model :   
5.1 We will be using only selected layers of the model that is conv1_1,conv2_1,conv3_1,conv4_1,conv5_1 (all five for the style features) and conv4_2 (for content features).There will be basically 5 differnt models:   
 1. With conv1_1 and conv4_2.  
 2. With conv1_1,conv_2,1 and conv4_2.  
 3. With conv1_1,conv2_1,conv3_1 and conv4_2.  
 4. With conv1_1,conv_2,1,conv3_1,conv4_1 and conv4_2.   
 5. With conv1_1,conv_2,1,conv3_1,conv4_1,conv5_1 and conv4_2.   
 And we will be presenting the results for four different beta values (100000,10000,1000,100) for each layer.     
5.2 We will use average pooling instead of max pooling as done in vgg19 architechture.   
Calculating the total loss(content loss and style loss):   
6.1 generate an image with white noise or an image with some noise in the content image. This will be our final image.   
6.2 Calculate the content loss as the squared difference between the original content image and the generated image.   
6.3 Calclulate the style loss by squared difference between the gram matrices of the original style image and the genrated image.   
6.4 Gram matrices are the correlation between different filter responses given by the Gram matrix Gˡ, where Gˡᵢⱼ is the inner product between the vectorized feature map i and j in layer l.   
6.5 The total loss is the sum of the product of style weight(beta) and the style loss and content weight(alpha) and content loss.   
Adam optimizer was used for gradient descent. We experimented with different learning rates for each of the 20 figures.   
#### Some of our experiences:   
If we initiate the generated image with white noise, we do not get the desired results. So we used the content image with a certain noise added to it as a starting generated image.Experimented with different noise ratio.   
Image resolution affects the overall results. Also make sure to use images with correct shape (250,300) otherwise the model will give error.   
It takes approximately 30 minutes to run this code on the free version of google colab for 2000 iterations.   

For more clarity watch the video at : https://www.youtube.com/watch?v=0tTRA3emrr4&t=29s https://www.youtube.com/watch?v=K_xBhp1YsrE&t=516s

Parts of code is from : 
https://github.com/log0/neural-style-painting/blob/master/TensorFlow%20Implementation%20of%20A%20Neural%20Algorithm%20of%20Artistic%20Style.ipynb
 
