FROM --platform=$TARGETOS/$TARGETARCH node:18-bullseye-slim

LABEL author="Michael Parker" maintainer="parker@pterodactyl.io"

RUN apt update \
	&& apt -y install pkg-config ffmpeg iproute2 git sqlite3 libsqlite3-dev python3 python3-dev ca-certificates dnsutils tzdata zip tar curl build-essential libtool libcairo2-dev libpango1.0-dev libjpeg-dev libgif-dev librsvg2-dev \
#	&& npm -g install npm@latest \
	&& useradd -m -d /home/container container

USER container
ENV USER=container HOME=/home/container
WORKDIR /home/container

COPY ./../entrypoint.sh /entrypoint.sh
CMD [ "/bin/bash", "/entrypoint.sh" ]
