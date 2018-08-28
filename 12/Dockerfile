FROM alpine:3.8

ARG JDK_BUILD="7"

ENV LANG C.UTF-8
ENV JAVA_HOME="/opt/java/current"
ENV PATH="${PATH}:${JAVA_HOME}/bin"

# Download from http://jdk.java.net/12/

RUN set -exo pipefail \
    && wget --output-document /tmp/openjdk.tar.gz \
        https://download.java.net/java/early_access/alpine/${JDK_BUILD}/binaries/openjdk-12-ea+${JDK_BUILD}_linux-x64-musl_bin.tar.gz \
    && mkdir -p /opt/java \
    && cd /opt/java \
    && tar --extract --gzip --verbose --no-same-owner --file=/tmp/openjdk.tar.gz \
    && ln -s /opt/java/$(ls -1) /opt/java/current \
    && rm /opt/java/current/lib/src.zip \
    && rm /tmp/openjdk.tar.gz
