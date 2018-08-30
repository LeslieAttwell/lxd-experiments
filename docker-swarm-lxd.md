# Docker Swarm Cluster on LXD

### Installing Docker Swarm Cluster
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
| docker-alfa    | RUNNING | 10.81.226.238 (eth0) |      | PERSISTENT | 0         |
+----------------+---------+----------------------+------+------------+-----------+
| docker-bravo   | RUNNING | 10.81.226.173 (eth0) |      | PERSISTENT | 0         |
+----------------+---------+----------------------+------+------------+-----------+
| docker-charlie | RUNNING | 10.81.226.174 (eth0) |      | PERSISTENT | 0         |
+----------------+---------+----------------------+------+------------+-----------+

```





