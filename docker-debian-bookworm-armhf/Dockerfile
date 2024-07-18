# syntax = docker/dockerfile:1.2

FROM debian:bookworm

RUN dpkg --add-architecture armhf

RUN apt-get update && apt-get install -y \
    autogen \
    automake \
    bash \
    bc \
    bison \
    build-essential \
    bzip2 \
    ca-certificates \
    ccache \
    chrpath \
    cpio \
    curl \
    diffstat \
    fakeroot \
    file \
    flex \
    gawk \
    gcc-arm-linux-gnueabihf \
    git \
    gzip \
    kmod \
    libgpiod-dev:armhf \
    libncursesw5-dev \
    libssl-dev \
    libtool \
    libyaml-dev \
    locales \
    lz4 \
    lzop \
    make \
    multistrap \
    ncurses-dev \
    pkg-config \
    python3 \
    python3-cbor \
    python3-pexpect \
    python3-pip \
    qemu-user-static \
    rsync \
    runit \
    socat \
    srecord \
    swig \
    texinfo \
    u-boot-tools \
    zstd \
    unzip \
    vim \
    wget \
    xz-utils

# Provide a more friendly name
ENV debian_chroot debian_bookworm
RUN echo "PS1='\${debian_chroot}\\[\033[01;32m\\]@\\H\[\\033[00m\\]:\\[\\033[01;34m\\]\\w\\[\\033[00m\\]\\$ '" >> /etc/bash.bashrc

# Set up locales
RUN sed -i -e 's/# en_US.UTF-8 UTF-8/en_US.UTF-8 UTF-8/' /etc/locale.gen && \
        echo 'LANG="en_US.UTF-8"'>/etc/default/locale && \
        dpkg-reconfigure --frontend=noninteractive locales && \
        update-locale LANG=en_US.UTF-8
ENV LC_ALL en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US.UTF-8
