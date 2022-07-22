# VCV-CPP
<h2>Deep Learning Model with C++ at VeinCV</h2>
<h3>Title: Running on Linux </h3>
So far I have been demostrating different projects using Pytorch C++ and the operating system I was running it on is Windows. In todays report I will show how to do the same thing in Linux operating system. I am using Windows as a host and Ubuntu 22.04 LTS as a guest through virtualbox.

<br>Requirements:</br> 
* C++
* Libtorch
* OpenCV 
* CMake
* Dirent (we don't need external installation as for Windows, it is available for Linux)

The project is done with cmake, because it is the best tool availalble to work with the Pytorch distribution and OpenCV and others.
So, let's see how we can havel all this tools in our system. \
Let's start from installing OpenCV, I will just provide you the link for the installation because it is very long and explaining it here is useless. In the following link you will find detailed procedures of the installation. http://techawarey.com/programming/install-opencv-c-c-in-ubuntu-18-04-lts-step-by-step-guide/, this one has backup I used this. Alos in the official documentation page you can find it https://docs.opencv.org/3.4/d7/d9f/tutorial_linux_install.html.

If you have followed all steps in the link provided, you should have by now OpenCV in your Linux system whatever distribution you are using. Before moving on to the next step, check its version if it is installed properly. 
<pre>$ pkg-config --modversion opencv</pre>
if this command prompt package opencv not found, try the following and it will be fixed if you have followed everything exactly.
<pre>
$ apt-file search opencv.pc  or apt-file search opencv4.pc
$ ls /usr/local/lib/pkgconfig/
$ sudo cp /usr/local/lib/pkgconfig/opencv4.pc  /usr/lib/x86_64-linux-gnu/pkgconfig/opencv.pc
$ pkg-config --modversion opencv
</pre>
Alright! now we have OpenCV installed in out system globally, the next step is to install Pytorch distribution of C++, and thanks to cmake it is very easy. Download the compatable type of libtorch to you system from https://pytorch.org/get-started/locally/ then extract the folder. I will show you how to do it easily or you can follow the officail webpage https://pytorch.org/tutorials/advanced/cpp_frontend.html. You just need to create the following CMakeLists.txt file.
<pre>
cmake_minimum_required(VERSION 3.0 FATAL_ERROR)
project(CppPytorch) # CppPytorch is the name of the project(you can change it as you want)
set(CMAKE_PREFIX_PATH /home/melie/Downloads/libtorch) # This is the path of the libtorch you just downloaded  
find_package(Torch REQUIRED)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${TORCH_CXX_FLAGS}")
add_executable(${PROJECT_NAME} main.cpp)
target_link_libraries(${PROJECT_NAME} "${TORCH_LIBRARIES}")
set_property(TARGET ${PROJECT_NAME} PROPERTY CXX_STANDARD 14)
</pre>
Good! now we have Pytorch in C++. But still we may want to have both torch and opencv at the same time, easy! just add the following two line into the cmake file and then you are good to go. Here there is no need to set the path of opencv because it is installed globally, not in local folder.
<pre>
find_package(OpenCV REQUIRED)
target_link_libraries(${PROJECT_NAME} "${OpenCV_LIBS}")
</pre>
In general the structure looks like as follows, first create the folder build and cmake, main and other files.
<pre>
build 
main.cpp
CMakeLists.txt
</pre>
then to build it execute the following two commands in the build directory.
<pre>
cmake ..
make
</pre>
and to run it also inside build directory: 
<pre>
./CppPytorch
</pre>
The structure of the two project I pushed are the same as the above one just only their name is different.\
<br>Edge Detection</br>
<pre>
cmake ..
make
./edge
</pre>
![image](https://user-images.githubusercontent.com/96078343/180441591-91d21aaf-7e7a-425a-80bc-2ea5df9ae562.png)
<br>Classification</br>
<pre>
cmake ..
make
./classification
</pre>
![image](https://user-images.githubusercontent.com/96078343/180442185-52d666a8-236b-4e53-852b-1248a8e27553.png)
I used the same code I pushed before. However, I have observed some strange things when I run this projects on Ubuntu.\
1. The first thing is the size of build file: when I run it on Windows Visual Studio IDE its size was morethan 1 GB, wheras on Ubuntu Visual Studio Code it is less than 10 MB. This is amazing, because last time I couldn't push the whole project to the github because of the size so I had to remove some file from the build directory. But now everything is pushed so you can just clone and run it easily.
2. The second thing is the speed, still it is CPU I don't have GPU but during training the speed is so good on Ubuntu.

<br>I think that is all, thank you so much</br>
