FROM python:2.7.15-alpine3.6

MAINTAINER edwin.cen@camsgear.com

# 使用国内镜像
RUN echo -e "http://mirrors.aliyun.com/alpine/v3.6/main\n\
http://mirrors.aliyun.com/alpine/v3.6/community" > /etc/apk/repositories

RUN apk update && apk upgrade

#修正时区
RUN apk add tzdata && \
    cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime && \
    echo "Asia/Shanghai" >  /etc/timezone && \
    apk del tzdata

#修改国内源
RUN mkdir ~/.pip
RUN touch ~/.pip/pip.conf
RUN echo "[global]\n\
          trusted-host = mirrors.aliyun.com\n\
          index-url = http://mirrors.aliyun.com/pypi/simple" >> ~/.pip/pip.conf
RUN pip install --upgrade pip