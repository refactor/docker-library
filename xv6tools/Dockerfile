FROM buildpack-deps:wheezy

MAINTAINER Wu Ray

ENV GMP_VERSION=5.0.5
ADD https://gmplib.org/download/gmp/gmp-${GMP_VERSION}.tar.bz2 /root/tars/
RUN cd /root/tars \
    && tar xjf gmp-${GMP_VERSION}.tar.bz2 \
    && cd gmp-${GMP_VERSION} \
    && ./configure --prefix=/usr/local \
    && make \
    && make install

ENV MPFR_VERSION=3.1.3
ADD http://www.mpfr.org/mpfr-current/mpfr-${MPFR_VERSION}.tar.gz /root/tars/
RUN cd /root/tars \
    && tar xzf mpfr-${MPFR_VERSION}.tar.gz \
    && cd mpfr-${MPFR_VERSION} \
    && ./configure --prefix=/usr/local \
    && make \
    && make install

ENV MPC_VERSION=0.9
RUN cd /root/tars \
    && wget -c http://www.multiprecision.org/mpc/download/mpc-${MPC_VERSION}.tar.gz \
    && tar xzf mpc-${MPC_VERSION}.tar.gz \
    && cd mpc-${MPC_VERSION} \
    && ./configure --prefix=/usr/local \
    && make \
    && make install

ENV BINUTILS_VERSION=2.21.1
ADD http://ftpmirror.gnu.org/binutils/binutils-${BINUTILS_VERSION}.tar.bz2 /root/tars/
RUN cd /root/tars \
    && tar xjf binutils-${BINUTILS_VERSION}.tar.bz2 \
    && cd binutils-${BINUTILS_VERSION} \
    && ./configure --prefix=/usr/local --target=i386-jos-elf --disable-werror \
    && make \
    && make install

ENV GCC_VERSION 4.6.4
ADD http://ftpmirror.gnu.org/gcc/gcc-${GCC_VERSION}/gcc-core-${GCC_VERSION}.tar.bz2 /root/tars/
RUN cd /root/tars \
    && tar xjf gcc-core-${GCC_VERSION}.tar.bz2 \
    && cd gcc-${GCC_VERSION} \
    && mkdir build \
    && cd build \
    && ../configure --prefix=/usr/local \
                    --target=i386-jos-elf --disable-werror \
                    --disable-libssp --disable-libmudflap --with-newlib \
                    --without-headers --enable-languages=c \
    && make all-gcc \
    && make install-gcc \
    && make all-target-libgcc \
    && make install-target-libgcc

ENV GDB_VERSION 7.3.1
ADD http://ftpmirror.gnu.org/gdb/gdb-${GDB_VERSION}.tar.bz2 /root/tars/
RUN cd /root/tars \
    && tar xjf gdb-${GDB_VERSION}.tar.bz2 \
    && cd gdb-${GDB_VERSION} \
    && ./configure --prefix=/usr/local --target=i386-jos-elf --program-prefix=i386-jos-elf- --disable-werror \
    && make all \
    && make install

RUN rm -rf /root/tars


WORKDIR /tmp/xv6
