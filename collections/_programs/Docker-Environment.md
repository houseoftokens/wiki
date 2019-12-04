---
title: HoT Docker Environment
chapter: 5
layout: default

---

# HoT Docker Environment

We provide a project to build and run `HoT` in docker environment-

[https://github.com/houseoftokens/hot.docker](https://github.com/houseoftokens/hot.docker)

To build an `HoT` docker image by your own, your system should meet these system requirements:

- Docker 18.03.0 or above
- 8GB RAM at least 
- 20GB Disk at least 

## Build

To build your own docker image, run following steps-

```bash
    git clone https://github.com/houseoftokens/hot.docker.git
    cd hot.docker
    docker build -t hot-image-name .
```

## Run

The docker image build by the `Dockerfile` can run both producer node anf non-producer node, you can specify node type by `NODE_TYPE`.

### Non-producer

```bash
    docker run \
        --name your-container-name \
        -d \
        -v/your/data/path:/hot/data \
        -p your_server_port:8011 \
        -p yout_peer-port:9011 \
        -e NODE_TYPE="server" \
        -e PEER_NODES="peer1-server-node-host:9011#peer2-server-node-host:9011" \
        housetoken/hot:latest
```

### Producer

```bash
    docker run \
        --name your-container-name \
        -d \
        -v/your/data/path:/hot/data \
        -p your_server_port:8011 \
        -p yout_peer-port:9011 \
        -e NODE_TYPE="producer" \
        -e PEER_NODES="peer1-server-node-host:9011#peer2-server-node-host:9011" \
        housetoken/hot:latest
```
