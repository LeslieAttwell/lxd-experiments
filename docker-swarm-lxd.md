# Docker Swarm Cluster on LXD

### Preparing Cluster
1. Build first 3x System containers as per this [guide](docker-lxd.md).
```bash
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
```ascii
               MASTER
            docker-alfa
                 :
       ----------------------
       :                    :
    WORKER 1             WORKER 2
  docker-bravo         docker-charlie
```

### Initializing the Docker Swarm Cluster
1. Exec into **docker-alfa** by running `lxc exec docker-alfa -- bash`.
2. Initialize the cluster by running `docker swarm init`. Example:
```bash
root@docker-alfa:~# docker swarm init
Swarm initialized: current node (ivmc5z2u885f8tecxpldoampe) is now a manager.

To add a worker to this swarm, run the following command:

    docker swarm join --token SWMTKN-1-5qqlg1tkfsfscxra931pheapq3j2qwkp054rsc6hcvvesatnrm-0ndpprfhwraia9t03rmhwc3zu 10.81.226.238:2377

To add a manager to this swarm, run 'docker swarm join-token manager' and follow the instructions.

root@docker-alfa:~# 
```
3. Copy/Save the `docker swarm join --token %` command for the **docker-brave** and **docker-charlie** workers.
4. Exec into **docker-bravo** and into **docker-charlie** (see Step 1 example) and run the command copied from Step 2. Example:
Worker 1 join:
```
root@docker-bravo:~# docker swarm join --token SWMTKN-1-5qqlg1tkfsfscxra931pheapq3j2qwkp054rsc6hcvvesatnrm-0ndpprfhwraia9t03rmhwc3zu 10.81.226.238:2377
This node joined a swarm as a worker.
root@docker-bravo:~# 
```
Worker 2 join:
```
root@docker-charlie:~# docker swarm join --token SWMTKN-1-5qqlg1tkfsfscxra931pheapq3j2qwkp054rsc6hcvvesatnrm-0ndpprfhwraia9t03rmhwc3zu 10.81.226.238:2377
This node joined a swarm as a worker.
root@docker-charlie:~# 
```
5. Exec into the master and run `docker node ls`
```
root@docker-alfa:~# docker node ls
ID                            HOSTNAME            STATUS              AVAILABILITY        MANAGER STATUS      ENGINE VERSION
ivmc5z2u885f8tecxpldoampe *   docker-alfa         Ready               Active              Leader              18.06.1-ce
b0pl8bupy7bws23rlcjv1x12f     docker-bravo        Ready               Active                                  18.06.1-ce
t8jnbkrmbl70rsarjgul5piz4     docker-charlie      Ready               Active                                  18.06.1-ce
root@docker-alfa:~# 
```
Docker Swarm running in System Container managed by LXD is now ready.
