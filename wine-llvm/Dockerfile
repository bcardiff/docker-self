# Image bcardiff/self:wine-llvm
FROM bcardiff/self:wine

# The published image is based on this Docker file
# but with LLVM-3.9.0-win64.exe installed by wine as follows:
#
# # wine LLVM-3.9.0-win64.exe
# # Installed at C:\LLVM-3.9.0\   ~/.wine/drive_c/LLVM-3.9.0

ADD http://releases.llvm.org/3.9.0/LLVM-3.9.0-win64.exe /home/user/

USER root
RUN chown user:user /home/user/LLVM-3.9.0-win64.exe
USER user
