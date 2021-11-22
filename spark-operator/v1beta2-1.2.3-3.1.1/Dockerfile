FROM gcr.io/spark-operator/spark-operator:v1beta2-1.2.3-3.1.1

ENV HADOOP_VERSION 3.1.1
ENV AWS_SDK_VERSION 1.11.271

# Add s3a connector
ADD https://repo1.maven.org/maven2/org/apache/hadoop/hadoop-aws/$HADOOP_VERSION/hadoop-aws-$HADOOP_VERSION.jar $SPARK_HOME/jars
ADD https://repo1.maven.org/maven2/com/amazonaws/aws-java-sdk-bundle/$AWS_SDK_VERSION/aws-java-sdk-bundle-$AWS_SDK_VERSION.jar $SPARK_HOME/jars

