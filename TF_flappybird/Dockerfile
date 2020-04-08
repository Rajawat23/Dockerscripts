# cuda 10.2 compatible docker

FROM nvidia/cuda:10.2-cudnn7-runtime-ubuntu18.04

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update
RUN apt-get install -y software-properties-common

RUN add-apt-repository ppa:deadsnakes/ppa
RUN apt-get update
RUN apt-get install -y git xvfb ffmpeg python-opencv python3.6 python3-pip python3.6-dev unzip wget

# make python 3.6 the default version
RUN rm /usr/bin/python3
RUN rm /usr/bin/python
RUN ln -s /usr/bin/python3.6 /usr/bin/python3
RUN ln -s /usr/bin/python3.6 /usr/bin/python

# upgrade pip
RUN python -m pip install --upgrade pip

RUN apt-get -y install cmake libz-dev

RUN apt-get update \
&& apt-get install -y --no-install-recommends git \
&& apt-get purge -y --auto-remove \
&& rm -rf /var/lib/apt/lists/

RUN pip install cmake
RUN pip install setuptools==41.0.0
RUN pip install gym==0.10.3
RUN pip install numpy==1.18.2
RUN pip install tensorflow-gpu==1.15.0
RUN pip install keras==2.2.4
RUN pip install opencv-python==3.4.2.17
RUN pip install atari-py==0.1.1
RUN pip install pygame==1.9.6
RUN pip install wandb

# Get pygame env git repo
RUN git clone https://github.com/ntasfi/PyGame-Learning-Environment.git

# install dependency from setup file
RUN pip install -e /PyGame-Learning-Environment

RUN pip install gym_ple
