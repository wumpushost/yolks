FROM        --platform=$TARGETOS/$TARGETARCH debian:stable-slim

LABEL       author="Jovan Jovanovic" maintainer="jovan@jovanovic.live"

LABEL       org.opencontainers.image.source="https://github.com/j122j/yolks"
LABEL       org.opencontainers.image.licenses=MIT

RUN         apt update \
	&& apt -y install build-essential libreadline-dev unzip curl wget git cmake \
	&& useradd -m -d /home/container container

RUN         cd /opt \
	&& curl -R -O http://www.lua.org/ftp/lua-5.4.4.tar.gz \
	&& tar zxf lua-5.4.4.tar.gz \
	&& cd lua-5.4.4 \
	&& make linux test \
	&& make install

RUN         cd /opt \
	&& wget https://luarocks.github.io/luarocks/releases/luarocks-3.9.1.tar.gz \
	&& tar zxpf luarocks-3.9.1.tar.gz \
	&& cd luarocks-3.9.1 \
	&& ./configure --with-lua-include=/usr/local/include \
	&& make \
	&& make install

RUN         cd /opt \
	&& git clone --recursive https://github.com/luvit/luvi.git \
	&& cd luvi \
	&& make regular \
	&& make test \
	&& make install

RUN         cd /opt \
	&& git clone --recursive https://github.com/luvit/lit.git lit \
	&& cd lit \
	&& luvi . -- make . /usr/local/bin/lit /usr/local/bin/luvi \
	&& lit make github://luvit/luvit /usr/local/bin/luvit /usr/local/bin/luvi


USER        container
ENV         USER=container HOME=/home/container
WORKDIR     /home/container

COPY        ./../entrypoint.sh /entrypoint.sh
CMD         [ "/bin/bash", "/entrypoint.sh" ]
