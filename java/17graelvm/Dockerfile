FROM alpine:latest

LABEL author="VeguiDev" maintainer="veguidev@farfania.com"
LABEL org.opencontainers.image.source="https://github.com/VeguiDev/yolks"
LABEL org.opencontainers.image.licenses=MIT

ENV GRAALVM_VERSION=17.0.12 \
    JAVA_HOME=/usr/lib/jvm/graalvm-ce-17.0.12 \
    PATH=/usr/lib/jvm/graalvm-ce-17.0.12/bin:$PATH

RUN apk --no-cache add ca-certificates wget gcc zlib zlib-dev libc-dev

RUN mkdir /usr/lib/jvm; \
    wget "https://github.com/oracle/graal/releases/download/vm-${GRAALVM_VERSION}/graalvm-ce-${GRAALVM_VERSION}-linux-amd64.tar.gz"; \
    tar -zxC /usr/lib/jvm -f graalvm-ce-${GRAALVM_VERSION}-linux-amd64.tar.gz; \
    rm -f graalvm-ce-${GRAALVM_VERSION}-linux-amd64.tar.gz

ENV LD_BIND_NOW=1

USER container
ENV USER=container HOME=/home/container
WORKDIR /home/container

COPY ./../entrypoint.sh /entrypoint.sh

CMD [ "/bin/sh", "/entrypoint.sh" ]