# Image bcardiff/self:crystal-win-devel38
FROM bcardiff/self:wine-llvm38-mxe

USER root

RUN \
  apt-get update && \
  apt-get install -y apt-transport-https && \
  apt-key adv --keyserver keys.gnupg.net --recv-keys 09617FD37CC06B54 && \
  echo "deb https://dist.crystal-lang.org/apt crystal main" > /etc/apt/sources.list.d/crystal.list && \
  wget -O - http://apt.llvm.org/llvm-snapshot.gpg.key | apt-key add - && \
  echo "deb http://apt.llvm.org/xenial/ llvm-toolchain-xenial main" > /etc/apt/sources.list.d/llvm.list && \
  apt-get update && \
  apt-get install -y crystal gcc pkg-config libssl-dev libxml2-dev \
          libyaml-dev libgmp-dev git make apt-transport-https curl \
          build-essential llvm-3.8 libedit-dev libreadline-dev git-core && \
  apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

USER user

CMD ["bash"]

# In host you can checkout the source
# $ git clone https://github.com/lbguilherme/crystal.git win
# $ cd win/
# $ git checkout win

# To use X11 in MAC
#  1. Open XQuarrts, Preferences, Security, [x] Allow connections from network clientes
#  2. `$ socat TCP-LISTEN:6000,reuseaddr,fork UNIX-CLIENT:\"$DISPLAY\"`
# Ref:
#  - http://kartoza.com/en/blog/how-to-run-a-linux-gui-application-on-osx-using-docker/
#  - https://github.com/docker/docker/issues/8710#issuecomment-72669844

# Start a docker container to work on that code from your `win` checkout.
# $ docker run --rm -it -e DISPLAY=192.168.0.138:0 -v $(pwd):/home/user/src bcardiff/self:crystal-win-devel bash
#
# LLVM is installed at: ~/.wine/drive_c/LLVM-3.8.1

# # cd /home/user/src
# # echo 'puts "Hello Windows!"' > foo.cr
# # ./bin/crystal build foo.cr --ll --single-module --cross-compile --target x86_64-windows-gnu
