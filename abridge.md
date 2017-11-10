---
layout: page
permalink: /abridge
---

# Class 4 (Abridged): Creating Your Own AI - Image Classification

In this class we'll be using a deep neural network (DNN) to perform classification of images. Classification is an approach where given an image, we will try to identify which of the pre-defined category it belongs to.

In order to do this you will put together a dataset from the labelled images provided, build a convolutional neural network model (a DNN with `Convolution` layers) and then train it.

You'll be using a web-based software called DIGITS that will allow you to interactively build and train a DNN.

<img src="/img/digits.png" class="img-responsive" alt="DIGITS" />

**Your teacher will provide you with the web address for accesssing  DIGITS**

## Introduction: Classification of handwritten digits

To familiarise yourself with DIGITS, we'll put together a simple model that can classify handwritten digits of 0 to 9.

<img src="/img/mnistdigits.gif" alt="MNIST dataset" class="img-responsive img-rounded"  />

### Creating the Dataset

To create a new dataset, click on the `Datasets` tab, then `Images` and `Classification`

<img src="/img/create_dataset.png" alt="Creating a dataset" class="img-responsive img-rounded img-screenshot"  />

If asked for a username, type in your name and press `Submit`

You'll be taken to the `New Image Classification Dataset` page. Then:
* Set the `Image Type` as `Grayscale`.
* Set the `width` and `height` of the image to `32` pixels. This will help our network train faster.
* Under `Training Images` type in the path `/data/mnist/train`.
* Tick on `Separate validation images folder`.
* Under `Validation Images` type `/data/mnist/test`.
* Name the dataset `mnist`.
* Press `Create`.

<img src="/img/create_mnist_dataset.png"  alt="New dataset" class="img-responsive img-rounded img-screenshot"  />

After a couple of minutes, a database will have been created that contains all of your images and labels. A database is used to allow images to be passed quickly to our network for training.

To explore the database that you've just created, press the `Explore the db` button.

<img src="/img/mnist_explore_db.png" alt="Click on Explore the db" class="img-responsive img-rounded img-screenshot"  />

You'll then be able to browse the images that we're using to train our model.

<img src="/img/mnist_exploring_db.png" alt="Browsing the images" class="img-responsive img-rounded img-screenshot"  />

### Creating the Model

Going back to the home page of DIGITS, click on the `Models` tab then on `Images` and `Classification`.

<img src="/img/create_model.png"  alt="New model" class="img-responsive img-rounded img-screenshot"  />

You'll be taken to the `New Image Classification Model` page, then:
* Under the `Select Dataset` box, click on `mnist` to use the dataset that you've just created.
* Under `Training epochs` enter `5`. A single `epoch` is when we have trained the model over a full set of data `once`.
* We'll use the standard `LeNet` network
* Under `Model name` name your model `mnist`
* Then press `Create` to begin training the model.

<img src="/img/create_lenet_model.png"  alt="Creating a LeNet model" class="img-responsive img-rounded img-screenshot" />

### Model Training

In the meanwhile you'll see a graph showing the status of the training being plotted in real-time.

<img src="/img/mnist_train_graph_loss.png"  alt="Lenet training graph" class="img-responsive img-rounded img-screenshot" />

* The blue line represents the `error` or `loss` in the `training` set.  As we're training our model, the `loss` will fluctuate but should show an overall decreasing trend until it stabilises after a certain amount of training. Its very unlikely that you will reach `0` `loss` and too low a value can cause `overfitting`, a scenario where your model fits the training data too well and can't be used to identify something it hasn't seen before.

* The green line represents the `loss` in the `validation` set. This `validation loss` should be decreasing with your `training loss`. When it doesn't it is a good indication that `overfitting` is occuring.

* Finally, the orange line represents the `accuracy`. It's the percentage of images that has been classified correctly when passing in the test dataset. The final accuary should be around `99%`.

### Test the classifier

You can try testing the model that you've just created. Scroll down to the `Trained Models` section and under `Test a single image`:
* Under `Image Path` enter `/data/mnist/test/5/00165.png`
* Press `Classify one`

<img src="/img/classify_one.png"  alt="Lenet training graph" class="img-responsive img-rounded img-screenshot" />

Looks like the model has predicted correctly that the digit is 5. You can also try to upload other images that you've download from the internet.

<img src="/img/classify_5.png"  alt="Lenet training graph" class="img-responsive img-rounded img-screenshot" />
