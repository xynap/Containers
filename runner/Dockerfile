FROM --platform=$TARGETOS/$TARGETARCH ubuntu:22.04

ENV DEBIAN_FRONTEND noninteractive
RUN apt-get update && apt-get upgrade -y
RUN apt-get install -y --no-install-recommends \
    build-essential \
    curl \
    dotnet-sdk-8.0 \
    git \
    golang \
    iproute2 \
    jq \
    nodejs \
    npm \
    python3 \
    python3-pip \
    rust-all \
    tini

RUN useradd -m -d /home/container -s /bin/bash container
USER container
ENV USER=container HOME=/home/container
WORKDIR /home/container

STOPSIGNAL SIGINT
COPY --chmod=755 ./entrypoint.sh /entrypoint.sh
ENTRYPOINT ["/usr/bin/tini", "-g", "--"]
CMD ["/entrypoint.sh"]
