FROM --platform=$TARGETOS/$TARGETARCH denoland/deno:debian

LABEL author="Yaj" maintainer="yaj@hss.gg"

USER root

RUN apt-get update \
	&& apt-get -y install --no-install-recommends ffmpeg iproute2 git sqlite3 libsqlite3-dev python3 python3-dev ca-certificates dnsutils tzdata zip tar curl build-essential libtool \
	&& rm -rf /var/lib/apt/lists/* \
	&& useradd -m -d /home/container container

USER container
ENV USER=container HOME=/home/container DENO_DIR=/home/container/.cache/deno
WORKDIR /home/container

COPY ./../entrypoint.sh /entrypoint.sh

ENTRYPOINT []
CMD [ "/bin/bash", "/entrypoint.sh" ]
