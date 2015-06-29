FROM buildpack-deps:wheezy

MAINTAINER Wu Ray

COPY tars/ /root/
ADD ftp://ftp.gmplib.org/pub/gmp-5.0.2/gmp-5.0.2.tar.bz2 /root/tars
ADD http://www.mpfr.org/mpfr-current/mpfr-3.1.3.tar.gz /root/tars
ADD http://www.multiprecision.org/mpC/download/mpc-0.9.tar.gz /root/tars
ADD http://ftpmirror.gnu.org/binutils/binutils-2.21.1.tar.bz2 /root/tars
ADD http://ftpmirror.gnu.org/gcc/gcc-4.6.4/gcc-core-4.6.4.tar.bz2 /root/tars
ADD http://ftpmirror.gnu.org/gdb/gdb-7.3.1.tar.bz2 /root/tars

RUN cd /root \
    && tar xjf gmp-5.0.2.tar.bz2 \
    && cd gmp-5.0.2 \
    && ./configure --prefix=/usr/local \
    && make \
    && make install \
    && cd .. \
    && tar xzf mpfr-3.1.3.tar.gz \
    && cd mpfr-3.1.3 \
    && ./configure --prefix=/usr/local \
    && make \
    && make install \
    && cd .. \
    && tar xzf mpc-0.9.tar.gz \
    && cd mpc-0.9 \
    && ./configure --prefix=/usr/local \
    && make \
    && make install \
    && cd .. \
    && tar xjf binutils-2.21.1.tar.bz2 \
    && cd binutils-2.21.1 \
    && ./configure --prefix=/usr/local --target=i386-jos-elf --disable-werror \
    && make \
    && make install \
    && cd .. 

RUN cd /root \
    && tar xjf gcc-core-4.6.4.tar.bz2 \
    && cd gcc-4.6.4 \
    && mkdir build \
    && cd build \
    && ../configure --prefix=/usr/local \
                    --target=i386-jos-elf --disable-werror \
                    --disable-libssp --disable-libmudflap --with-newlib \
                    --without-headers --enable-languages=c \
    && make all-gcc \
    && make install-gcc \
    && make all-target-libgcc \
    && make install-target-libgcc \
    && cd ../..

RUN cd /root \
    && tar xjf gdb-7.3.1.tar.bz2 \
    && cd gdb-7.3.1 \
    && ./configure --prefix=/usr/local --target=i386-jos-elf --program-prefix=i386-jos-elf- --disable-werror \
    && make all \
    && make install \
    && cd ..

RUN cd /root \
    && rm binutils-2.21.1.tar.bz2 && rm -rf binutils-2.21.1 \
    && rm gcc-core-4.6.4.tar.bz2 && rm -rf gcc-4.6.4 \
    && rm gdb-7.3.1.tar.bz2 && rm -rf gdb-7.3.1 \
    && rm gmp-5.0.2.tar.bz2 && rm -rf gmp-5.0.2 \
    && rm mpc-0.9.tar.gz && rm -rf mpc-0.9 \
    && rm mpfr-3.1.3.tar.gz && rm -rf mpfr-3.1.3


WORKDIR /tmp/xv6
