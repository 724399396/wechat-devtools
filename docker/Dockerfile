FROM ubuntu:20.04

ENV LANG=C.UTF-8

# update repo sources
RUN set -ex; \
    cp /etc/apt/sources.list /etc/apt/sources.list.bak; \
    echo "deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal main restricted universe multiverse" > /etc/apt/sources.list; \
    echo "deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal-security main restricted universe multiverse" >> /etc/apt/sources.list; \
    echo "deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal-updates main restricted universe multiverse" >> /etc/apt/sources.list; \
    echo "deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal-proposed main restricted universe multiverse" >> /etc/apt/sources.list; \
    echo "deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal-backports main restricted universe multiverse" >> /etc/apt/sources.list; \
    apt-get clean; \
    dpkg --add-architecture i386; \
    apt-get update;

RUN set -ex; \
    DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends \
        apt-utils \
        dbus-x11 \
        libasound2 \
        libatk1.0-0 \
        libatomic1 \
        libcanberra-gtk3-module \
        libgconf-2-4 \
        libgtk3.0 \
        libnss3 \
        libupower-glib3 \
        libxtst6 \
        libx11-6 \
        libx11-xcb1 \
        libxss1 \
        libxrandr2 \
        mesa-utils \
        ttf-wqy-microhei \
        upower \
        wine \
        wine32 \
        wine-binfmt \
        xserver-xorg-video-all;

ADD wechat-devtools-1.03.2009140-compact.tar.gz /opt/wechat/devtools

COPY docker-entrypoint /opt/wechat/devtools/bin/docker-entrypoint

# COPY spdlog.docker.node /opt/wechat/devtools/package.nw/node_modules/spdlog/build/Release/spdlog.node
# COPY spdlog.docker.node /opt/wechat/devtools/package.nw/node_modules/spdlog-node/build/Release/spdlog.node

# RUN apt-get build-essential python libx11-dev pkg-config libxkbfile-dev
# RUN useradd -m minun

# xhost +
# docker run -t -i --rm -v /tmp/.X11-unix:/tmp/.X11-unix -e DISPLAY=$DISPLAY -v $HOME/.Xauthority:/root/.Xauthority wechat-devtools bash

