# MISU Computer-Lab Environments

+ Ezra Eisbrenner (December 2023)

## Required other software

1. install Homebrew (https://brew.sh) and run the brew commands, given in the other sections, in your terminal

## Windows

1. install a Linux in a virtual machine
2. follow the instructions for Linux

## MacOS and Linux

### Python Environment

First,

1. `brew install --cask mambaforge`
   * see `https://formulae.brew.sh/cask/mambaforge` for more information
2. If in doubt, look for the `conda`/`mamba` executable with `brew info mambaforge`

then create the MISU conda environment

```
mamba create         `# mamba is faster than conda` \
      -n misu_pyenv  `# name of new conda environment` \
      -c conda-forge `# channel from where to pull packages` \
      "python<3.10"  `# proplot does not support python > 3.10 as of December 2023` \
                     `# cartopy does not support python > 3.9 as of January 2024 with these dependencies` \
      dynaconf       `# advanced project settings` \
      jupyter        `# for notebooks and interactive vscode` \
      numpy          `# math` \
      scipy          `# math` \
      xarray         `# dimensional data` \
      pandas         `# tabular data` \
      f90nml         `# fortran namelist handling` \
      proplot        `# plotting with sensible defaults (restricts matplotlib<3.5 as of January 2024)` \
      matplotlib     `# plotting` \
      cartopy        `# map projections` \
      black          `# a formatter, non-negotiable`
```

activate the environment with

`mamba activate misu_pyenv` or `conda activate misu_pyenv`

### FORTRAN dependencies

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
