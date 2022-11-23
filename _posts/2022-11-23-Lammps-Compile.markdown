# Lammps compile 

Makefile name

> MAKE/Makefile.mpi

Add package

```make yes-packagename```

Like follows:

```make yes-reaxff```

```make ps ``` to check what packages will be installed.

Compile

```make -j 16 mpi```


# Makefile Changes:
## fftw lib

FFT_INC = -I/data/soft/fftw/v3.3.4_intel/ -DFFT_FFTW

FFT_PATH = -L/data/soft/fftw/v3.3.4_intel/lib

FFT_LIB = -lfftw3

## mpi lib
MPI_INC =   -DMPICH_SKIP_MPICXX -DOMPI_SKIP_MPICXX=1 -I/usr/mpi/gcc/mvapich2-1.9a2/include

MPI_PATH = -L/usr/mpi/gcc/mvapich2-1.9a2/lib

MPI_LIB = -lmpich -lmpl
