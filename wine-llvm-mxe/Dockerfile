# Image bcardiff/self:wine-llvm-mxe-deps
# is match this Dockerfile
#
# Image bcardiff/self:wine-llvm-mxe
# matches after running:
# ```
# git clone https://github.com/lbguilherme/mxe.git
# git checkout updated-gc
# # Check http://mxe.cc/#requirements for a list of dependencies
# # (or just run the comand below and get an error listing what is missing)
# make MXE_TARGETS=x86_64-w64-mingw32.static gcc gc libevent libiconv # This will take some considerable time
# ```
#
FROM bcardiff/self:wine-llvm

USER root

RUN apt-get update && \
    apt-get install -y \
    autoconf automake autopoint bash bison bzip2 flex gettext \
    git g++ gperf intltool libffi-dev libgdk-pixbuf2.0-dev \
    libtool libltdl-dev libssl-dev libxml-parser-perl make \
    openssl p7zip-full patch perl pkg-config python ruby scons \
    sed unzip wget xz-utils \
    g++-multilib libc6-dev-i386 \
    libtool && \
    apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
# for 16.04 libtool-bin

USER user
