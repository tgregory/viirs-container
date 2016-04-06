FROM ubuntu:trusty

COPY MCR_R2013a_glnxa64_installer.zip /mcr-install/MCR.zip

RUN apt-get -qq update && apt-get -qq install -y unzip \
    && mkdir /opt/mcr \
    && cd /mcr-install \
    && unzip MCR.zip \
    && rm MCR.zip \
    && ./install -destinationFolder /opt/mcr -agreeToLicense yes -mode silent \
    && cd / \
    && rm -rf mcr-install
