FROM --platform=$TARGETOS/$TARGETARCH ghcr.io/graalvm/jdk-community:17

LABEL       author="VeguiDev" maintainer="veguidev@farfania.com"

LABEL       org.opencontainers.image.source="https://github.com/VeguiDev/yolks"
LABEL       org.opencontainers.image.licenses=MIT

RUN wget http://ftp2.scientificlinux.org/linux/scientific/6.0/x86_64/os/Packages/python-2.6.5-3.el6.x86_64.rpm \
    http://ftp2.scientificlinux.org/linux/scientific/6.0/x86_64/os/Packages/python-libs-2.6.5-3.el6.x86_64.rpm \
    http://ftp2.scientificlinux.org/linux/scientific/6.0/x86_64/os/Packages/python-iniparse-0.3.1-2.1.el6.noarch.rpm \
    http://ftp2.scientificlinux.org/linux/scientific/6.0/x86_64/os/Packages/pygpgme-0.1-18.20090824bzr68.el6.x86_64.rpm \
    http://ftp2.scientificlinux.org/linux/scientific/6.0/x86_64/os/Packages/python-urlgrabber-3.9.1-7.el6.noarch.rpm \
    http://ftp2.scientificlinux.org/linux/scientific/6.0/x86_64/os/Packages/python-pycurl-7.19.0-5.el6.x86_64.rpm \
    http://ftp2.scientificlinux.org/linux/scientific/6.0/x86_64/os/Packages/rpm-python-4.8.0-12.el6.x86_64.rpm \
    http://ftp2.scientificlinux.org/linux/scientific/6.0/x86_64/os/Packages/yum-3.2.27-14.el6.noarch.rpm \
    http://ftp2.scientificlinux.org/linux/scientific/6.0/x86_64/os/Packages/yum-metadata-parser-1.1.2-14.1.el6.x86_64.rpm

RUN rpm -Uhv py*.rpm \
    yum*.rpm \
    rpm-py*.rpm

RUN 				yum update \
    && yum install lsof curl ca-certificates openssl git tar sqlite3 fontconfig libfreetype6 tzdata iproute2 libstdc++6 \
    && useradd -d /home/container -m container

USER        container
ENV         USER=container HOME=/home/container
WORKDIR     /home/container

COPY        ./../entrypoint.sh /entrypoint.sh
CMD         [ "/bin/bash", "/entrypoint.sh" ]

