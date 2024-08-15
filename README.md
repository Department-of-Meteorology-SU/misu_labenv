# MISU Computer-Lab Environments

+ Ezra Eisbrenner (August 2024)
+ Ezra Eisbrenner (December 2023)

## Windows

1. for FORTRAN install a Linux in a virtual machine and follow the instructions for Linux
   + but, you are welcome to give feedback on the use of [WSL](https://learn.microsoft.com/en-us/windows/wsl/install) v2 (Windows Subsystem for Linux version 2). The steps for Linux below should work 1-to-1 on WSLv2. 
2. for Python you can
   + install the [Anaconda suite](https://docs.anaconda.com/free/anaconda/install/windows/), it is slow but works (you can find a list of recommended packages in the MacOS and Linux section below)
   + or follow this [miniforge installation guide for Windows](https://github.com/conda-forge/miniforge?tab=readme-ov-file#windows)
   + or work within the virtual maschine too, then follow the instructions for Linux
  
## MacOS

1. install Homebrew (https://brew.sh) and run the brew commands, given here and in the other sections, in your terminal
2. if you want python, then
   * `brew install --cask mambaforge`
   * see `https://formulae.brew.sh/cask/mambaforge` for more information
   * If in doubt, look for the `conda`/`mamba` executable with `brew info mambaforge`
3. if you want FORTRAN, follow the FORTRAN instructions below.

## Linux

1. if you want python, then
   * unfortunately, `--cask` is not supported on Linux, thus Mamba has to be installed the conventional ways
   * see here https://mamba.readthedocs.io/en/latest/installation/mamba-installation.html
   * they send you here https://github.com/conda-forge/miniforge
   * which will tell you to do `curl -L -O "https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-$(uname)-$(uname -m).sh"` then `bash Miniforge3-$(uname)-$(uname -m).sh`
* if you want FORTRAN, install Homebrew (https://brew.sh) and follow the FORTRAN instructions below.

## Python Environment

Create the MISU conda environment with the shell (bash) command below

```
mamba create         `# mamba is faster than conda` \
      -n misu_pyenv  `# name of new conda environment` \
      -c conda-forge `# channel from where to pull packages` \
      "python<3.10"  `# proplot does not support python > 3.10 as of December 2023` \
                     `# cartopy does not support python > 3.9 as of January 2024 with these dependencies` \
      dynaconf       `# advanced project settings` \
      jupyter        `# for notebooks and interactive vscode` \
      dask           `# for parallel workflows like xarray.open_mfdataset` \
      h5netcdf       `# another backend for NetCDF` \
      numpy          `# math` \
      scipy          `# math` \
      xarray         `# dimensional data` \
      pandas         `# tabular data` \
      f90nml         `# fortran namelist handling` \
      proplot        `# plotting with sensible defaults (restricts matplotlib<3.5 as of January 2024)` \
      matplotlib     `# plotting` \
      cartopy        `# map projections` \
      colormaps      `# provides many colormaps` \
      black          `# a formatter, non-negotiable`
```

activate the environment with

`mamba activate misu_pyenv` or `conda activate misu_pyenv`

## FORTRAN dependencies

1. `brew install gfortran`
2. `brew install netcdf`
3. `brew install netcdf-fortran`

You can find the path to the executables with

1. `brew info gfortran`
   + find the path to the library, for example `/home/linuxbrew/.linuxbrew/Cellar/gcc/13.2.0/bin`
1. `brew info netcdf-fortran`
   + find the path to the library, for example `/usr/local/Cellar/netcdf-fortran/4.6.1`

## Unsupported

Other ways are possible, on all systems, from Linux, to MacOS, to Windows. Including official Linux repositories which may hold `libnetcdff-dev` or using `WSL` on Windows. However, none of those are supported by the teaching assistant.
