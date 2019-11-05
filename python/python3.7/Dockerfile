FROM python:3.7.5-alpine

MAINTAINER edwin.cen@camsgear.com

# 更新 apk国内源
RUN sed -i -e "s/dl-cdn.alpinelinux.org/mirrors.aliyun.com/" -e "s/http:/https:/" /etc/apk/repositories

# 更新 中国时区
# LANG=zh_CN.UTF-8
ARG TIME_ZONE='Asia/Shanghai'
RUN apk update && \
    apk add --no-cache tzdata && \
    cp /usr/share/zoneinfo/$TIME_ZONE /etc/localtime && \
    echo $TIME_ZONE > /etc/timezone && \
    apk del tzdata && \
    rm -rf /var/cache/apk/*

#修改国内源
RUN mkdir ~/.pip && \
    touch ~/.pip/pip.conf && \
    echo -e "[global]\nindex-url = https://mirrors.aliyun.com/pypi/simple/\n[install]\ntrusted-host = mirrors.aliyun.com" >> ~/.pip/pip.conf && \
    pip install --upgrade pip