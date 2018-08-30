# LXD Experiments
Here I just want to play with LXD (Machine Containers) to understand the possible and identify use cases.
[Getting Started Guide](https://tutorials.ubuntu.com/tutorial/tutorial-setting-up-lxd-1604#0)

### Installing

My daily system is Ubuntu so all instructions based on it.

```
sudo apt update
sudo apt install lxd zfsutils-linux
sudo adduser $USER lxd
newgrp lxd
```

### Initialize lxd
Run `lxd init` and follow instructions. See  [Getting Started Guide](https://tutorials.ubuntu.com/tutorial/tutorial-setting-up-lxd-1604#0)

### Launching and list test container
```
lxc launch ubuntu:18.04 alfa
Creating alfa
Starting alfa
+--------------+---------+----------------------+------+------------+-----------+
|     NAME     |  STATE  |         IPV4         | IPV6 |    TYPE    | SNAPSHOTS |
+--------------+---------+----------------------+------+------------+-----------+
| alfa         | RUNNING | 10.81.226.98 (eth0)  |      | PERSISTENT | 0         |
+--------------+---------+----------------------+------+------------+-----------+
```
