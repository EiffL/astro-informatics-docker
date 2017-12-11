# astro-informatics-docker

Docker containers for the [astro-informatics](https://github.com/astro-informatics/) software stack:
  - [SSHT](http://astro-informatics.github.io/ssht/): Spin spherical harmonic transforms
  - [so3](http://astro-informatics.github.io/so3/): Wigner transforms
  - [S2LET](http://astro-informatics.github.io/s2let/): Fast wavelets on the sphere
  - [massmappy](https://astro-informatics.github.io/massmappy/): Mapping dark matter on the celestial sphere

This repository contains several versions of the stack:

 - [mininal](minimal): Based on Ubuntu 16.04, the astro-informatics stack is
 installed in `/opt/astroinformatics` and the python modules are installed
 in the python environment. This can act as a clean base image.

 - [jupyter](jupyter): Based on the [jupyter/scipy-notebook](https://hub.docker.com/r/jupyter/scipy-notebook/),
 contains the same software as the minimal image, but hosts a jupyter server.

## Quick Start

Obviously, you need to install Docker on your system, follow [this link](https://docs.docker.com/engine/installation/).

The following command will download the live jupyter notebook version of the
stack:
```
docker run -it --rm -p 8888:8888 -P eiffl/astroinformatics-jupyter
```

Copy paste the notebook url shown in your terminal to your browser, it should
look something like: `http://localhost:8888/?token=348e145241d1f0282ae2e433281d701ea305e1063ba80bde`

Feel free to try out the examples in the `massmappy` folder. Note however that
you cannot save any modifications you make if you start Docker with this simple
command.
