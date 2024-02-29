FROM debian:bookworm-slim

FROM ghcr.io/graalvm/native-image-community:17-muslib

LABEL       author="VeguiDev" maintainer="veguidev@farfania.com"

LABEL       org.opencontainers.image.source="https://github.com/VeguiDev/yolks"
LABEL       org.opencontainers.image.licenses=MIT

RUN 				apt update -y \
    && apt install -y lsof curl ca-certificates openssl git tar sqlite3 fontconfig libfreetype6 tzdata iproute2 libstdc++6 \
    && useradd -d /home/container -m container

USER        container
ENV         USER=container HOME=/home/container
WORKDIR     /home/container

COPY        ./../entrypoint.sh /entrypoint.sh
CMD         [ "/bin/bash", "/entrypoint.sh" ]

