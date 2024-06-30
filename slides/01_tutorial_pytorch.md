---
marp: true
title: 24 Jun 2024
size: 16:9
math: mathjax
theme: am_dark
paginate: true
headingDivider: [2,3]
footer: Kashu Yamazaki, 2024
# backgroundImage: url('https://marp.app/assets/hero-background.svg')
---

<!-- _class: cover_b -->
<!-- _header: "" -->
<!-- _footer: "" -->
<!-- _paginate: "" -->
<!-- _backgroundImage: url('https://marp.app/assets/hero-background.svg') -->

# Robot Perception and Control

###### Tutorial

Last updated: Jul / 25 /2024
Kashu Yamazaki
kyamazak@andrew.cmu.edu

## Docker 🐳

<!-- _class: trans -->
<!-- _footer: "" -->
<!-- _paginate: "" -->

## Virtual Machine vs Containers

A **Virtual Machine (VM)** virtualizes the underlying hardware by means of a hypervisor, while it provides operating-system-level virtualization. **Containers** are more lightweight than VMs, as they are not emulating hardware.

![#center w:850](img/vm_vs_container.png)

## Why Docker?

There are several merits of using Docker.

- We can **share the environment** 😀
    - You can share the Docker Image to help others setup and run your code. 
    - **No more repeated setup process on every different machine!**
- We can **improve reproducibility**. 
    - The code works even after several years on the Image.
    - No more suffering from messing up your environment after installing some software updates.

<!-- _class:  bq-red -->

> Note for Mac and Windows
>
> Docker uses the Linux kernel to manage resources between containers; Docker has to run in a Linux virtual machine for Mac and Windows, which makes some feature fail on Mac and Windows.
> Also the chip architecture needs to be considered (`M1` and `M2`): some has to cross compile `docker buildx build`

## Structure of Docker Environment

![#center w:600](img/docker_architecture.svg)

* **Image**: a template that contains middleware settings or commands needed to launch a container.
* **Container**: a virtual environment created based on a Docker Image where web servers, PyTorch environment, ... run. 
* **Registry**: Docker Hub is the place where the Images are published and shared.


## Managing Images and Containers

<!-- _class: pon-3 -->

<div class=ldiv>

- **List Images**: `docker images`
- **Remove an Image**: `docker rmi <imageID>`
- **Prune an Image**: `docker image prune`
- **Get an Image**: `docker pull`
- **Build an Image**: `docker build -t <imageName> -f Dockerfile .`

</div>

<div class=rdiv>

- **List Containers**: `docker ps -a`
- **Remove a Container**: `docker rm <containerID>`
- **Start a Container**: `docker run <imageName>`
- **Attach to a running Shell**: `docker exec -it <containerID> bash` 

</div>

<div class="bdiv">

With `docker images` command, you can check `<imageName>` and `<imageID>`.

![#center w:900](img/docker_images.png)

</div>

## Getting your own Image

You can write a `Dockerfile` to create your own image:

```Dockerfile
# Specify the base image: you can explore docker hub.
FROM pytorch/pytorch:2.0.1-cuda11.7-cudnn8-runtime
# Install dependencies and command-line tools.
RUN apt-get update && apt-get install -y build-essential cmake git wget
# Set the working directory.
WORKDIR /workspace
ENV HOME /workspace
# Pip install python packages.
RUN pip install timm opencv-python
```

Then: `docker build -t <imageName> -f /path/to/Dockerfile .` to build the image.
You can also publish your image on DockerHub by: `docker login && docker push <imageName>`

## Running Containers

**Docker run Options**

- `--rm` remove the container after it exits
- `--gpus` for GPU isolation
- `-i -t` or `-it` interactive, and connect a "tty"
- `-p 5004:8888` map port 8888 on the host to 5004 inside the container
- `-v ~/data:/data` map storage volume from host to container (bind mount) i.e. bind the `~/data` directory in your home directory to `/data` in the container

Starts TensorFlow with ports, volumes, console, and comment (All 1 line):

```sh
docker run --rm -it --gpus all -p 5004:8888 -v ~/data:/data <imageName>
```


## Running GUI Applications with Docker

1. Allow local X11 connections
    ```bash 
    xhost local:root
    ```

2. Run docker with options 
- Intel GPU

    ```bash 
    docker run --device=/dev/dri:/dev/dri -v /tmp/.X11-unix:/tmp/.X11-unix -e DISPLAY
    ```

- NVIDIA GPU

    ```bash
    docker run  --gpus 'all,"capabilities=compute,utility,graphics"' -v /tmp/.X11-unix:/tmp/.X11-unix -e DISPLAY
    ```

## Accessing Devices from the Container



## PyTorch 🔥

<!-- _class: trans -->
<!-- _footer: "" -->
<!-- _paginate: "" -->

## Computational Graph

There are two elements that consists the computational graph: valuable and operator (In PyTorch `tensor` and `function`).

