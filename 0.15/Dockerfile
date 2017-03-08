FROM nvidia/cuda:8.0-cudnn5-runtime-ubuntu14.04
LABEL maintainer "NVIDIA CORPORATION <cudatools@nvidia.com>"

ENV CAFFE_VERSION 0.15
LABEL com.nvidia.caffe.version="0.15"

ENV CAFFE_PKG_VERSION 0.15.13-3ubuntu14.04+cuda8.0
RUN apt-get update && apt-get install -y --no-install-recommends \
        caffe-nv=$CAFFE_PKG_VERSION \
        caffe-nv-tools=$CAFFE_PKG_VERSION \
        python-caffe-nv=$CAFFE_PKG_VERSION \
        libcaffe-nv0=$CAFFE_PKG_VERSION && \
    rm -rf /var/lib/apt/lists/*  && \ 
    
    mkdir opencv_compile  && \ 
cd opencv_compile  && \ 
wget -O opencv.zip https://github.com/Itseez/opencv/archive/3.1.0.zip  && \ 
wget -O opencv_contrib.zip https://github.com/Itseez/opencv_contrib/archive/3.1.0.zip  && \ 
unzip opencv.zip  && \ 
unzip opencv_contrib.zip  && \ 
cd opencv-3.1.0  && \ 
mkdir build  && \ 
cd build && \ 
cmake -D CMAKE_BUILD_TYPE=RELEASE \ 
    -D CMAKE_INSTALL_PREFIX=/usr/local \
    -D WITH_CUDA=ON \
    -D ENABLE_FAST_MATH=1 \
    -D CUDA_FAST_MATH=1 \
    -D WITH_CUBLAS=1 \
    -D INSTALL_PYTHON_EXAMPLES=ON \
    -D OPENCV_EXTRA_MODULES_PATH=../../opencv_contrib-3.1.0/modules \
    -D BUILD_EXAMPLES=ON .. && \
make -j8  && \ 
sudo make install 

