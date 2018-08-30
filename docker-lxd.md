# Docker in lxd

### Start an lxd container supporting Docker
```
lxc launch ubuntu:18.04 docker-alfa -c security.nesting=true
Creating docker-alfa
Starting docker-alfa
```

### Install Docker in the Container

1. `apt-get update`
2.  Install Common packages
```
apt-get install \
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

```
