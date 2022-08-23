# HILAPP singularity container #

Definition file for HILA pre-processor [singularity](https://sylabs.io/singularity/) container. This container is meant to be a portable solution for compiling the first half of HILA code which is the parsing for specific architectures.

Singularity is a tailor made containerizing software often supported by HPC platforms such as CSC supercomputers.

One can download the singularity container hilapp.sif directly from this github repositories release page or build it from scratch. If downloaded skip directly to **Using singulartiy container** section.

## Building container from scratch ##

### 1. Installing singularity ###

Install singularity either from source of via any given package manager which is supported. Documentation can be found on the [GitHub page](https://github.com/sylabs/singularity)

You can simply download latest .deb or .rpm from github [release page](https://github.com/sylabs/singularity/releases) and install directly with package manager

Ubuntu:
```
dpkg -i singularity-ce_$(SINGULARITY_VERSION)-$(UBUNTU_VERSION)_amd64.deb
```

### 2. Building singularity container ###

Note: sudo privileges are necessary for building singularity containers

Download copy of HILA into current working directory

```
git clone git@bitbucket.org:Kari_Rummukainen/HILA.git
```

Build singularity container

```
sudo singularity build hilapp hilapp.def
```

## Using singulartiy container ##

The hilapp.sif file will act as a singularity container and equivalently as the hilapp binary and can be used as such when pre processing HILA code. Thus you can move it to your HILA projects bin folder

```
mkdir HILA/hilapp/bin
mv hilapp.sif HILA/hilapp/bin/hilapp
```

Now one can simply move the singularity container to any give supercomputer. 

Note that on supercomputers the default paths aren't the same as on default linux operating systems. Thus one will need to mount their HILA source folder to singularity using the APPTAINER_BIND environment variable. Simple navigate to the base of your HILA source directory and run

    export APPTAINER_BIND=$(pwd)


