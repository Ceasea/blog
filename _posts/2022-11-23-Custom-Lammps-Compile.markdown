
Makefile name

> MAKE/Makefile.mpi

Add package

```make yes-packagename```

Like follows:

```make yes-reaxff```

```make ps ``` to check what packages will be installed.

Compile

```make -j 16 mpi```


## Makefile Changes:

fftw lib

> FFT_INC = -I/data/soft/fftw/v3.3.4_intel/ -DFFT_FFTW
> 
> FFT_PATH = -L/data/soft/fftw/v3.3.4_intel/lib
> 
> FFT_LIB = -lfftw3

mpi lib
> MPI_INC =   -DMPICH_SKIP_MPICXX -DOMPI_SKIP_MPICXX=1 -I/usr/mpi/gcc/mvapich2-1.9a2/include
> 
> MPI_PATH = -L/usr/mpi/gcc/mvapich2-1.9a2/lib
> 
> MPI_LIB = -lmpich -lmpl

尝试换了几个MPI lib, 目前这个可以正常编译通过.

编译通过后无法找到动态链接库, 即使增加了LD_library_PATH后也不行.(原因不明)

因此在编译时加入动态链接库地址

> MPI_LIB = $(MPI_PATH)/libmpich.a $(MPI_PATH)/libmpl.a /data/soft/compiler/intel/v2013/comp
oser_xe_2013_sp1.0.080/compiler/lib/intel64/libimf.a /usr/mpi/gcc/mvapich2-1.9a2/lib/libmp
ichcxx.a  /usr/mpi/gcc/mvapich2-1.9a2/lib/libmpichcxx.so.8
