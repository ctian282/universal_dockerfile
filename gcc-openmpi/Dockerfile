# FILE: Dockerfile


FROM ubuntu:18.04
ENV DEBIAN_FRONTEND=noninteractive


# Install a bunch of build shit.
RUN	apt-get update \
	&& apt-get install -y \
		build-essential \
		cmake \
		git \
		sudo \
		unzip \
		emacs \
		wget \
    #lpcola env
    libopenmpi-dev\
    libhealpix-cxx-dev\
    libfftw3-mpi-dev\
    libfftw3-dev\
    libgsl-dev\
#DTFE
    libboost1.65-all-dev\
    libcgal-dev\
