# Docker Training

Before our first hands-on training session, please do the following:

1. Download and install [Docker for your platform of choice][docker]. If you run
into any errors, reference the "Getting Started Tutorial" for your platform.

  Note: Windows users may be prompted to enable Hyper-V and required to restart.

2. Verify it Docker was installed correctly by running `docker run --rm hello-world`

You should be all set. The remainder of this README includes reference notes and
instructions for the training.

## Introduction to Docker

There are a couple more one-time setup steps you may want to do. Mac OS X (or
anyone using a bash shell) users may want to setup [bash completion][bash].
PowerShell users may want to setup [posh][posh]. Windows users must also [share
a local drive][drive] in the Docker for Windows Settings. On Mac OS X, `/Users`
is automatically shared, so you are all set.

[docker]: https://www.docker.com/products/docker
[bash]: https://docs.docker.com/docker-for-mac/#/installing-bash-completion
[posh]: https://docs.docker.com/docker-for-windows/#/set-up-tab-completion-in-powershell
[drive]: https://docs.docker.com/docker-for-windows/#/shared-drives
