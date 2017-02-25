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


###3.Docker Image Best Practices
```
docker commit containername imagename
```

##4. Installing a Private (And Free) Docker Registry
```
firewall-cmd --zone=public --add-port=5000/tcp
firewall-cmd --zone=public --add-port=5000/tcp --permanent
```

then
```
docker pull registry:latest
```


```
docker run -p 5000:5000
```
###3 Installing and Using Docker Resistry: The Package Method
```
apt install docker-registry
```
but might have some issue. Here
```
wget http://http.us.debian.org/debian/pool/main/d/docker-gegistr/docker-registry_2..1-ds1-2_am64.deb
dpkg -i
```

```
docke rmi -f hello-world localhost:5000/hello-world:latest
```

###3. Docker Images Storage
```
cd /var/lib/docker-registry/docker/registry/v2/repositories
```

container volume
```
/var/lib/docker/volumes/ccccc121c/_data/docker/registry/v2/repositories/hello-world
```

```
docker volume create myvolume
```
## 5. Securing Your Images in Transit
###2 
```
docker run -d -p 5000:5000 --restart=always --name registry -v `pwd` /certs:/certs -e REGISTRY_HTTP_TLS_CERTIFICATE=/certs/stuff.crt
-e REGISTRY_HTTP_TLS_KEY=/certs/stuff.key registry
```
Dockerfile
```
FROM registry
ADD /certs/ /home/
ENV REGISTRY_HTTP_TLS_CERTIFICATE=/certs/stuff.crt REGISTRY_HTTP_TLS_KEY=/certs/stuff.key
EXPOSE 5000
```

```
vim /etc/docker/registry/config.yml
```
edit
```
http:
  addr: :5000
  tls:
    certificate: /home/ubuntu/certs/stuff.crt
    key: ...key
  headers:
    X-Content-Type-Options: [nosiniff]
  
```
