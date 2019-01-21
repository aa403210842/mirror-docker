# 6-onbuild
```bash
docker build -t registry.cn-hangzhou.aliyuncs.com/camsgear/nodejs:6-onbuild -f Dockerfile-6-onbuild .
```

# 8-onbuild
```bash
docker build -t registry.cn-hangzhou.aliyuncs.com/camsgear/nodejs:8-onbuild -f Dockerfile-8-onbuild .
```

# 8-icu-onbuild
```bash
docker build -t registry.cn-hangzhou.aliyuncs.com/camsgear/nodejs:8-icu-onbuild -f Dockerfile-8-icu-onbuild .

# 10-onbuild
```bash
docker build -t registry.cn-hangzhou.aliyuncs.com/camsgear/nodejs:10-onbuild -f Dockerfile-10-onbuild .
```

# 11-onbuild
```bash
docker build -t registry.cn-hangzhou.aliyuncs.com/camsgear/nodejs:11-onbuild -f Dockerfile-11-onbuild .
```

# 测试
```
docker run -d --name test -p 3000:3000 registry.cn-hangzhou.aliyuncs.com/camsgear/nodejs:8-onbuild
```