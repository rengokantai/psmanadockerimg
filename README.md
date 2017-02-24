# psmanadockerimg
```
#!/bin/bash
apt update && apt install -y apt-transport-https ca-certificates && apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D
echo "deb https://apt.dockerproject.org/repo ubuntu-xenial main" > /etc/apt/sources.list.d/docker.list && apt update && apt install -y linux-image-extra-$(uname -r) linux-image-extra-virtual && apt update && apt install -y docker-engine
```


###2. A Survey
```
cd /var/lib/docker
```

## 3.Managing Image Using Docker Hub
###2 Buliding and Pushing Images
tag build from Dockerfile
```
docker -t tagname .
```
build image to customized tag
```
docker tag imagename rengokantai/new
```
```
docker network inspect bridge
```
