# Image bcardiff/self:wine-llvm38
FROM bcardiff/self:wine

# The published image is based on this Docker file
# but with LLVM-3.8.1-win64.exe installed by wine as follows:
#
# # wine LLVM-3.8.1-win64.exe
# # Installed at C:\LLVM-3.8.1\   ~/.wine/drive_c/LLVM-3.8.1

ADD http://releases.llvm.org/3.8.1/LLVM-3.8.1-win64.exe /home/user/

USER root
RUN chown user:user /home/user/LLVM-3.8.1-win64.exe
USER user
