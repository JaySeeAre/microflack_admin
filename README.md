MicroFlack's Administration Scripts
===================================

This repository contains installation and administration scripts for MicroFlack.

Getting Started
----------------
Make sure Hyper-V is installed and enabled on your hardware.

I have switched the vagran file to use bento/ubuntu-16.04 which supports the hyperv provider so you should be able to start by cd'ing to the microflack_admin dir and running:

```
vagrant up --provider=hyperv
```

Environment variables used by microservices
-------------------------------------------

Microservices expect the following environment variables to be defined:

- LB

The URL of the load balancer, for example `http://192.168.33.10`. Required.

- LB_ALGORITHM

The load balancing algorithm to use, for example `roundrobin` or `source`. Optional.

- ETCD

A list of connection endpoints for the etcd service, separated by commas. For example, `http://192.168.33.10:2379` for a single endpoint, or `http://192.168.33.10:2379,http://192.168.33.11:2379` for multiple endpoints. Required.

- REDIS

The IP address and port of the Redis service, for example `192.168.33.10:6379`. Required.

- SECRET_KEY

The user session's secret key. Optional.

- JWT_SECRET_KEY

The token signing key. This key must be the same across all services for token generation and validation to work. Required.

- DATABASE_URL

The SQLAlchemy database connection URL. Optional.

- SERVICE_NAME

The name of the service. Optional.

- SERVICE_URL

The path portion of the URL on which the service will be exposed by the load balancer. Optional.

- HOST_IP_ADDRESS

The IP address the container can use to access the Docker host. Optional.

Message post install
--------------------
MicroFlack is now deployed!
- Run `source ~/.profile` or log back in to update your environment.
- You may need some variables from `/home/ubuntu/.profile` if you intend to run services in another host.