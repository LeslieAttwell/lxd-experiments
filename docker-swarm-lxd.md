# Docker Swarm Cluster on LXD

### Installing Docker Swarm Cluster
1. Build first 3x System containers. [Guide](docker-lxd.md)
```
lxc launch ubuntu:18.04 docker-alfa -c security.nesting=true
lxc launch ubuntu:18.04 docker-bravo -c security.nesting=true
lxc launch ubuntu:18.04 docker-charlie -c security.nesting=true
```



[Guide](docker-lxd.md)


p
