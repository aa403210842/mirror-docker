# 指定我们的基础镜像是node
FROM node:10.15-alpine

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

# 更新 npm国内taobao源
RUN npm config set registry https://registry.npm.taobao.org && \
    npm config set disturl https://npm.taobao.org/mirrors/node/

# 容器启动时执行的命令，类似npm run start
CMD ["node", "--version"]