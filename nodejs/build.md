# onbuild
```bash
docker build -t registry.cn-hangzhou.aliyuncs.com/camsgear/nodejs:onbuild -f Dockerfile .
```

# git-onbuild
```bash
docker build -t registry.cn-hangzhou.aliyuncs.com/camsgear/nodejs:git-onbuild -f Dockerfile-git-onbuild .
```

# icu-onbuild
```bash
docker build -t registry.cn-hangzhou.aliyuncs.com/camsgear/nodejs:icu-onbuild -f Dockerfile-icu-onbuild .
```

# canvas-onbuild
```bash
docker build -t registry.cn-hangzhou.aliyuncs.com/camsgear/nodejs:canvas-onbuild -f Dockerfile-canvas-onbuild .
```

# 测试
```
docker run -d --name test -p 3000:3000 registry.cn-hangzhou.aliyuncs.com/camsgear/nodejs:onbuild
```