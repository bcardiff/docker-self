# Image bcardiff/self:wine

# The published image is based on this Docker file after running ./winecfg
#
# $ docker run -e DISPLAY=<MY LOCAL IP>:0 -it bcardiff/self:wine bash
#

FROM ubuntu:16.04

# To use X11 in MAC
#  1. Open XQuarrts, Preferences, Security, [x] Allow connections from network clientes
#  2. `$ socat TCP-LISTEN:6000,reuseaddr,fork UNIX-CLIENT:\"$DISPLAY\"`
# Ref:
#  - http://kartoza.com/en/blog/how-to-run-a-linux-gui-application-on-osx-using-docker/
#  - https://github.com/docker/docker/issues/8710#issuecomment-72669844

ENV DEBIAN_FRONTEND noninteractive

RUN echo "user ALL=NOPASSWD: ALL" >> /etc/sudoers
RUN useradd -ms /bin/bash user && adduser user sudo

# based on https://github.com/webanck/docker-wine-steam
RUN dpkg --add-architecture i386 && \
    apt-get update && \
    apt-get install -y software-properties-common && \
    add-apt-repository ppa:wine/wine-builds && \
    apt-get update && \
    apt-get install -y --install-recommends winehq-devel cabextract unzip p7zip wget zenity xvfb && \
    wget https://raw.githubusercontent.com/Winetricks/winetricks/master/src/winetricks && chmod ugo+x winetricks && mv winetricks /usr/local/bin && \
    su user -c winecfg && \
    # su user -c 'xvfb-run -a winetricks -q corefonts' && \
    # su user -c 'xvfb-run -a winetricks -q dotnet20' && \
    # su user -c 'xvfb-run -a winetricks -q dotnet40' && \
    apt-get autoremove -y --purge software-properties-common && \
    apt-get autoremove -y --purge xvfb && \
    apt-get clean -y && \
    rm -rf /home/wine/.cache && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

USER user
ENV HOME /home/user
WORKDIR /home/user
