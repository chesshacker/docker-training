# Docker Training

This repository provides some pre-work before we meet for Docker training. The
goal of this material is to get everyone's machine setup to run Docker, to
download some of the images we will use during class, and to at least introduce
everyone briefly to some of the Docker concepts that we will be exploring during
our class.

## Installation

1. Download and install [Docker for your platform of choice][docker]. If you run
into any errors, reference the "Getting Started Tutorial" for your platform.

  Note for Windows 10: you may be prompted to enable Hyper-V and required to
  restart.

  Note for Windows 7 or 8: you may have to use [Docker Toolbox][dockertoolbox]
  instead of Docker for Windows.

  Tip for Windows 7: If your install fails because it can't create a network
  adapter, you may find during the install that checking "Install VirtualBox
  with NDIS5 instead of NDIS6" helps to solve the problem.

2. Verify Docker was installed correctly by running:

  ```
  docker run --rm hello-world
  ```

3. Windows users must also [share a local drive][drive] in the Docker for
Windows Settings. On Mac OS X, `/Users` is automatically shared, so you are all
set.

  If you are on a corporate sort of laptop, the vEthernet (DockerNat) network
  could be classified as a Public network, and firewall rules might prevent you
  from sharing your drive. You can change the network category using the local
  security policy editor (Windows-R, run secpol.msc), select "Network List
  Manager Policies" on the left, then double-click "Unidentified Networks",
  change "Location type" to Private, and apply changes.

  To verify your shared drive is setup on Windows, run:

  ```
  docker run --rm -v c:/Users:/data alpine ls /data
  ```

## Download Images

Once you have Docker installed, and preferably when you have a good internet
connection, run the following:

```
docker pull alpine
docker pull nginx
docker pull node
docker pull python:3-alpine
docker pull openjdk:jre-alpine
docker pull mysql:5.7
docker pull wordpress
docker pull postgres
docker pull ruby:2.4
```

## Introduction to Docker

Docker is a popular set of tools to provide lightweight virtualization at a
higher level than hypervisors. Containers run as a guest of the operating system
and therefore, they must run a similar operating system as the host. They look
like a complete host but are much leaner, so you can run more containers than
you could traditional virtual machines.

When using Docker to do development from a Mac OS X or Windows computer, you
actually run a virtual machine with Linux which in turn runs your Docker
containers. Thanks to recent advances in the Docker ecosystem, integration with
Mac OS X and Windows is fairly seamless, and you don't need to think too much
about the virtual machine. From a Windows computer, it is also possible to run
Windows containers that interact with the Windows operating system instead of a
Linux virtual machine, but the focus here will be on Linux containers.

Docker is both open-source software and a company. It became popular because it
automates the deployment of applications into containers, creating a
developer-friendly environment to ship software quickly and consistently from
local development to test and production.

Docker also fits in well with microservices architectures because you typically
run a single process in a single container and you connect many containers to
create a distributed application.

## Nuts and bolts

Docker containers are managed by a Docker daemon, and you typically interact
with the daemon using a Docker client, though you can also interact with it
using an API.

Docker containers are your running processes. Just as shipping containers
transport stuff, Docker containers are used to ship your software. To start an
application, you are required to specify an image. Additionally, you may specify
volumes, environment variables, connected containers, exposed ports, and a few
other settings. An image is built on a "Union file system" which is composed of
layers. The image layers are immutable, so you can quickly and consistently
start up your containers. On top of the image, volumes are mounted which contain
persistent data that can be modified by your application. Environment variables
are often used to change runtime behavior. Linked containers and ports come into
play when you want to connect your services together. We will dig into all of
these topics more during the lab.

If you successfully installed Docker, you have the tools you need to get
started, and you should also have the hello-world image. When you executed the
`run` command to verify your installation, Docker did several things. It pulled
the hello-world image from a Docker repository called Docker Hub, and then it
used this image to create and start a container. You can create an account on
Docker Hub to store your images, or you can use other container registries,
typically offered by the cloud platform of your choice.

You can do a lot with the Docker images provided on Docker Hub, but soon you
will want to create your own images. To build an image, you create a Dockerfile
and use the Docker client to build and push your image to the Docker repository
of your choice.

## Beyond the Basics

Understanding how to run containers with the Docker client is important to
learning Docker, but when you start running many connected containers, you'll
want some better automation. Locally, docker-compose is typically used to
provide that automation. With docker-compose, you define multiple containers in
a YAML file, and can then use `docker-compose up` to start all the containers
together. This is very important to doing local development, so we will cover
it during class.

To run containers in production there are many more technologies and tools you
can employ, including Docker Swarm and Kubernetes. We will not cover these as
part of this class.

## References

Hopefully this brief overview gave you some idea of what Docker is. If it
doesn't  make sense yet, don't worry... we will connect these ideas and give you
some hands on experience during the class. There are a lot of great references
to continue learning. I highly recommend reading [The Docker Book][dockerbook].

Docker provides some great reference material too. See [Docker's
documentation][dockerdocs] and [free self-paced courses][classes].

## Optional Setup

Mac OS X (or anyone using a bash shell) users may want to setup [bash
completion][bash]. PowerShell users may want to setup [posh][posh].

[docker]: https://www.docker.com/products/docker
[bash]: https://docs.docker.com/docker-for-mac/#/installing-bash-completion
[posh]: https://docs.docker.com/docker-for-windows/#/set-up-tab-completion-in-powershell
[drive]: https://docs.docker.com/docker-for-windows/#/shared-drives
[dockerbook]: https://www.dockerbook.com/
[dockerdocs]: https://docs.docker.com/
[classes]: https://training.docker.com/category/self-paced-online
[dockertoolbox]: https://docs.docker.com/toolbox/toolbox_install_windows/
