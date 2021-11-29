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
    wget  \
    gfortran


# Copy in minimal LSF components for openMPI build.
ADD lsf /tmp/lsf

# Setup the temporary LSF paths
ARG LSF_ENVDIR=/tmp/lsf/conf
ARG LSF_LIBDIR=/tmp/lsf/10.1/lib


ARG OMPI_VER="4.0.3"
# Compile openmpi with LSF
RUN mkdir /tmp/openmpi && \
    cd /tmp/openmpi && \
    wget https://www.open-mpi.org/software/ompi/v4.0/downloads/openmpi-$OMPI_VER.tar.gz && \
    tar zxf openmpi-$OMPI_VER.tar.gz && \
    cd openmpi-$OMPI_VER && \
    ./configure --prefix=/usr --enable-orterun-prefix-by-default --disable-getpwuid --with-lsf=/tmp/lsf/10.1 --with-lsf-libdir=/tmp/lsf/10.1/lib && \
    make -j $(nproc) all && \
    make install && \
    ldconfig && \
    rm -rf /tmp/openmpi


# copy lsf lib to /usr/lib
RUN cp /tmp/lsf/10.1/lib/lib* /usr/lib/



RUN mkdir /tmp/fftw3 && \
    cd /tmp/fftw3 && \
    wget https://www.fftw.org/fftw-3.3.10.tar.gz && \
    tar zxf fftw-3.3.10.tar.gz && \
    cd fftw-3.3.10 && \
    ./configure --prefix=/usr --enable-mpi --enable-float --enable-openmp&& \
    make -j $(nproc) all && \
    make install && \
    rm -rf /tmp/fftw3    

RUN mkdir /tmp/fftw3 && \
    cd /tmp/fftw3 && \
    wget https://www.fftw.org/fftw-3.3.10.tar.gz && \
    tar zxf fftw-3.3.10.tar.gz && \
    cd fftw-3.3.10 && \
    ./configure --prefix=/usr --enable-mpi --enable-openmp&& \
    make -j $(nproc) all && \
    make install && \
    rm -rf /tmp/fftw3    


# Clean up
RUN rm -rf /tmp/lsf
RUN rm -rf /tmp/hello-world

RUN apt-get install -y \
    libhealpix-cxx-dev\
    libgsl-dev\
    libhdf5-dev\
    #python essential
    python3\
    python3-pip\
    python-numpy\
    # some basic shell commands...
    bc\
    sed

# # pip install python packages
# RUN pip3 install healpy
# RUN pip3 install cython
# RUN pip3 install mpi4py
# RUN pip3 install nbodykit
# RUN pip3 install "dask[array]"
# RUN pip3 install dill
