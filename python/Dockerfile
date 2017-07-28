FROM ubuntu:14.04
MAINTAINER odarbelaeze@gmail.com

ENV ROOT_TAR="root_v6.08.04.Linux-ubuntu14-x86_64-gcc4.8.tar.gz"
ENV ROOT_DL="https://root.cern.ch/download/$ROOT_TAR"

ENV ROOTSYS="/cern/root/"
ENV PATH="$ROOTSYS/bin:$PATH"
ENV LD_LIBRARY_PATH="$ROOTSYS/lib:$LD_LIBRARY_PATH"
ENV PYTHONPATH="$ROOTSYS/lib:$PYTHONPATH"

RUN apt-get update && apt-get upgrade -y &&\
    apt-get install --no-install-recommends --no-install-suggests -y \
                                            git dpkg-dev make g++ gcc gfortran \
                                            binutils libx11-dev libxpm-dev libxft-dev \
                                            libxext-dev libpng12-dev libjpeg-turbo8-dev \
                                            gfortran libssl-dev wget \
                                            python-dev python-pip python-numpy python-matplotlib \
    && pip install click docopt \
    && mkdir /cern && cd /cern \
    && wget -nv --no-check-certificate $ROOT_DL \
    && apt-get purge -y wget && apt-get autoremove -y && apt-get clean \
    && rm -rf /var/lib/apt/lists/* \
    && tar xzf $ROOT_TAR \
    && rm -rf $ROOT_TAR

ADD run-root /usr/local/sbin/run-root

WORKDIR /tmp/
