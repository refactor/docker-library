#Compiler Toolchain used for MIT6.828: Operating System Engineering

This Dockfile include compiler tools used in 6.828, include gcc, gdb

[Tools Used in 6.828](http://pdos.csail.mit.edu/6.828/2014/tools.html) 


## How to use this image

shell1 $ make qemu-gdb

shell2 $ docker run -ti --rm  -v /tmp/xv6:/tmp/xv6 wulei/xv6tools i386-jos-elf-gdb



