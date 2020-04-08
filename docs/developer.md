# Developer guide

## Developer install

Clone the repository on your local machine:

```shell script
$ git clone https://github.com/tonio73/dnnviewer.git
```

## Run

For local development, the entry point is the file `dnnviewer.py` in the root directory.

Model ZOO is in 

```shell script
$ dnnviewer.py --model-keras dnnviewer-data/models/MNIST_dense128.h5 --test-dataset mnist
```

# Software architecture

The application is based on Dash for the user interface management (which is generating ReactJs components), and Plotly for the data visualization.

Code is separated in two branches:

- The Graphical representation
- Adapters to read existing models, currently only supporting Keras

## Graphical representation

Top level class it the dnnviewer.Grapher. It holds a collection of layers based on the base class dnnviewer.layers.AbstractLayer.AbstractLayer

## _Bridge_ - adapters to load neural network representation

Within `dnnviewer.bridge` is the code to load a DNN model in Keras and extract the DNN topology, weights, compute the gradients and activations

# Tooling

### Code quality

- Code is PEP8 compliant, thanks to *flake8* and *Intellij* for watching
- There are a few pytest unit tests in `unittests/`

#### Run unit test

From project root directory:

```shell
$ python -m pytest
```

#### Code linting

```shell
$ flake8  --max-line-length=120
```