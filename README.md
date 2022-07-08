# VCV-CPP
<h2>Deep Learning Model with C++ at VeinCV</h2>
<h3>Title: Binary Classification of Images using Pytorch C++ </h3>

This project is about binary classification of an image, I am using image of cats and dogs, you can find the full dataset
in the following link https://www.kaggle.com/c/dogs-vs-cats or https://www.microsoft.com/en-us/download/confirmation.aspx?id=54765 .
It has total of 25000 images(12500 each), but I used only some of it.
*	60 images for training (30 each)
*	16 separate images for validation (8 each)
*	20 separate images for inference (10 each)

To deal with processing of the files inside directory I used an interface called <b>'dirent.h'</b> which I came across lately. It is good and simple to use, 
I recommend using it for other projects too. For window users it requires a little integration, you can find the 
download link and brief explanation of steps in the link https://github.com/tronkko/dirent. For UNIX, it exists as a standard library, I think!

Used: 
* C++(17++)
* Libtorch(1.11)
* OpenCV(4.6.0) 
* CMake(3.23.2)

The code is written in C++, so you need a C++ pytorch distribution, OpenCV, CMake to be able to run this project, you can find the steps to install all this in the 
previous project I posted. \
The model architecture looks like as follows:
![image](https://user-images.githubusercontent.com/96078343/177979924-4f9872c2-4093-4f85-bda4-ef7acb2e9b31.png)

<pre>
conv1 = torch::nn::Conv2d(torch::nn::Conv2dOptions(3, 32, 3).stride(2));
batch_norm1 = torch::nn::BatchNorm2d(32);
conv2 = torch::nn::Conv2d(torch::nn::Conv2dOptions(32, 64, 3).stride(2));
batch_norm2 = torch::nn::BatchNorm2d(64);

auto size = get_size(channel, height, width);

fc1 = torch::nn::Linear(size, 50);
fc2 = torch::nn::Linear(50, 1);
</pre>

Network Parameters:
* Rectifier Linear Unit
* Sigmoid on the output
* Adam Optimizer 
* Binary CrossEntropy Loss

Lastly, prediction using the inference dataset were made by loading the saved model :\
 ![image](https://user-images.githubusercontent.com/96078343/177985159-74046333-079b-4dd6-8af2-0eab32be1cc8.png)
![image](https://user-images.githubusercontent.com/96078343/177985521-1f078b59-3a76-4a5c-a061-189a11a2b458.png)


<font face="Arial">Thank you for visiting!</font>
