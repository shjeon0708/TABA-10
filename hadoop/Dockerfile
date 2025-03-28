FROM ubuntu:20.04
ENV HADOOP_VERSION=3.3.5
ENV HADOOP_HOME=/home/hadoop
ENV JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64
ENV PATH=$PATH:$HADOOP_HOME/bin:$HADOOP_HOME/sbin

RUN apt-get update && \
    apt-get install -y openjdk-8-jdk curl rsync vim net-tools wget && \
    apt-get clean
    
RUN curl -O https://downloads.apache.org/hadoop/common/hadoop-$HADOOP_VERSION/hadoop-$HADOOP_VERSION.tar.gz && \
    tar -xzvf hadoop-$HADOOP_VERSION.tar.gz && \
    mv hadoop-$HADOOP_VERSION /home/hadoop && \
    rm hadoop-$HADOOP_VERSION.tar.gz
    
COPY core-site.xml $HADOOP_HOME/etc/hadoop/core-site.xml
COPY hdfs-site.xml $HADOOP_HOME/etc/hadoop/hdfs-site.xml
COPY mapred-site.xml $HADOOP_HOME/etc/hadoop/mapred-site.xml

EXPOSE 9870 9864 8088 9000

CMD ["/bin/bash"]
