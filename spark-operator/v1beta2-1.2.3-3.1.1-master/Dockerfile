ARG SPARK_IMAGE=gcr.io/spark-operator/spark-operator:v1beta2-1.2.3-3.1.1

# Build spark-operator binary from master branch
FROM golang:1.15.2-alpine as builder
WORKDIR /workspace
RUN apk update && apk add git && \
    git clone --depth 1 https://github.com/GoogleCloudPlatform/spark-on-k8s-operator && \
    cd spark-on-k8s-operator && \
    go mod download && \
    CGO_ENABLED=0 GOOS=linux GOARCH=amd64 GO111MODULE=on go build -a -o /usr/bin/spark-operator main.go

FROM ${SPARK_IMAGE}
USER root
COPY --from=builder /usr/bin/spark-operator /usr/bin/

# Add s3a connector
ADD https://repo1.maven.org/maven2/org/apache/hadoop/hadoop-aws/2.7.3/hadoop-aws-2.7.3.jar $SPARK_HOME/jars
ADD https://repo1.maven.org/maven2/com/amazonaws/aws-java-sdk/1.7.4.2/aws-java-sdk-1.7.4.2.jar $SPARK_HOME/jars

