#Tensorflow Installation Guide

for Ubuntu 16.04 64bit, GTX 970

17.01.23

##Reference

1. http://luke77.tistory.com/44

2. https://github.com/tensorflow/tensorflow/blob/master/tensorflow/g3doc/get_started/os_setup.md#test-the-tensorflow-installation

###Graphic driver update

    sudo add-apt-repository ppa:graphics-drivers/ppa 
    sudo apt update

System settings>Software&Updates>Additional Drivers tab

Re-boot

###Anaconda

Go to https://www.continuum.io/downloads

Downloads 'Anaconda for Linux Python 2.7 Linux 64-bit'

    bash Anaconda2-4.1.1-Linux-x86_64.sh

Reboot terminal

Test as python> import matplotlib

###CUDA Toolkit

Go to https://developer.nvidia.com/cuda-downloads (for Linux runfile(local))

Install additional packages

    sudo apt-get install nvidia-modprobe freeglut3-dev libx11-dev libxmu-dev libxi-dev libglu1-mesa-dev

Install CUDA

- EULA 동의 : accept
- You are attempting to install on an unsupported configuration. Do you with to continue? : yes
- Install NVIDIA Accelerated Graphics Driver for Linux-x86_64 352.39 ? no (이미 설치했음)
    - Install the CUDA 7.5 Toolkit? yes
    - Enter Toolkit Location : Enter (default)
    - Do you want to install a symbolic link at /usr/local/cuda ? yes
    - Install the CUDA 7.5 Samples? no
    - Enter CUDA Samples Location : Enter (default)

- Move to home (cd ~)

    vi ~/.bashrc
    export LD_LIBRARY_PATH="$LD_LIBRARY_PATH:/usr/local/cuda/lib64"
    export CUDA_HOME=/usr/local/cuda

### CUDNN

Go to https://developer.nvidia.com/cudnn 

- Move to

    sudo nautilus

- copy files cuda/include

- copy files cuda/lib64

- setup

    sudo chmod a+r /usr/local/cuda/lib64/libcudnn*

###Tensorflow

1. Numpy

    sudo apt-get install python-numpy swig python-dev

2. Tensorflow

    git clone --recurse-submodules https://github.com/tensorflow/tensorflow

    cd ~/tensorflow
    ./configure

    Please specify the location of python. - Enter (default)
    
    Do you with to build TensorFlow with Google Cloud Platform support? N
    
    Do you wish to build TensorFlow with GPU support? y
    
    Please specify which gcc should be used by nvcc as the host complier. : /usr/bin/gcc-4.8
    
    Please specify the Cuda SDK version you want to use: 7.5
    
    Please specify the location where CUDA 7.5 toolkit is installed. Refer to README.md for more details. : Enter (default)
    
    Please specify the Cudnn version you want to use. : 4
    
    Please specify the location where cuDNN 4.0 library is installed. Refer to README.md for more details. : Enter (default)
    
    Please note that each additional compute capability significantly increases your build time and binary size. : 3.5

- install tensorflow to python

#### Ubuntu/Linux 64-bit, GPU enabled, Python 2.7
#### Requires CUDA toolkit 8.0 and CuDNN v5.1. For other versions, see "Installing from sources" below.
    
    $ export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/linux/gpu/tensorflow_gpu-0.12.1-cp27-none-linux_x86_64.whl

    $ pip install --upgrade $TF_BINARY_URL
