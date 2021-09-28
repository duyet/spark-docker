# Spark Image for Kubernetes

![Build and Push Docker](https://github.com/duyet/spark-docker/workflows/Build%20and%20Push%20Docker/badge.svg)

# Docker hub

- https://hub.docker.com/r/duyetdev/spark
- https://hub.docker.com/r/duyetdev/spark-py
- https://hub.docker.com/r/duyetdev/spark-operator

# Image information

## spark-py

Base image from gcr.io/spark-operator/spark-py, adding some jar files to support AWS.

- hadoop-aws-3.3.1.jar
- aws-java-sdk-bundle-1.11.271.jar

## spark-operator

Base image from gcr.io/spark-operator/spark-operator, adding some jar files to support AWS.

- hadoop-aws-3.3.1.jar
- aws-java-sdk-bundle-1.11.271.jar

# Usage

```bash
docker pull duyetdev/spark-py:v3.1.1-hadoop3
docker pull duyetdev/spark-operator:v1beta2-1.2.3-3.1.1
```