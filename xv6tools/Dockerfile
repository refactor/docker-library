FROM buildpack-deps:wheezy

MAINTAINER Wu Ray

ENV tmp_dir=/root/

ENV GMP_VERSION=5.0.5
RUN cd ${tmp_dir} \
    && wget -c https://gmplib.org/download/gmp/gmp-${GMP_VERSION}.tar.bz2 \
    && tar xjf gmp-${GMP_VERSION}.tar.bz2 \
    && cd gmp-${GMP_VERSION} \
    && ./configure --prefix=/usr/local \
    && make \
    && make install \
    && cd ${tmp_dir} \
    && rm gmp-${GMP_VERSION}.tar.bz2 \
    && rm -rf gmp-${GMP_VERSION}

ENV MPFR_VERSION=3.1.3
RUN cd ${tmp_dir} \
    && wget -c http://www.mpfr.org/mpfr-current/mpfr-${MPFR_VERSION}.tar.gz \
    && tar xzf mpfr-${MPFR_VERSION}.tar.gz \
    && cd mpfr-${MPFR_VERSION} \
    && ./configure --prefix=/usr/local \
    && make \
    && make install \
    && cd ${tmp_dir} \
    && rm  mpfr-${MPFR_VERSION}.tar.gz \
    && rm -rf mpfr-${MPFR_VERSION}

ENV MPC_VERSION=0.9
RUN cd ${tmp_dir} \
    && wget -c http://www.multiprecision.org/mpc/download/mpc-${MPC_VERSION}.tar.gz \
    && tar xzf mpc-${MPC_VERSION}.tar.gz \
    && cd mpc-${MPC_VERSION} \
    && ./configure --prefix=/usr/local \
    && make \
    && make install \
    && cd ${tmp_dir} \
    && rm mpc-${MPC_VERSION}.tar.gz \
    && rm -rf mpc-${MPC_VERSION}

ENV BINUTILS_VERSION=2.21.1
RUN cd ${tmp_dir} \
    && wget -c http://ftpmirror.gnu.org/binutils/binutils-${BINUTILS_VERSION}.tar.bz2 \
    && tar xjf binutils-${BINUTILS_VERSION}.tar.bz2 \
    && cd binutils-${BINUTILS_VERSION} \
    && ./configure --prefix=/usr/local --target=i386-jos-elf --disable-werror \
    && make \
    && make install \
    && cd ${tmp_dir} \
    && rm binutils-${BINUTILS_VERSION}.tar.bz2 \
    && rm -rf binutils-${BINUTILS_VERSION}

ENV GCC_VERSION=4.6.4
RUN cd ${tmp_dir} \
    && wget -c http://ftpmirror.gnu.org/gcc/gcc-${GCC_VERSION}/gcc-core-${GCC_VERSION}.tar.bz2 \
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
    && make install-target-libgcc \
    && cd ${tmp_dir} \
    && rm gcc-core-${GCC_VERSION}.tar.bz2 \
    && rm -rf gcc-${GCC_VERSION}

ENV GDB_VERSION=7.3.1
RUN cd ${tmp_dir} \
    && wget -c http://ftpmirror.gnu.org/gdb/gdb-${GDB_VERSION}.tar.bz2 \
    && tar xjf gdb-${GDB_VERSION}.tar.bz2 \
    && cd gdb-${GDB_VERSION} \
    && ./configure --prefix=/usr/local --target=i386-jos-elf --program-prefix=i386-jos-elf- --disable-werror \
    && make all \
    && make install \
    && cd ${tmp_dir} \
    && rm gdb-${GDB_VERSION}.tar.bz2 \
    && rm -rf gdb-${GDB_VERSION}

RUN rm -rf ${tmp_dir}


WORKDIR /tmp/xv6
