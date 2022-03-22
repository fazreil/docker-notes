title: Docker-Notes
author:
  name: Fazreil Amreen
  twitter: fab52
  url: http://fazreil.github.io
output: notes.html
controls: true
theme: sjaakvandenberg/cleaver-dark

---
# Introduction

This article explains containerization technology and how are we going to use containerization in daily operations.

---

# Definition

Containerization is a technology of *packaging softwares* in containers. The motivation of encapsulating software in containers is to allow the software to be *portable* to run in various systems. Any images distributed to registry are able to work on any systems.

The medium of distribution for a container is a *registry*. Imagine registries like the PVCS storage where we store all of the distributed applications.

---
### Images and Containers

Packaged application uploaded into container registry is called the image. When these images are executed to run on the system, they are called containers.  

---
# Anatomy of a container

This section discuss the building blocks of a continer.

---
### What are there in a container?

Containers include the application we're delivering, bundle it together with underlying libraries and also the operating system to manage the runtime of the application. The design of such anatomy allow decoupling the application from the host operating system. You may run the application in any operating system as long as it runs container runtime like docker, ecs, etc.

---
### What are there in a container?

<figure class="video_container">
  <video controls="true" allowfullscreen="true">
    <source src="img/anatomy.webm" type="video/webm">
  </video>
</figure>

---
### dockerfiles

Docker images are build with the declarative definition that sums up the building block of a container, or in this sense, the docker image. Example of a dockerfile:

```
FROM openjdk:11
COPY target/app.war /opt/application1/app.war
exec java -jar /opt/application1/app.war
```

The example above clearly define how a docker image is being build.

---
### docker build command
Building the image is done by running build command:

```
docker build . -t rhbdigital/application1:1.0.0
```

---
### docker run command
Running the docker image is done by executing the following command:

```
docker run -p 8080:8080 -v mount1:/etc/application1 rhbdigital/application1:1.0.0
```

---
### Containers vs Virtual Machines

Virtual Machines by definition is an abstraction of hardware in a traditional computer that consists of application-OS-hardware. In another hand, a container is an abstraction of the OS. You might heard some people says that containers do not have OS; in a sense that is correct but the misconception is that it carries OS on its own however when managing containers, takes away the pain of managing the OS. Things that we usually manage in the OSis like patching libraries, managing memory limits, mounting hardwares are taken away when managing libraries.

But what if we really need to patch libraries, manage memory limits and mounting hardwares? Containers lifecycles are short. Once the container runs, We're almost hands-off the containers. If we are to make any of said changes, we will rebuild the image and distribute them all over.

---
### Scalability of Containers vs VM

<figure class="video_container">
  <video controls="true" allowfullscreen="true">
    <source src="img/scaling.webm" type="video/webm">
  </video>
</figure>

---
# Containers in software development

This section discusses about how containers play its part in software development

---
### SIT to use containers

Testers could test on SIT on demand to minimize the use of resources. Each SIT is provisioned according to the need in SIT when initialized and teared down after testing session is completed.

---
### Use containers as jenkins agents

Jenkins can dynamically bring up/down agents on-demand to minimize the use of resources. Only have agents as containers to run as needed.

---
### Software packaged in containers

Softwares being developed using various technologies like java (war, jar), NodeJS (zip files), websites (html) or C# (exe).

These executables are then packaged into docker images and distributed.

---
### Delivering softwares packaged in containers

<figure class="video_container">
  <video controls="true" allowfullscreen="true">
    <source src="img/build.webm" type="video/webm">
  </video>
</figure>

---
# Q&A
