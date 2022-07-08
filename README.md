# VCV-CPP
<h2>Deep learning models with cpp at VeinCV</h2>
<h3>Title: Binary Classification of Images using Pytorch C++ </h3>

This project is about binary classification of an image, I am using image of cats and dogs, you can find the full dataset
at https://www.kaggle.com/c/dogs-vs-cats or https://www.microsoft.com/en-us/download/confirmation.aspx?id=54765 .
It has total of 25000 images(12500 each), but I used only small amount of it.
*	60 images for training (30 each)
*	16 separate images for validation (8 each)
*	20 separate images for inference (10 each)

To deal with processing of the images inside directory I used an interface caleed <b>'dirent.h'</b> which I came across lately. It is a good
one I recommend using it for other projects too. For window users it requires a little integration, you can find the 
download link and brief explanation of steps in the link https://github.com/tronkko/dirent.
 for UNIX, it exists as a standard library, I think!

Used: C++(17++), Libtorch(1.11), OpenCV(4.6.0), CMake(3.23.2)

The code is written in C++, so you need a C++ pytorch distribution, OpenCV, CMake to be able to run this project, you can find the steps on installing all this in the 
previous project I posted. 

<pre>
cmake_minimum_required (VERSION 3.8)

find_package(OpenCV REQUIRED)
find_package(Torch REQUIRED)
include_directories(${OpenCV_INCLUDE_DIRS})

add_executable (TorchOpenCV "TorchOpenCV.cpp" "TorchOpenCV.h")
target_link_libraries(TorchOpenCV "${TORCH_LIBRARIES}")
target_link_libraries(TorchOpenCV "${OpenCV_LIBS}")

if (MSVC)
  file(GLOB TORCH_DLLS "${TORCH_INSTALL_PREFIX}/lib/*.dll")
  add_custom_command(TARGET TorchOpenCV
                     POST_BUILD
                     COMMAND ${CMAKE_COMMAND} -E copy_if_different
                     ${TORCH_DLLS}
                     $<TARGET_FILE_DIR:TorchOpenCV>)
endif (MSVC)
</pre>
By now you must have torch and OpenCV in your visual studio.\
<font face="Arial">Incase of any confusion refer the file Requirements.txt there are some video links attached for setting up the environment.</font>
