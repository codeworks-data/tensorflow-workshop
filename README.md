# Set-up
## Using Docker
### Using a Jupyter Notebook container
We will use a [`jupyter-minimal`](https://hub.docker.com/r/jupyter/minimal-notebook/tags/) docker image to run Jupyter Notebook locally. It comes with many packages already installed.
Fire up `Docker` and start by connecting the current working directory to the Docker container:
```
$ docker run -p 8888:8888 -v $(pwd):/home/jovyan/work jupyter/minimal-notebook 
```
Use ``` $ docker ps ``` to retrieve the container id.

To install required packages, enter the Docker container:
```
$ docker exec -it CONTAINER-ID /bin/bash
```

With a simple ```$ pip list``` you can see the list of pre-installed Python libraries.

`TensorFlow` is not one of them. 

We will install it using `pip`. As indicated in the [official docs](https://www.tensorflow.org/install?hl=fr), `TensorFlow` requires the latest verison of `pip` which is already up-to date in the container. Which is one of the advantages of using a `Docker image`.

```
# Current stable release for CPU and GPU
$ pip install tensorflow
```

And voilà! You can now import `TensorFlow` in your notebook.

### Using a TensorFlow container

An easier way would be to use a `TensorFlow` [Docker image](https://hub.docker.com/r/tensorflow/tensorflow/) directly.

```
 $ docker pull tensorflow/tensorflow:latest  # Download latest stable image
 $ docker run -it -p 8888:8888 tensorflow/tensorflow:latest-jupyter  # Start Jupyter server
```
## In a local Python virtual env
Start by updating `pip`, then installing tha package:
```
# Requires the latest pip
pip install --upgrade pip
# Current stable release for CPU and GPU
pip install tensorflow
```
## Using Google Colab

If you do not wish to set up anything at all, use [Google Colab](https://colab.research.google.com/notebooks/welcome.ipynb)