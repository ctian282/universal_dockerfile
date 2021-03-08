# FILE: Dockerfile


FROM ubuntu:20.04
ENV DEBIAN_FRONTEND=noninteractive


# Install a bunch of build tools.
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
    libhdf5-dev\
    libboost-all-dev\
    #python essential
    python3\
    python3-pip\
    python-numpy\
    # some basic shell commands...
    bc\
    sed

# pip install python packages
RUN pip3 install healpy
RUN pip3 install cython
RUN pip3 install mpi4py
RUN pip3 install nbodykit
RUN pip3 install "dask[array]"
