# Image bcardiff/self:wine-llvm
FROM bcardiff/self:wine

# The published image is based on this Docker file
# but with LLVM-3.9.0-win64.exe installed by wine as follows:
#
# # wine LLVM-3.9.0-win64.exe
# # C:\LLVM\ and adding it to the (windows) path for all users

ADD http://releases.llvm.org/3.9.0/LLVM-3.9.0-win64.exe /home/user/
RUN sudo chown user:user /home/user/LLVM-3.9.0-win64.exe
