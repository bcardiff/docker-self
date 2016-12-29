# Image bcardiff/self:crystal-win-devel-0.20.3
FROM bcardiff/self:wine-llvm-mxe

RUN \
  apt-get update && \
  apt-get install -y apt-transport-https && \
  apt-key adv --keyserver keys.gnupg.net --recv-keys 09617FD37CC06B54 && \
  echo "deb https://dist.crystal-lang.org/apt crystal main" > /etc/apt/sources.list.d/crystal.list && \
  apt-get update && \
  apt-get install -y crystal gcc pkg-config libssl-dev libxml2-dev libyaml-dev libgmp-dev git make && \
  apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

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
# $ docker run --rm -it -e DISPLAY=192.168.0.138:0 -v $(pwd):/root/src bcardiff/self:crystal-win-devel-0.20.3 bash
#
# LLVM is installed at: ~/.wine/drive_c/LLVM

# # cd /root/src
# # echo 'puts "Hello Windows!"' > foo.cr
# # ./bin/crystal build foo.cr --ll --single-module --cross-compile --target x86_64-windows-gnu
