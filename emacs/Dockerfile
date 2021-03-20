FROM ubuntu:20.04
ENV DEBIAN_FRONTEND=noninteractive


# Install a bunch of build tools.
RUN	apt-get update \
    && apt-get install -y \
    git \
    sudo \
    unzip \
    emacs \
    && apt-get clean
