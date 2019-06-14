FROM registry.cn-hangzhou.aliyuncs.com/camsgear/python:2.7.15-alpine3.6

# MAINTAINER edwin.cen@camsgear.com

# 使用国内镜像
RUN echo -e "\n@testing http://nl.alpinelinux.org/alpine/edge/testing" >> /etc/apk/repositories

RUN apk update
RUN apk add --update --no-cache \
  # --virtual .build-deps \
      build-base \
      openblas-dev \
      unzip \
      wget \
      cmake \

      #Intel® TBB, a widely used C++ template library for task parallelism'
      libtbb@testing  \
      libtbb-dev@testing   \

      # Wrapper for libjpeg-turbo
      libjpeg  \

      # accelerated baseline JPEG compression and decompression library
      libjpeg-turbo-dev \

      # Portable Network Graphics library
      libpng-dev \

      # A software-based implementation of the codec specified in the emerging JPEG-2000 Part-1 standard (development files)
      jasper-dev \

      # Provides support for the Tag Image File Format or TIFF (development files)
      tiff-dev \

      # Libraries for working with WebP images (development files)
      libwebp-dev \

      # A C language family front-end for LLVM (development files)
      clang-dev \

      linux-headers

#安装python依赖
RUN pip install numpy

ENV CC /usr/bin/clang
ENV CXX /usr/bin/clang++

RUN mkdir /opt && cd /opt && \
  wget https://github.com/opencv/opencv/archive/2.4.13.6.zip && \
  unzip 2.4.13.6.zip && \
  cd /opt/opencv-2.4.13.6 && \
  mkdir build && \
  cd build && \
  cmake -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr/local -D WITH_FFMPEG=NO \
  -D WITH_IPP=NO -D WITH_OPENEXR=NO .. && \
  make VERBOSE=1 && \
  make && \
  make install && \
  rm -rf /opt/*

RUN  rm -rf /var/cache/apk/*