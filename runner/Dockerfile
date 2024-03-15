FROM --platform=$TARGETOS/$TARGETARCH ghcr.io/parkervcp/yolks:ubuntu

ENV DEBIAN_FRONTEND noninteractive
RUN apt-get update && apt-get upgrade -y
RUN apt-get install -y --no-install-recommends \
    build-essential \
    dotnet-sdk-8.0 \
    golang \
    jq \
    nodejs \
    npm \
    openjdk-21-jdk-headless \
    python3 \
    python3-pip \
    ruby \
    rust-all

WORKDIR /home/container
COPY --chown=container:container ./entrypoint.sh /entrypoint.sh
RUN  chmod +x /entrypoint.sh

STOPSIGNAL SIGINT
ENTRYPOINT ["/usr/bin/tini", "-g", "--"]
CMD ["/entrypoint.sh"]
