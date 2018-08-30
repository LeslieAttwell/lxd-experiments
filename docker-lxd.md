# Docker in LXD

### Start an LXD container supporting Docker
```
lxc launch ubuntu:18.04 docker-alfa -c security.nesting=true
Creating docker-alfa
Starting docker-alfa
```

### Install Docker in the Container

1. `apt-get update`
2.  Install Common packages
```
apt-get install -y \
apt-transport-https \
ca-certificates \
curl \
software-properties-common
```
3. Add Docker Repository
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add - \
&& apt-key fingerprint 0EBFCD88

add-apt-repository \
"deb [arch=amd64] https://download.docker.com/linux/ubuntu \
$(lsb_release -cs) \
stable"
```
4. Install Docker CE
```
apt-get update \
&& apt-get install docker-ce -y
```

### Test Docker in 
1. Running hello-world
```
docker run hello-world
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
9db2ca6ccae0: Pull complete 
Digest: sha256:4b8ff392a12ed9ea17784bd3c9a8b1fa3299cac44aca35a85c90c5e3c7afacdc
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

    To try something more ambitious, you can run an Ubuntu container with:
    $ docker run -it ubuntu bash

    Share images, automate workflows, and more with a free Docker ID:
    https://hub.docker.com/

    For more examples and ideas, visit:
    https://docs.docker.com/engine/userguide/
```
2. Run alpine test container
```
docker run -it --rm alpine sh
Unable to find image 'alpine:latest' locally
latest: Pulling from library/alpine
8e3ba11ec2a2: Pull complete
Digest: sha256:7043076348bf5040220df6ad703798fd8593a0918d06d3ce30c6c93be117e430
Status: Downloaded newer image for alpine:latest
/ # hostname
602a3cc02e0d
/ # 
```
