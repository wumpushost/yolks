FROM --platform=$TARGETOS/$TARGETARCH eclipse-temurin:8-jre

LABEL author="Yaj" maintainer="yaj@hss.gg"


LABEL org.opencontainers.image.source="https://github.com/wumpushost/yolks"
LABEL org.opencontainers.image.licenses=MIT

RUN apt update -y \
	&& apt install -y curl ca-certificates openssl git tar sqlite3 fontconfig tzdata iproute2 libfreetype6 \
	&& useradd -d /home/container -m container

USER container
ENV USER=container HOME=/home/container
WORKDIR /home/container

COPY ./../entrypoint.sh /entrypoint.sh
CMD [ "/bin/bash", "/entrypoint.sh" ]
