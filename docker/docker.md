# Containers and Docker

## Overview
  - [Overview](#overview)
  - [What is a container?](#what-is-a-container)
  - [Why containers?](#why-containers)
    - [Application development](#application-development)
      - [without containers](#without-containers)
      - [with containers](#with-containers)
    - [Application deployment](#application-deployment)
      - [without containers](#without-containers-1)
      - [with containers](#with-containers-1)
  - [What is Docker?](#what-is-docker)
    - [Docker vs Virtual Machines](#docker-vs-virtual-machines)
    - [How does Docker work?](#how-does-docker-work)
  - [Docker Command Cheatsheet](#docker-command-cheatsheet)

## What is a container?

- A way to package an application with all necessary dependencies and configuration.
- That package is a portable artifact, easily shared and moved around.

## Why containers?

**TLDR**: Containers allow you to reproduce runtime environments easily.

### Application development

#### without containers

-  An application requires an environment to run on.
-  An environment may contain many different dependencies for the application to run (such as node.js, postgres, sql, etc...)
-  To share application among developers, they would also need to have installed the same dependencies to run on the same environment.
- Problems:
  - Installation process highly variable, especially if  on different operating systems.
  - Many manual steps to install, and something could go wrong along the way.

#### with containers

- Each container is in it's own isolated environment, packaged with all configurations.
- One command to install the app.

### Application deployment

#### without containers

- Developers produce running artifacts for the application (`.jar` or `.js` file)
- Developers would create setup instructions or scripts to deploy a database for the application.
- Developers would send these instructions + running artifacts to an operations team to deploy.
- Problems:
  - Again, long instructions to configure servers lead to mistakes or problems.
  - Issues with dependency conflicts or versions.

#### with containers

- All dependencies are already packaged inside an application container.
- No environment configuration needed on server (only need docker runtime).
- Run docker commands to deploy application on the same environment.

## What is Docker?

**Docker** is an open platform for developing, shipping and deploying containers. It allows you crte

### Docker vs Virtual Machines

![docker vs vm](https://i1.wp.com/www.docker.com/blog/wp-content/uploads/Blog.-Are-containers-..VM-Image-1-1024x435.png?ssl=1)

Source: https://www.docker.com/blog/containers-replacing-virtual-machines/

**Virtual Machines**

- Each application runs on it's own guest operating system.
- *Hypervisor* is used to share hardware resources between guest operating systems.

**Docker**

- All containerised applications run on the same host operating system.
- Benefits over Virtual Machines:
  - **Saves memory**: Each container is a lot smaller as compared to an entire OS.
  - **Saves time**: Building a container takes seconds, while an operating system may take ages to build.
  - **Caching**: Virtual machine snapshots are used sparingly, while docker uses images, which can be cached and built incrementally.

### How does Docker work?

![docker-architecture](https://docs.docker.com/engine/images/architecture.svg)

Image taken from the official docker documentation site: https://docs.docker.com/get-started/overview/

- **Client**: Docker CLI, taking user input to run commands (eg: `docker run` or `docker pull`)
- **Docker Host**: Machine where the docker program is installed on. Could be your laptop or a virtual machine on the cloud.
- **Docker Daemon**: A running program that receives and runs docker commands from the client such as pulling images from a registry or to run a containers from a images.
- **Container**: An isolated environment for running an application.
- **Image**: A read only template on how to build and run a container.
- **Registry**: Server where docker images are stored. These is where the docker host would pull or push images to/from. There are private and public registries available depending on use cases.

## Docker Command Cheatsheet

![docker-cheat-sheet](https://raw.githubusercontent.com/sangam14/dockercheatsheets/master/dockercheatsheet8.png)

**Source**: https://github.com/collabnix/dockerlabs/blob/master/docker/cheatsheet/README.md














