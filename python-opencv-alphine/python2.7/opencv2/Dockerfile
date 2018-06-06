FROM python:2.7.15-alpine3.6

MAINTAINER edwin.cen@camsgear.com

# 使用国内镜像
RUN echo -e "http://mirrors.aliyun.com/alpine/v3.6/main\n\
http://mirrors.aliyun.com/alpine/v3.6/community\n\
@testing http://nl.alpinelinux.org/alpine/edge/testing" > /etc/apk/repositories

RUN apk update && apk upgrade

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

RUN mkdir ~/.pip
RUN touch ~/.pip/pip.conf
RUN echo "[global]" >> ~/.pip/pip.conf
RUN echo "trusted-host = mirrors.aliyun.com" >> ~/.pip/pip.conf
RUN echo "index-url = http://mirrors.aliyun.com/pypi/simple" >> ~/.pip/pip.conf
RUN pip install --upgrade pip
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
  make install

RUN apk add tzdata && \
    cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime && \
    echo "Asia/Shanghai" >  /etc/timezone && \
    apk del tzdata

RUN rm -rf /var/cache/apk/*
RUN rm -rf /opt/*