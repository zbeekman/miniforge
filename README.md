# miniforge
[![Build Status](https://travis-ci.com/conda-forge/miniforge.svg?branch=master)](https://travis-ci.com/conda-forge/miniforge)

This repository holds a minimal installer for conda specific to conda-forge. It can be directly compared to [Miniconda](https://docs.conda.io/en/latest/miniconda.html), with the added feature that conda-forge is the default channel.

## Download

Miniforge installers are available here: https://github.com/conda-forge/miniforge/releases

#### Miniforge3
Latest installers with python 3.7 in the base environment

- [linux-aarch64](https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-Linux-aarch64.sh) (also called `arm64`)
- [linux-ppc64le](https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-Linux-ppc64le.sh) (also called `POWER8/9`)
- [linux-x86_64](https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-Linux-x86_64.sh) (also called `amd64`)
- [osx-x86_64](https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-MacOSX-x86_64.sh)

#### Miniforge-pypy3
Latest installers with pypy3.6 in the base environment

- [linux-aarch64](https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge-pypy3-Linux-aarch64.sh)
- [linux-ppc64le](https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge-pypy3-Linux-ppc64le.sh)
- [linux-x86_64](https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge-pypy3-Linux-x86_64.sh)
- [osx-x86_64](https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge-pypy3-MacOSX-x86_64.sh)

Follow the aarch64 and ppc64le migration status here: https://conda-forge.org/status/

## Features

- [X] Automatic build of constructor.
- [X] Automatic upload of constructor results.
- [X] Automatic testing of constructor.
- [ ] Integration with conda-forge's developer documentation.
- [ ] Integration with conda-forge's official site.
- [ ] Upstream to Anaconda ?

## Testing

After construction on Travis, the installer is tested against a range of distribution that match the installer architecture (`$ARCH`). For example when architecture is `aarch64`, the constructed installer is tested against:

- Centos 7
- Debian Buster (10)
- Ubuntu 16.04
- Ubuntu 18.04
- Ubuntu 19.10

## Usage

Installers are built and uploaded via Travis but if you want to construct your own Miniforge installer, here is how:

```bash
# Configuration
export ARCH=aarch64
export DOCKERIMAGE=condaforge/linux-anvil-aarch64

bash build_miniforge.sh
```

## Release

To release a new version of Miniforge:

- Open a new PR.
- Edit [`Miniforge3/construct.yaml`](./Miniforge3/construct.yaml).
  - Update the `version` tag to: `$CONDA_VERSION-$BUILD_NUMBER`. For example, `4.7.11-0`.
  - Update `conda` version in the `specs` section to `$CONDA_VERSION`.
  - Update `python` version in the `specs` section to the Python version used in [Miniconda](https://repo.anaconda.com/miniconda/).
- Once CI is happy, merge into `master`.
- Tag `HEAD` to `$CONDA_VERSION-$BUILD_NUMBER` and push the tag:
  - `git tag $CONDA_VERSION-$BUILD_NUMBER`
  - `git push origin master --tags`

## License

[BSD 3-Clause](./LICENSE)

## History

Relevant conversations:

- https://github.com/conda-forge/conda-forge.github.io/issues/871#issue-496677528
- https://github.com/conda-forge/conda-forge.github.io/pull/922
