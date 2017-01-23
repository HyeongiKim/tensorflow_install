#Tensorflow Installation Guide

for Ubuntu 16.04 64bit, GTX 970

17.01.23

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
