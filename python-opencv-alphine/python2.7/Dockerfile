FROM python:2.7.15-alpine3.6

MAINTAINER edwin.cen@camsgear.com

# 使用国内镜像
RUN echo -e "http://mirrors.aliyun.com/alpine/v3.6/main\nhttp://mirrors.aliyun.com/alpine/v3.6/community" > /etc/apk/repositories

#修正时区
ARG TIME_ZONE='Asia/Shanghai'
RUN apk update && \
    apk --no-cache add tzdata && \
    cp /usr/share/zoneinfo/$TIME_ZONE /etc/localtime && \
    echo $TIME_ZONE > /etc/timezone && \
    apk del tzdata && \
    rm -rf /var/cache/apk/*

#修改国内源
RUN mkdir ~/.pip && \
    touch ~/.pip/pip.conf && \
    echo -e "[global]\nindex-url = https://mirrors.aliyun.com/pypi/simple/\n[install]\ntrusted-host = mirrors.aliyun.com" >> ~/.pip/pip.conf && \
    pip install --upgrade pip