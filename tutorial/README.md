# Metaprob tutorial

This directory contains a work-in-progress tutorial for Metaprob, in the file `Tutorial.ipynb`. The tutorial should generally be run in a Docker container, though it's also possible to run as a Clojure / Jupyter project directly on your machine.

If you're interested in using Metaprob outside a Jupyter notebook or contributing to the language itself, please refer to the general [installation instructions](INSTALL.md).

## Getting started

First, you should clone this repository:

    git clone https://github.com/probcomp/metaprob.git

Once the repository is cloned, `cd` into the newly-created `metaprob` directory.

## Running in a container

To run the Metaprob tutorial in a Docker you will need to run the following commands from the root of this repository (in the same directory as `Makefile`):

1. Ensure `docker` is installed. Can you run `docker version`? See below for help.
2. If this is the first time you're using the container, build the
   Docker image by running `make docker-build` in the root directory
   of this repository. Note that you should only need to run this
   command once- this step can be skipped in the future when starting
   the container.
3. Confirm the container you built is present on your system. Running `docker images | grep probcomp` should print a line starting with `probcomp/metaprob-clojure`.
4. Run the Docker image with `make docker-notebook`. Eventually a message including `The Jupyter Notebook is running at:` should be displayed.
5. In your browser, visit [http://127.0.0.1:8888/](http://127.0.0.1:8888)
6. Click on `Tutorial.ipynb`.

### Installing Docker

Please visit Docker's own installation documentation:

* for Mac: [Install Docker Desktop for Mac](https://docs.docker.com/docker-for-mac/install/)
* for Linux: [Debian](https://docs.docker.com/install/linux/docker-ce/debian/), [Ubuntu](https://docs.docker.com/install/linux/docker-ce/ubuntu/), [Fedoroa](https://docs.docker.com/install/linux/docker-ce/fedora/), [CentOS](https://docs.docker.com/install/linux/docker-ce/centos/). Please remember to complete the [post-installation steps for Linux](https://docs.docker.com/install/linux/linux-postinstall/).

If you've installed Docker but the instructions above are still failing, make sure Docker is running. On the Mac, double-click the Docker application. The "whale" should appear in your status bar.

## Running as a Clojure project

Note that this method of running the tutorial is less supported than using the Docker container, but we'll make an effort to support the following:

1. Ensure you have Jupyter installed. Can you run `jupyter notebook` and start a Jupyter server?
2. Ensure lein is installed.
3. Install the Lein Jupyter kernel: `lein jupyter install-kernel`.
4. In the root directory of this repository, run `lein jupyter notebook`. (If you prefer (and have installed) Jupyter Lab, you may use it (`lein jupyter lab`), but you will need to run `jupyter labextension install @jupyterlab/javascript-extension` for the visualization code to work.)
5. Running step 4 should open a web browser to the Jupyter Notebook (or Lab) application. Navigate to the `Tutorial.ipynb` file.

If you run into an error that your IO rate has been exceeded, try starting the server with this option:

`lein jupyter notebook --NotebookApp.iopub_data_rate_limit=10000000`
