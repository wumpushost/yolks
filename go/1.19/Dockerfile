FROM --platform=$TARGETOS/$TARGETARCH golang:1.19

LABEL author="Jovan Jovanovic" maintainer="jovan@jovanovic.live"

LABEL org.opencontainers.image.source="https://github.com/j122j/yolks"
LABEL org.opencontainers.image.licenses=MIT

RUN apt update \
	&& apt -y install build-essential unzip curl wget git \
	&& useradd -m -d /home/container container

ENV GOPATH /home/container/.go
ENV PATH $GOPATH/bin:$PATH
RUN mkdir -p "$GOPATH/src" "$GOPATH/bin" && chmod -R 777 "$GOPATH"

USER container
ENV USER=container HOME=/home/container
WORKDIR /home/container

COPY ./../entrypoint.sh /entrypoint.sh
CMD [ "/bin/bash", "/entrypoint.sh" ]
