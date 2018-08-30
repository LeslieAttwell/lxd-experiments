# Docker Swarm Cluster on LXD

### Preparing Cluster
1. Build first 3x System containers as per this [guide](docker-lxd.md).
```
lxc launch ubuntu:18.04 docker-alfa -c security.nesting=true
lxc launch ubuntu:18.04 docker-bravo -c security.nesting=true
lxc launch ubuntu:18.04 docker-charlie -c security.nesting=true
Creating docker-alfa
Starting docker-alfa
Creating docker-bravo
Starting docker-bravo
Creating docker-charlie
Starting docker-charlie

lxc list
+----------------+---------+----------------------+------+------------+-----------+
|      NAME      |  STATE  |         IPV4         | IPV6 |    TYPE    | SNAPSHOTS |
+----------------+---------+----------------------+------+------------+-----------+
| docker-alfa    | RUNNING | 172.17.0.1 (docker0) |      | PERSISTENT | 0         |
|                |         | 10.81.226.238 (eth0) |      |            |           |
+----------------+---------+----------------------+------+------------+-----------+
| docker-bravo   | RUNNING | 172.17.0.1 (docker0) |      | PERSISTENT | 0         |
|                |         | 10.81.226.173 (eth0) |      |            |           |
+----------------+---------+----------------------+------+------------+-----------+
| docker-charlie | RUNNING | 172.17.0.1 (docker0) |      | PERSISTENT | 0         |
|                |         | 10.81.226.174 (eth0) |      |            |           |
+----------------+---------+----------------------+------+------------+-----------+
```

### Cluster Design
               MASTER
	     docker-alfa
	          :
       ----------------------
       :                    :
    WORKER1              WORKER2
 docker-bravo        docker-charlie

### Starting Docker Swarm Cluster
1. Exec into **docker-alfa** by running `lxc exec docker-alfa -- bash` which will be the master and run `docker swarm init` Example:
```
lxc exec docker-alfa -- bash

```





