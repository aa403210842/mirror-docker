# lts
```bash
docker build -t registry.cn-hangzhou.aliyuncs.com/icamdora/nodejs:lts -f Dockerfile .
```

# onbuild
```bash
docker build -t registry.cn-hangzhou.aliyuncs.com/icamdora/nodejs:onbuild -f Dockerfile-onbuild .
```

# git-onbuild
```bash
docker build -t registry.cn-hangzhou.aliyuncs.com/icamdora/nodejs:git-onbuild -f Dockerfile-git-onbuild .
```

# icu-onbuild
```bash
docker build -t registry.cn-hangzhou.aliyuncs.com/icamdora/nodejs:icu-onbuild -f Dockerfile-icu-onbuild .
```

# libxmljs-onbuild
```bash
docker build -t registry.cn-hangzhou.aliyuncs.com/icamdora/nodejs:libxmljs-onbuild -f Dockerfile-libxmljs-onbuild .
```

# 测试
```
docker run -d --name test -p 3000:3000 registry.cn-hangzhou.aliyuncs.comi/cadorar/nodejs:onbuild
```