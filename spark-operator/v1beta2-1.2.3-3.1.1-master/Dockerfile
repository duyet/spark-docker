ARG SPARK_IMAGE=gcr.io/spark-operator/spark-operator:v1beta2-1.2.3-3.1.1

# Build spark-operator from master branch
FROM golang:1.15.2-alpine as builder
WORKDIR /workspace
RUN apk update && apk add git && \
    git clone https://github.com/GoogleCloudPlatform/spark-on-k8s-operator && \
    cd spark-on-k8s-operator && \
    go mod download && \
    CGO_ENABLED=0 GOOS=linux GOARCH=amd64 GO111MODULE=on go build -a -o /usr/bin/spark-operator main.go

FROM ${SPARK_IMAGE}
USER root
COPY --from=builder /usr/bin/spark-operator /usr/bin/
