# Introduction

![Docker Logo](./img/docker_logo.jpg)

**Docker** is a platform for developing, delivering, and running applications in containers. It allows you to package an application
and all its dependencies into a single entity called a **docker image**. Instances of docker images are  **containers**,
which are lightweight and isolated, enabling applications to run in any environment without the need to install and configure
all their dependencies.

- **docker image**: represents a snapshot of a filesystem with the application and its dependencies installed.
A Docker image is immutable and is used to create Docker containers.

- **docker container**: represents an instance of a Docker image. Containers are isolated from the runtime environment,
can be started and stopped independently of each other.