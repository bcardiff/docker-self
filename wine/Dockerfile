# Image bcardiff/self:wine

# The published image is based on this Docker file after running ./winecfg
#
# $ docker run -e DISPLAY=<MY LOCAL IP>:0 -it bcardiff/self:wine bash
#

FROM ubuntu:14.04

# To use X11 in MAC
#  1. Open XQuarrts, Preferences, Security, [x] Allow connections from network clientes
#  2. `$ socat TCP-LISTEN:6000,reuseaddr,fork UNIX-CLIENT:\"$DISPLAY\"`
# Ref:
#  - http://kartoza.com/en/blog/how-to-run-a-linux-gui-application-on-osx-using-docker/
#  - https://github.com/docker/docker/issues/8710#issuecomment-72669844

RUN dpkg --add-architecture i386

RUN apt-get update && \
    apt-get install -y software-properties-common && \
    apt-get clean && rm -rf /var/lib/apt/lists/*

RUN add-apt-repository ppa:ubuntu-wine/ppa

RUN apt-get update && \
    apt-get install --no-install-recommends -y wine1.8 winetricks && \
    apt-get clean && rm -rf /var/lib/apt/lists/*

ENV DISPLAY :0

RUN echo "user ALL=NOPASSWD: ALL" >> /etc/sudoers

RUN useradd -ms /bin/bash user && adduser user sudo
USER user
ENV HOME /home/user
ENV WINEPREFIX /home/user/.wine
WORKDIR /home/user
