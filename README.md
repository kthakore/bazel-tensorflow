# Tensorflow C++ Image Recognition Demo

**NOTE: This demo is from Tensorflow's original repo. It is used to help set up a bazel build for tensorflow. **

This example shows how you can load a pre-trained TensorFlow network and use it
to recognize objects in images.

## Description

This demo uses a Google Inception model to classify image files that are passed
in on the command line.

## To build/install/run

The TensorFlow `GraphDef` that contains the model definition and weights
is not packaged in the repo because of its size. Instead, you must
first download the file to the `data` directory in the source tree:

```bash
$ wget https://storage.googleapis.com/download.tensorflow.org/models/inception_dec_2015.zip -O data/inception_dec_2015.zip

$ mkdir -p data

$ unzip tensorflow/examples/label_image/data/inception_dec_2015.zip -d data/
```

Then, as long as you've managed to build the main TensorFlow framework, you
should have everything you need to run this example installed already.

Once extracted, see the labels file in the data directory for the possible
classifications, which are the 1,000 categories used in the Imagenet
competition.

To build it, run this command:

```bash
$ bazel build src/...
```

That should build a binary executable that you can then run like this:

```bash
$ bazel-bin/src/label_image
```

This uses the default example image that ships with the framework, and should
output something similar to this:

```
I tensorflow/examples/label_image/main.cc:200] military uniform (866): 0.902268
I tensorflow/examples/label_image/main.cc:200] bow tie (817): 0.05407
I tensorflow/examples/label_image/main.cc:200] suit (794): 0.0113195
I tensorflow/examples/label_image/main.cc:200] bulletproof vest (833): 0.0100269
I tensorflow/examples/label_image/main.cc:200] bearskin (849): 0.00649746
```
In this case, we're using the default image of Admiral Grace Hopper, and you can
see the network correctly spots she's wearing a military uniform, with a high
score of 0.9.

Next, try it out on your own images by supplying the --image= argument, e.g.

```bash
$ bazel-bin/src/label_image/label_image --image=my_image.png
```

For a more detailed look at this code, you can check out the C++ section of the
[Inception tutorial](https://tensorflow.org/tutorials/image_recognition/).
