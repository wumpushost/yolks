FROM --platform=$TARGETOS/$TARGETARCH debian:stable-slim

LABEL author="Jovan Jovanovic" maintainer="jovan@jovanovic.live"

ENV TZ=UTC
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ >/etc/timezone

RUN apt update \
	&& apt -y install ffmpeg iproute2 git sqlite3 libsqlite3-dev python3 python3-dev ca-certificates dnsutils tzdata zip tar curl build-essential libtool \
	&& useradd -m -d /home/container container

ENV BUN_INSTALL=/opt/bun
RUN curl https://bun.sh/install | bash
ENV PATH=$BUN_INSTALL/bin:$PATH

USER container
ENV USER=container HOME=/home/container
WORKDIR /home/container

COPY ./../entrypoint.sh /entrypoint.sh
ENTRYPOINT [ "/bin/bash", "/entrypoint.sh" ]
CMD [ "bun" ]
