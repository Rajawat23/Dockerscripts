FROM nvidia/cuda:10.2-cudnn7-runtime-ubuntu18.04

# ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && \
	apt-get install -y \
		curl \
		bzip2 \
		libfreetype6 \
		libgl1-mesa-dev \
		libglu1-mesa \
		libxi6 \
		libxrender1 && \
	apt-get -y autoremove && \
	rm -rf /var/lib/apt/lists/*

ARG DISPLAY=:0
ARG LANG=en_US.UTF-8

ENV DISPLAY $DISPLAY
RUN apt-get update -y && apt-get install -y --no-install-recommends \
		apt xz-utils unzip avahi-utils dbus \
		xserver-xorg-core libgl1-mesa-glx libgl1-mesa-dri libglu1-mesa xfonts-base \
		x11-session-utils x11-utils x11-xfs-utils x11-xserver-utils xauth x11-common

# RUN add-apt-repository ppa:xorg-edgers/ppa

# RUN apt-get update

RUN apt-get install -y xorg-dev

RUN apt-get install xorg -y

# RUN nvidia-xconfig --busid=PCI:0:6:0 --use-display-device=none --virtual=1280x1024
# RUN Xorg :1

ENV BLENDER_MAJOR 2.78
ENV BLENDER_VERSION 2.78c
ENV BLENDER_BZ2_URL http://mirror.cs.umn.edu/blender.org/release/Blender$BLENDER_MAJOR/blender-$BLENDER_VERSION-linux-glibc219-x86_64.tar.bz2

RUN export DISPLAY=:1

RUN mkdir /usr/local/blender && \
	curl -SL "$BLENDER_BZ2_URL" -o blender.tar.bz2 && \
	tar -jxvf blender.tar.bz2 -C /usr/local/blender --strip-components=1 && \
	rm blender.tar.bz2
ENV PATH /usr/local/blender:$PATH