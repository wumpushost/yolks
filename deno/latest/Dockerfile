FROM        --platform=$TARGETOS/$TARGETARCH debian:bullseye-slim

LABEL       author="Jovan Jovanovic" maintainer="jovan@lightbulb.host"

RUN         apt update \
	&& apt -y install ffmpeg iproute2 git sqlite3 libsqlite3-dev python3 python3-dev ca-certificates dnsutils tzdata zip tar curl build-essential libtool \
	&& useradd -m -d /home/container container

ENV 	   DENO_INSTALL="/usr/local"
ENV 	   PATH="$DENO_INSTALL/bin:$PATH"

RUN curl -s https://gist.githubusercontent.com/LukeChannings/09d53f5c364391042186518c8598b85e/raw/ac8cd8c675b985edd4b3e16df63ffef14d1f0e24/deno_install.sh | sh

USER        container
ENV         USER=container HOME=/home/container
WORKDIR     /home/container

COPY        ./../entrypoint.sh /entrypoint.sh
CMD         [ "/bin/bash", "/entrypoint.sh" ]
