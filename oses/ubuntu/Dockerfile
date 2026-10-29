FROM --platform=$TARGETOS/$TARGETARCH ubuntu:24.04

LABEL author="Michael Parker" maintainer="parker@pterodactyl.io"

ENV DEBIAN_FRONTEND noninteractive

## add container user
RUN useradd -m -d /home/container -s /bin/bash container

## update base packages
RUN apt update \
	&& apt upgrade -y

RUN apt-get update && apt-get install -y --no-install-recommends \
    gcc g++ libc++-dev gdb libc6 git wget curl tar zip unzip binutils xz-utils \
    liblzo2-2 cabextract iproute2 net-tools netcat-openbsd telnet libatomic1 \
    libsdl1.2debian libsdl2-2.0-0 libfontconfig1 libicu74 icu-devtools libunwind8 \
    libssl3t64 libssl-dev sqlite3 libsqlite3-dev libmariadb-dev-compat \
    libduktape207 libzip4t64 locales ffmpeg apt-transport-https init-system-helpers \
    libcurl3t64-gnutls libjsoncpp25 libleveldb1d liblua5.1-0 libluajit-5.1-2 \
    libsqlite3-0 libfluidsynth3 bzip2 zlib1g libevent-dev \
    && rm -rf /var/lib/apt/lists/*

## configure locale
RUN update-locale lang=en_US.UTF-8 \
	&& dpkg-reconfigure --frontend noninteractive locales

WORKDIR /home/container

COPY ./entrypoint.sh /entrypoint.sh
CMD [ "/bin/bash", "/entrypoint.sh" ]
