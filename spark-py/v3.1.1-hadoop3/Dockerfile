FROM gcr.io/spark-operator/spark-py:v3.1.1-hadoop3
USER root

# Add s3a connector
ENV HADOOP_VERSION 3.1.1
ENV AWS_SDK_VERSION 1.11.271
ADD https://repo1.maven.org/maven2/org/apache/hadoop/hadoop-aws/$HADOOP_VERSION/hadoop-aws-$HADOOP_VERSION.jar $SPARK_HOME/jars
ADD https://repo1.maven.org/maven2/com/amazonaws/aws-java-sdk-bundle/$AWS_SDK_VERSION/aws-java-sdk-bundle-$AWS_SDK_VERSION.jar $SPARK_HOME/jars

# Install python packages
RUN apt-get update --allow-releaseinfo-change && \
    apt-get install -y libsasl2-dev curl && \
    pip3 install boto3 aliyun-python-sdk-core sentry-sdk oss2 \
       orjson tenacity numpy pandas geoip2 psycopg2-binary \
       pyorc pycryptodome asn1crypto pycrypto pyyaml && \
    curl https://archive.apache.org/dist/spark/spark-3.2.1/spark-3.2.1-bin-hadoop3.2.tgz --output spark.tgz && \
    tar -xvzf ./spark.tgz -C ./ && \
    cp ./spark-3.2.1-bin-hadoop3.2/jars/* $SPARK_HOME/jars && \
    rm -rf ./spark-3.2.1-bin-hadoop3.2 spark.tgz

# Setup for the Prometheus JMX exporter.
# Add the Prometheus JMX exporter Java agent jar for exposing metrics sent to the JmxSink to Prometheus.
ADD https://repo1.maven.org/maven2/io/prometheus/jmx/jmx_prometheus_javaagent/0.11.0/jmx_prometheus_javaagent-0.11.0.jar /prometheus/
RUN chmod 644 /prometheus/jmx_prometheus_javaagent-0.11.0.jar

RUN mkdir -p /etc/metrics/conf
COPY spark-py/v3.1.1-hadoop3/conf/metrics.properties /etc/metrics/conf
COPY spark-py/v3.1.1-hadoop3/conf/prometheus.yaml /etc/metrics/conf

COPY spark-py/v3.1.1-hadoop3/entrypoint.sh /opt/
