# VCV-CPP
<h2>Deep Learning Model with C++ at VeinCV</h2>
<h3>Title: UNET implementation using Pytorch C++ </h3>

This project is about implementing UNET architecture. I used a dataset found here https://www.kaggle.com/c/tgs-salt-identification-challenge which contains images of the earth at different locations aimed to do segmentation to know where salt deposits exist. So the goal is to do semantic segmentation and identify which part of the earth in the image contains salt or sediment (binary classification). Since training with all this data takes a lot of time and requires high computational power, I only used a small part of the dataset.
* 18 images for training 
* 9 separate images for validation 
* 5 separate images for prediction

Used: 
* C++(17++)
* Libtorch(1.11)
* OpenCV(4.6.0) 
* CMake(3.23.2)

The code is written in C++, so you need a C++ pytorch distribution, OpenCV, CMake, dirent interface to be able to run this project, you can find the steps to install all this in the previous projects I posted. \
The UNET architecture looks like as follows:
![image](https://user-images.githubusercontent.com/96078343/179245823-a344998c-5ccd-44fc-b584-9db8d83ecbb2.png)
\
<br>Sample code</br>
<pre>
conv1 = torch::nn::Conv2d(torch::nn::Conv2dOptions(1, 16, 3).padding({1,1}));
batch1 = torch::nn::BatchNorm2d(16);
conv2 = torch::nn::Conv2d(torch::nn::Conv2dOptions(16, 16, 3).padding({ 1,1 }));
batch2 = torch::nn::BatchNorm2d(16);
</pre>
This are just the two convolution layers, there ReLU follows and maxpooling for the encoder and decoder has this structure plus upsampling
<pre>
upConv1 = torch::nn::ConvTranspose2d(torch::nn::ConvTranspose2dOptions(256, 128, 2).stride(2));
</pre>
In the decoder this output will be combined with the output of the corresponding encoder after ReLU.

Network Parameters:
* Rectifier Linear Unit
* Sigmoid on the output
* Adam Optimizer 
* Binary CrossEntropy Loss
* Maxpooling

Lastly, prediction were made by loading the saved model :\
![image](https://user-images.githubusercontent.com/96078343/179247013-a7308a32-fdef-4475-b23e-90836531e362.png)
![image](https://user-images.githubusercontent.com/96078343/179247034-6a12f929-29d7-4968-97cd-bd8971579827.png)
<font face="Arial">Thank you for visiting!</font>
