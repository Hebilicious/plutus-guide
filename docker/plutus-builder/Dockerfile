# syntax=docker/dockerfile:1.2
FROM haskell:8.10.7

RUN apt-get update
RUN apt-get install -y libtool pkg-config

WORKDIR /home/plutus
RUN git clone https://github.com/input-output-hk/libsodium.git

WORKDIR /home/plutus/libsodium
RUN git checkout 66f017f1
RUN ./autogen.sh
RUN ./configure
RUN make
RUN make install
ENV LD_LIBRARY_PATH="/usr/local/lib:$LD_LIBRARY_PATH"
ENV PKG_CONFIG_PATH="/usr/local/lib/pkgconfig:$PKG_CONFIG_PATH"

WORKDIR /home/builder
