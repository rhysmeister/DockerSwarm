# Docker Swarm

This project uses Vagrant and Ansible to launch a Docker Swarm Cluster.

It is based on the following tutorial...

https://docs.docker.com/engine/swarm/swarm-tutorial/

# Requirements

* Git
* Vagrant 2.2.3+
* Ansible 2.8.2+
* VirtualBox 6+

# Description of Swarm Cluster

* 3 CentOS 7 Virtualbox Instances 2GB RAM / 2 vCPUs.
* The 3 nodes will be assigned the following IP addresses 192.168.44.101-103.
* 192.168.44.101 (cnode1) will be considered the Manager machine.

# Setup

```
git clone https://github.com/rhysmeister/DockerSwarm.git
cd DockerSwarm
vagrant up
```

Access the docker manager

```
vagrant ssh docker1
docker node ls
```

SWMKEY-1-cjwvaP1ijjTvFofXVcUeLwwdpZqCxwRHp+oaGjk0tUo
