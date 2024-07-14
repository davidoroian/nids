ARG UBUNTU_VERSION=20.04
FROM ubuntu:${UBUNTU_VERSION}

ARG TREX_VERSION=v3.04

RUN apt-get update &&\
    apt-get upgrade -y &&\
    apt-get install -y --no-install-recommends \
    iproute2 \
    iputils-ping \
    vim \
    tcpdump \
    net-tools \
    netbase \
    pciutils \
    python3 \
    python3-pip \
    python3-distutils \
    strace \
    wget &&\
    apt-get autoclean &&\
    apt-get autoremove -y &&\
    rm -rf /var/lib/apt/lists/*

RUN pip3 install --upgrade pip &&\
    pip3 install --no-cache-dir \
    pyyaml 

RUN wget --no-check-certificate https://trex-tgn.cisco.com/trex/release/${TREX_VERSION}.tar.gz && \
    tar -zxvf ${TREX_VERSION}.tar.gz -C / && \
    chown root:root /${TREX_VERSION}  && \
    rm ${TREX_VERSION}.tar.gz

COPY config.yaml /etc/trex_cfg.yaml

WORKDIR /${TREX_VERSION}
