FROM alpine:3.8

ARG JDK_BUILD="27"

ENV LANG C.UTF-8
ENV JAVA_HOME="/opt/java/current"
ENV PATH="${PATH}:${JAVA_HOME}/bin"

# Download from http://jdk.java.net/11/

RUN set -exo pipefail \
    && wget --output-document /tmp/openjdk-11.tar.gz \
        https://download.java.net/java/early_access/alpine/${JDK_BUILD}/binaries/openjdk-11+${JDK_BUILD}_linux-x64-musl_bin.tar.gz \
    && mkdir -p /opt/java \
    && cd /opt/java \
    && tar -zxvf /tmp/openjdk-11.tar.gz \
    && JAVA_DIR=$(ls -1) \
    && ln -s /opt/java/${JAVA_DIR} /opt/java/current \
    && rm /tmp/openjdk-11.tar.gz
