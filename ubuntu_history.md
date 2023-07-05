history

## install gcc-10.4.0
> sudo apt-get install m4
> sudo apt-get install tmux
> sudo apt-get install zlib1g-dev
> sudo apt-get install gcc-multilib
> wget https://mirrors.ustc.edu.cn/gnu/gmp/gmp-6.2.1.tar.xz
> wget https://mirrors.ustc.edu.cn/gnu/mpfr/mpfr-4.1.0.tar.gz
> wget https://mirrors.ustc.edu.cn/gnu/mpc/mpc-1.2.1.tar.gz

[源码编译gcc实录](https://blog.csdn.net/nahancy/article/details/127490943)

```shell
tar -Jxvf gmp-6.2.1.tar.xz 
cd ../gmp-6.2.1
./configure --prefix=/usr/local/gmp
make && make install
tar -zxvf mpfr-4.1.0.tar.gz 
cd ../mpfr-4.1.0
./configure --prefix=/usr/local/mpfr --with-gmp=/usr/local/gmp/
make && make install
tar -zxvf mpc-1.2.1.tar.gz
cd ../mpc-1.2.1
./configure --prefix=/usr/local/mpc --with-gmp=/usr/local/gmp/ --with-mpfr=/usr/local/mpfr/
make && make install

./configure --prefix=/usr/local/gcc10 \
--with-gmp=/usr/local/gmp/ \
--with-mpfr=/usr/local/mpfr/ \
--with-mpc=/usr/local/mpc/ \
--enable-languages=c,c++ \
--with-system-zlib \
--enable-multilib
```

```
./configure --prefix=/usr/local/gcc10 \
--with-gmp=/usr/local/gmp/ \
--with-mpfr=/usr/local/mpfr/ \
--with-mpc=/usr/local/mpc/ \
--enable-languages=c,c++ \
--with-system-zlib \
--disable-multilib \
--enable-threads=posix
```

```
./configure --disable-checking --enable-languages=c,c++ --disable-multilib --prefix=/home/yangs/gcc-10.4.0 --enable-threads=posix
```


## install network ssh
> sudo apt install net-tools

> sudo apt-get install ssh -y
> sudo apt install g++
> sudo apt install make
> sudo apt install git
> sudo apt install curl
> sudo apt install tee
> sudo apt install sz
