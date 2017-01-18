FROM nvidia/cuda:7.5-cudnn5-runtime-ubuntu14.04
LABEL maintainer "NVIDIA CORPORATION <cudatools@nvidia.com>"

ENV CAFFE_VERSION 0.15
LABEL com.nvidia.caffe.version="0.15"

ENV CAFFE_PKG_VERSION 0.15.13-1+cuda7.5
RUN apt-get update && apt-get install -y --no-install-recommends \
        caffe-nv=$CAFFE_PKG_VERSION \
        caffe-nv-tools=$CAFFE_PKG_VERSION \
        python-caffe-nv=$CAFFE_PKG_VERSION \
        libcaffe-nv0=$CAFFE_PKG_VERSION && \
    rm -rf /var/lib/apt/lists/*