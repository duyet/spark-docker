# Spark the Docker image for Kubernetes
Spark image for running on Kubernetes

![Build and Push Docker](https://github.com/duyetdev/spark-docker/workflows/Build%20and%20Push%20Docker/badge.svg)

# Docker hub

```
https://hub.docker.com/r/duyetdev/spark
https://hub.docker.com/r/duyetdev/spark-py
```

# About this image

The images are built to be run in a container runtime environment that Kubernetes supports. Docker is a container runtime environment that is frequently used with Kubernetes. Spark (starting with version 2.3) ships with a *Dockerfile* that can be used for this purpose, or customized to match an individual application’s needs. It can be found in the `kubernetes/dockerfiles/` directory.

Spark also ships with a `bin/docker-image-tool.sh` script that can be used to build and publish the Docker images to use with the Kubernetes backend.

This repo using Github Actions to build these images from Apache Spark source code:

```
$ ./bin/docker-image-tool.sh -r <repo> -t my-tag build
$ ./bin/docker-image-tool.sh -r <repo> -t my-tag push
```

Let see the full script at [.github/workflows/build.yaml](.github/workflows/build.yaml)
