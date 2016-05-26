BioDocker
=========

[![Join the chat at https://gitter.im/BioDocker/biodocker](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/BioDocker/biodocker?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

```
___.   .__           .___             __                 
\_ |__ |__| ____   __| _/____   ____ |  | __ ___________
 | __ \|  |/  _ \ / __ |/  _ \_/ ___\|  |/ // __ \_  __ \
 | \_\ \  (  <_> ) /_/ (  <_> )  \___|    <\  ___/|  | \/
 |___  /__|\____/\____ |\____/ \___  >__|_ \\___  >__|   
     \/               \/           \/     \/    \/       

 ```

Containers
--------
Repository of approved bioinformatics containers

Links:
-------
Web Page              : http://biodocker.github.io/

Project Definition    : https://github.com/BioDocker/biodocker

Contribution Rules    : https://github.com/BioDocker/biodocker/blob/master/CONTRIBUTING.md

Wiki of the project   : https://github.com/BioDocker/biodocker/wiki

Containers            : https://github.com/BioDocker/containers

Containers Development: https://github.com/BioDocker/sandbox

Email                 : biodockers@gmail.com

License
----------

[Apache 2](http://www.apache.org/licenses/LICENSE-2.0)

Contents
----------

1. [Essentials](#1-essentials)  
 1.1. [Objectives](#11-objectives)    
 1.2. [What is BioDocker](#12-what-is-biodocker)  
* [Containers](#2-containers)  
  2.1. [What is a container?](#21-what-is-a-container)  
  2.2. [How to search for a container](#22-how-to-search-for-a-container)  
  2.3. [What do I need to use a container?](#23-what-do-i-need-to-use-a-container)   
  2.4. [How do I use a container?](#24-how-do-i-use-a-container)  
  2.5. [How to build a BioDocker container](#25-how-to-build-a-biodocker-container)  
* [Developing containers](#3-developing-containers)  
  3.1. [What do I need to develop?](#31-what-do-i-need-to-develop)  
  3.2. [How to create a container?](#32-how-to-create-a-container)  
* [Support](#4-support)  
  4.1  [Get involved](#41-get-involved)  

1. Essentials
--------------

### 1.1. Objectives

* Provide bioinformatics software in containers that are ready-to-use
* Promote software standardization and reproducible results in bioinformatics

### 1.2. What is BioDocker?

The BioDocker project came from the idea of using the Docker technology for bioinformatics software. Having a common and controllable environment for running software could help to deal with some of the
current problems during software development and distribution.


2. Containers
-------------

### 2.1. What is a container?

Containers are build from existing operating systems. They are different from Virtual machines because they don't posses an entire guest OS inside, instead, containers are build using optimized system
libraries and use the host OS memory management and process controls. Containers normally are centralized around a specific software and you can make them executable by instantiating images from them.

## 2.2. How to search for a container

The BioDocker containers are listed on this repository. Every software has a specific directory with a recipie inside on how to make the container.

### 2.3. What do I need to use a container?

In order to run a Docker (or BioDocker) container on your computer you will need the Docker daemon installed.

Check [here](https://docs.docker.com/installation/) for the instructions on how to do it.

### 2.4. How do I use a container?

In general the `README.md` of each project should explain you how to interact with it.

### 2.5. How to build a Biodocker container

There are two different ways to run a container.

* Go to the GitHub repository with the recipe of the software you want, clone it, and build it yourself on your machine.
* Use the docker daemon to search for a ready-to-use version of the containerized software you want.

Inside the central repository there is a list of softwares with docker recipes, there you can find more information about how to work with them.


3. Developing containers
-----------------------

### 3.1. What do I need to develop?

Docker containers are based on Linux systems, so you will need a computer with Linux installed, you also will need the docker daemon and the software you want to containerize.

### 3.2. How to create a container?

Having all in hands now you need to create a Dockerfile. Dockerfiles are simple recipes to instruct the daemon on how to set an appropriate OS and how to download, manage, install and
give access to the software inside.

You can check the [Docker](https://docs.docker.com/reference/builder/) documentation for more information.

Once the container is ready you can get in touch with us so we can make the appropriate arrangements to make your container available to everyone in the community by giving an automated build system.


4. Support
----------

### 4.1. Get involved

Whether you want to make your own software available to others as a container, to just use them on your pipelines and analysis or just give opinions, you are most welcome. This is a community-driven project, that means everyone has a voice.

Here are some general ideas:

* Browse our list of containers
* Propose your own ideas or software
* Interact with other if you think there is something missing.
