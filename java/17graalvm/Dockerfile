FROM debian:stable-slim

LABEL author="VeguiDev" maintainer="veguidev@farfania.com"
LABEL org.opencontainers.image.source="https://github.com/VeguiDev/yolks"
LABEL org.opencontainers.image.licenses=MIT

# Update system and install dependencies
RUN apt-get update -y \
    && apt-get -y install wget gdb lsof curl ca-certificates openssl git tar sqlite3 fontconfig libfreetype6 tzdata iproute2 libstdc++6 \
    && useradd -d /home/container -m container

# Descargar y extraer GraalVM
RUN wget "https://download.oracle.com/graalvm/17/latest/graalvm-jdk-17_linux-x64_bin.tar.gz" -O /tmp/graalvm-jdk-17_linux-x64_bin.tar.gz \
    && tar -xvf /tmp/graalvm-jdk-17_linux-x64_bin.tar.gz -C /tmp \
    && DIR_NAME=$(tar -tf /tmp/graalvm-jdk-17_linux-x64_bin.tar.gz | head -1 | cut -d "/" -f 1) \
    && mv /tmp/$DIR_NAME /usr/local/graalvm \
    && rm /tmp/graalvm-jdk-17_linux-x64_bin.tar.gz

# Establecer las variables de entorno
ENV PATH="/usr/local/graalvm/bin:${PATH}"
ENV JAVA_HOME="/usr/local/graalvm"

USER container
ENV USER=container HOME=/home/container
ENV LD_BIND_NOW=1
WORKDIR /home/container

COPY ./../entrypoint.sh /entrypoint.sh
CMD [ "/bin/bash", "/entrypoint.sh" ]