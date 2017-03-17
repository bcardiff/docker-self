# Image bcardiff/self:wine-llvm38-mxe
FROM bcardiff/self:wine-llvm38

USER root

RUN apt-get update && \
    apt-get install -y \
    autoconf automake autopoint bash bison bzip2 flex gettext \
    git g++ gperf intltool libffi-dev libgdk-pixbuf2.0-dev \
    libtool libltdl-dev libssl-dev libxml-parser-perl make \
    openssl p7zip-full patch perl pkg-config python ruby scons \
    sed unzip wget xz-utils \
    g++-multilib libc6-dev-i386 \
    libtool-bin && \
    apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

USER user

RUN cd /home/user && \
    git clone https://github.com/lbguilherme/mxe.git && \
    cd mxe && \
    git checkout updated-gc && \
    make MXE_TARGETS=x86_64-w64-mingw32.static gcc gc libevent libiconv
