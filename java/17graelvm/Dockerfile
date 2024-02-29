FROM debian:latest

RUN wget "https://download.oracle.com/graalvm/17/latest/graalvm-jdk-17_linux-x64_bin.tar.gz"
RUN tar -xvf "graalvm-jdk-17_linux-x64_bin.tar.gz"

ENV PATH="/graalvm-jdk-17/bin:${PATH}"
ENV JAVA_HOME="/graalvm-jdk-17"

LABEL       author="VeguiDev" maintainer="veguidev@farfania.com"

LABEL       org.opencontainers.image.source="https://github.com/VeguiDev/yolks"
LABEL       org.opencontainers.image.licenses=MIT

RUN 				apt-get update -y \
    && apt-get -y install lsof curl ca-certificates openssl git tar sqlite3 fontconfig libfreetype6 tzdata iproute2 libstdc++6 \
    && useradd -d /home/container -m container

USER        container
ENV         USER=container HOME=/home/container
WORKDIR     /home/container

COPY        ./../entrypoint.sh /entrypoint.sh
CMD         [ "/bin/bash", "/entrypoint.sh" ]

