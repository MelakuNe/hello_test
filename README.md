# VCV-CPP
<h2>Deep learning models with cpp at VeinCV</h2>
<h3>Title: Binary Classification of Images using Pytorch C++ </h3>

This project is about binary classification of an image, I am using image of cats and dogs, you can find the full dataset
at https://www.kaggle.com/c/dogs-vs-cats or https://www.microsoft.com/en-us/download/confirmation.aspx?id=54765 .
It has total of 25000 images(12500 each), but I used only small amount of it.
*	60 images for training (30 each)
*	16 separate images for validation (8 each)
*	20 separate images for inference (10 each)

To deal with processing of the files inside directory I used an interface called <b>'dirent.h'</b> which I came across lately. It is a good
one I recommend using it for other projects too. For window users it requires a little integration, you can find the 
download link and brief explanation of steps in the link https://github.com/tronkko/dirent.
 for UNIX, it exists as a standard library, I think!

Used: C++(17++), Libtorch(1.11), OpenCV(4.6.0), CMake(3.23.2)

The code is written in C++, so you need a C++ pytorch distribution, OpenCV, CMake to be able to run this project, you can find the steps on installing all this in the 
previous project I posted. 
The model architecture looks like as follows
![image](https://user-images.githubusercontent.com/96078343/177979924-4f9872c2-4093-4f85-bda4-ef7acb2e9b31.png)

<pre>
		conv1 = torch::nn::Conv2d(torch::nn::Conv2dOptions(3, 32, 3).stride(2));
		batch_norm1 = torch::nn::BatchNorm2d(32);
		conv2 = torch::nn::Conv2d(torch::nn::Conv2dOptions(32, 64, 3).stride(2));
		batch_norm2 = torch::nn::BatchNorm2d(64);

		auto size = get_size(channel, height, width);

		fc1 = torch::nn::Linear(size, 50);
		fc2 = torch::nn::Linear(50, 1);
endif (MSVC)
</pre>
<font face="Arial">Thank you for visiting.</font>
