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
look something like: `http://localhost:8888/?token=...`

Feel free to try out the examples in the `massmappy` folder.

Note however that you cannot save any modifications you make if you start Docker
with this simple command. To run a Docker image with a mounted local folder to save your work:
```
docker run -it --rm -v [path to local folder]:/home/jovyan/work -p 8888:8888  eiffl/astroinformatics-jupyter
```
You can then save files within the `/home/jovyan/work` inside the image.

## Building images

### Automated build

This is the preferred option, it uses dockerhub to automatically build the images.
See this [link](https://docs.docker.com/docker-hub/builds/) to see how to set it up.

### Manual build

Just go to the sub-directory of the specific image you want to build, and run:
```
docker build  -t='eiffl/astroinformatics-jupyter' .
```
where the `-t` option here is used to set a specific tag for the image, should
be changed based on what version you are building.

To push the built image to docker hub:
```
docker push 'eiffl/astroinformatics-jupyter'
```
To run this command, you must first login to your dockerhub account with `docker login`.
