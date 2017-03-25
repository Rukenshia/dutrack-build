FROM ubuntu:16.04
MAINTAINER Jan Christophersen <jan@ruken.pw>

# install required packages
RUN apt-get update && apt-get install -y curl git bash libcurl4-openssl-dev llvm gcc libpq-dev postgresql libsqlite3-dev libmysqlclient-dev

# install rustup
RUN curl https://sh.rustup.rs -sSf > install_rustup.sh
RUN chmod +x install_rustup.sh
RUN ./install_rustup.sh -y --default-toolchain=nightly-2017-03-04

# setup diesel_cli
ENV PATH=$PATH:/root/.cargo/bin
RUN cargo install diesel_cli

# start postgres service
ADD start.sh .
ENTRYPOINT ./start.sh && bash