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
* Docker Swarm is configured but no services are added. An example of how to do that is included below.

# Setup

```
git clone https://github.com/rhysmeister/DockerSwarm.git
cd DockerSwarm
vagrant up
```

# Access the docker manager

```
vagrant ssh docker1
docker node ls
```

# Setup a Docker Swarm Service

Create a service called nginx_service, using the nginx image, exposing the port 80.

```
docker service create --replicas 5 -p 80:80 --name nginx_service nginx
```

View the containers in the Swarm

```
docker service ps nginx_service
```

Ensure what all three Swarm nodes return the Welcome to nginx message

```
ips="192.168.44.101 192.168.44.102 192.168.44.103"
for ip in "$ips"; do  curl -s http://$ip | grep --color "<h1>Welcome to nginx"; done
```

Remove the service

```
docker service rm nginx_service
```
