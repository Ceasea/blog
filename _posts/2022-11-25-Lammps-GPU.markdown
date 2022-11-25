## Install CUDA on WSL2

1. update Windows to 21H2 version as least
2. reboot
3. Install NVidia dirver in Windows, https://www.nvidia.com/Download/index.aspx?lang=en-us
4. Install CUDA-toolkit in wsl2, https://docs.nvidia.com/cuda/wsl-user-guide/index.html#installing-nvidia-drivers
5. CUDA should be /usr/local/cuda in your wls2. Add export PATH=$PATH:/usr/local/cuda in ~/.bashrc and source ~/.bashrc

## Build GPU lib in Lammps/src

Every time build gpu lib, run following command

```make no-gpu```

```make yes-gpu```

### Build gpu lib command

```make lib-gpu args="-m mpi -a sm_60 -p mixed -b" # build GPU library with mixed precision and P100 using other settings in Makefile.mpi```

## Build Lammps

```make mpi -j 16```

## Use GPU in Lammps

### Note 

1. Ensure the Lammps potential support GPU.

    Potetials like MEAM, reaxff need newton pair on while GPU need newton pair off, therefore, GPU can not use in such case.

2. input file

    ```package gpu 0 neigh no```

### Command

```/home/ceasea/software/lammps-23Jun2022/src/lmp_mpi -sf gpu -pk gpu 1 -in in.CHO```



