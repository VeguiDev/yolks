FROM        --platform=$TARGETOS/$TARGETARCH node:22-bookworm-slim

LABEL       author="Michael Parker" maintainer="parker@pterodactyl.io"

RUN         apt update \
    && apt -y install ffmpeg iproute2 git sqlite3 libsqlite3-dev python3 python3-dev ca-certificates dnsutils tzdata zip tar curl build-essential libtool iputils-ping libnss3 tini \
    && useradd -m -d /home/container container

RUN apt install -y \
    libatk-bridge2.0-0 \
    libgtk-3-0 \
    libx11-xcb1 \
    libnss3 \
    libxcomposite1 \
    libxdamage1 \
    libxrandr2 \
    libgbm1 \
    libasound2 \
    libpangocairo-1.0-0 \
    libcups2 \
    libxshmfence1 \
    libatspi2.0-0 \
    libatk1.0-0 \
    libdrm2 \
    libdbus-1-3 \
    libxss1 \
    fonts-liberation \
    libappindicator3-1 \
    libwayland-client0 \
    libwayland-cursor0 \
    libwayland-egl1 \
    libx11-6 \
    libxext6 \
    libxfixes3 \
    libxtst6 \
    libpci3 \
    ca-certificates \
    fonts-noto-color-emoji

RUN         npm install --global npm@latest typescript ts-node @types/node

USER        container
ENV         USER=container HOME=/home/container
WORKDIR     /home/container

STOPSIGNAL SIGINT

COPY        --chown=container:container ./../entrypoint.sh /entrypoint.sh
RUN         chmod +x /entrypoint.sh
ENTRYPOINT    ["/usr/bin/tini", "-g", "--"]
CMD         ["/entrypoint.sh"]