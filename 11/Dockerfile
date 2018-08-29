FROM alpine:3.8 as ecr-login
RUN set -exo pipefail \
    && apk add --no-cache \
        go \
        git \
        make \
        musl-dev \
    && go get -u github.com/awslabs/amazon-ecr-credential-helper/ecr-login/cli/docker-credential-ecr-login


FROM alpine:3.8

ARG JDK_BUILD="27"

ENV LANG C.UTF-8
ENV JAVA_HOME="/opt/java/current"
ENV PATH="${PATH}:${JAVA_HOME}/bin"

COPY --from=ecr-login /root/go/bin/docker-credential-ecr-login /usr/local/bin/docker-credential-ecr-login

# Download from http://jdk.java.net/11/

RUN set -exo pipefail \
    && wget --output-document /tmp/openjdk.tar.gz \
        https://download.java.net/java/early_access/alpine/${JDK_BUILD}/binaries/openjdk-11+${JDK_BUILD}_linux-x64-musl_bin.tar.gz \
    && mkdir -p /opt/java \
    && cd /opt/java \
    && tar --extract --gzip --verbose --no-same-owner --file=/tmp/openjdk.tar.gz \
    && ln -s /opt/java/$(ls -1) /opt/java/current \
    && rm /opt/java/current/lib/src.zip \
    && rm /tmp/openjdk.tar.gz \
    && mkdir -p /root/.docker \
    && echo "{ \"credsStore\": \"ecr-login\" }" > /root/.docker/config.json
