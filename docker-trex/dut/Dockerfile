ARG UBUNTU_VERSION=20.04
FROM ubuntu:${UBUNTU_VERSION}

ARG ZEEK_VERSION=6.2.0
ARG DEBIAN_FRONTEND=noninteractive

RUN apt-get update &&\
    apt-get install -y --no-install-recommends \
    cmake \
    make \
    gcc \
    g++ \
    flex \
    bison \
    libpcap-dev \
    libfl-dev \
    libssl-dev \
    python3 \
    python3-dev \
    python3-git \
    python3-semantic-version \
    swig \
    zlib1g-dev \
    libjemalloc-dev \
    curl \
    iproute2 \
    tcpdump \
    wget \
    vim 

RUN wget --no-check-certificate https://download.zeek.org/zeek-${ZEEK_VERSION}.tar.gz &&\
    tar -zxvf zeek-${ZEEK_VERSION}.tar.gz -C / &&\
    rm zeek-${ZEEK_VERSION}.tar.gz &&\
    mkdir /opt/zeek &&\
    mkdir /traffic &&\
    chown tcpdump:tcpdump /traffic

RUN cd zeek-${ZEEK_VERSION} &&\
    ./configure --prefix=/opt/zeek/ &&\
    make && \
    make install

ENV PATH="/opt/zeek/bin:${PATH}"

WORKDIR /