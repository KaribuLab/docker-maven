FROM alpine:3.22.2

RUN apk add --no-cache gcompat libc6-compat libstdc++ zlib

COPY amazon-corretto-8.472.08.1-linux-x64.tar.gz /tmp/amazon-corretto-8.472.08.1-linux-x64.tar.gz
COPY apache-maven-3.5.2-bin.tar.gz /tmp/apache-maven-3.5.2-bin.tar.gz

RUN tar -xzf /tmp/amazon-corretto-8.472.08.1-linux-x64.tar.gz -C /opt && \
    rm -f /tmp/amazon-corretto-8.472.08.1-linux-x64.tar.gz && \
    ln -s /opt/amazon-corretto-8.472.08.1-linux-x64 /opt/jdk8 && \
    tar -xzf /tmp/apache-maven-3.5.2-bin.tar.gz -C /opt && \
    rm -f /tmp/apache-maven-3.5.2-bin.tar.gz && \
    ln -s /opt/apache-maven-3.5.2 /opt/maven

ENV JAVA_HOME=/opt/jdk8
ENV MAVEN_HOME=/opt/maven
ENV LD_LIBRARY_PATH=$JAVA_HOME/jre/lib/amd64:$JAVA_HOME/jre/lib/amd64/server:$JAVA_HOME/lib/amd64
ENV PATH=$PATH:$JAVA_HOME/bin:$MAVEN_HOME/bin