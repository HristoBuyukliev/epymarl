# FROM nvidia/cuda:9.2-cudnn7-devel-ubuntu16.04
FROM nvcr.io/nvidia/pytorch:23.01-py3

# # CUDA includes
# ENV CUDA_PATH /usr/local/cuda
# ENV CUDA_INCLUDE_PATH /usr/local/cuda/include
# ENV CUDA_LIBRARY_PATH /usr/local/cuda/lib64

# Ubuntu Packages
RUN apt-get update -y && \
    apt-get install -y nano vim man build-essential wget sudo tmux
    
# Install curl and other dependencies
RUN apt-get update -y && apt-get install -y curl libssl-dev openssl libopenblas-dev \
    libhdf5-dev hdf5-helpers hdf5-tools libhdf5-serial-dev libprotobuf-dev protobuf-compiler git
# RUN curl -sk https://raw.githubusercontent.com/torch/distro/master/install-deps | bash && \
#     rm -rf /var/lib/apt/lists/*

# # Install python3 pip3
# RUN apt-get update
# RUN apt-get -y install python3
# RUN apt-get -y install python3-pip
# RUN pip3 install --upgrade pip

# # Python packages we use (or used at one point...)
# RUN pip3 install numpy scipy pyyaml matplotlib
# RUN pip3 install imageio
# RUN pip3 install tensorboard-logger
# RUN pip3 install pygame

RUN pip install pygame pyyaml imageio einops tensorboard-logger

RUN mkdir /install
WORKDIR /install

RUN pip install jsonpickle==0.9.6
# install Sacred (from OxWhirl fork)
RUN pip install setuptools
RUN git clone https://github.com/oxwhirl/sacred.git /install/sacred && cd /install/sacred && python3 setup.py install

#### -------------------------------------------------------------------
#### install pytorch
#### -------------------------------------------------------------------
RUN pip install torchvision snakeviz pytest probscale

## -- SMAC
RUN pip install git+https://github.com/oxwhirl/smac.git
ENV SC2PATH /pymarl/3rdparty/StarCraftII

WORKDIR /pymarl
