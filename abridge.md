---
layout: page
permalink: /abridge
---

# Class 4 (Abridged): Creating Your Own AI - Image Classification

In this class we'll be using a deep neural network (DNN) to perform classification of images. Classification is an approach where given an image, we will try to identify which of the pre-defined category it belongs to.

In order to do this you will put together a dataset from the labelled images provided, build a convolutional neural network model (a DNN with `Convolution` layers) and then train it.

You'll be using a web-based software called DIGITS that will allow you to interactively build and train a DNN.

<img src="/img/digits.png" class="img-responsive" alt="DIGITS" />

In order to access DIGITS, click the link below:

<h3><a href="http://52.31.253.104:5000" target="_blank">Open DIGITS</a></h3>

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

## Exercise: Classification of Cats and Dogs

**Put together a deep learning network for classifying images using what we've learnt so far.**

**Tasks:**
* **Choose one of the optional datasets to create, either "Cats and Dogs" or "Cifar 10" dataset, using instructions in the sections below. Go through it carefully as the settings are different!**
* **Create and train the model.**
* **Load a few images from the internet and test classify to see if your model works.**

### Optional Dataset 1: Creating the Cats and Dogs Dataset

This dataset contain images of cats and dogs is obtained from Keggle/Microsoft research. The dataset contains 25,000 images in total, half of which are dogs and the other half are cats.

<img src="/img/dog.6.jpg" alt="Cat" class="img-responsive " style="max-width:150px;max-height:150px" /> | <img src="/img/cat.9.jpg" alt="" class="img-responsive " style="max-width:150px;max-height:150px" /> | <img src="/img/dog.34.jpg" alt="" class="img-responsive " style="max-width:150px;max-height:150px" /> | <img src="/img/cat.24.jpg" alt="" class="img-responsive " style="max-width:150px;max-height:150px" /> | <img src="/img/dog.81.jpg" alt="" class="img-responsive " style="max-width:150px;max-height:150px" /> | <img src="/img/cat.39.jpg" alt="" class="img-responsive " style="max-width:150px;max-height:150px" />

To create this dataset, click on the `Datasets` tab, then `Images` and `Classification`.

You'll be taken to the `New Image Classification Dataset` page. Then:
* Set the `Image Type` as `Color`.
* Set the `width` and `height` of the image to `64` pixels. This will help our network train faster.
* Under `Training Images` type in the path `/data/catsdogs/train`
* Name the dataset `catsdogs_data`
* Press `Create`

<img src="/img/new_image_dataset.png"  alt="New dataset" class="img-responsive img-rounded img-screenshot"  />

### Optional Dataset 2: Creating the Cifar10 dataset

This dataset contain images belonging to 10 categories, aeroplane, automobile, bird, cat, deer, dog, frog, horse, shap and truck. It contains a 60,000 images for training and 6,000 images for testing.

<img src="/img/cifar-10.png"  alt="Cifar 10 dataset" class="img-responsive img-rounded"  />

To create this dataset, click on the `Datasets` tab, then `Images` and `Classification`.

You'll be taken to the `New Image Classification Dataset` page. Then:
* Set the `Image Type` as `Color`.
* Set the `width` and `height` of the image to `32` pixels.
* Under `Training Images` type in the path `/data/cifar10/train`
* Tick the `Separate validation images folder` box
* Under `Validation Images` enter `/data/cifar10/test`
* Name the dataset `cifar10`
* Press `Create`

<img src="/img/create_cifar_dataset.png"  alt="New Cifar dataset" class="img-responsive img-rounded img-screenshot"  />

## Going further: Getting more data and augmenting them

Unlike previous machine learning approach, deep learning's performance has been shown to keep improving the more data and processing power you give to it. If you're struggling to raise accuracy, it may be that you need to incrase the size of your dataset or increase the size of your network.

<img src="/img/dl_moredata.png" alt="DNN performance increases with more data" class="img-responsive"  />

Many techniques can be applied to augment your data. For images, by inverting, scaling, rotating or adding noise, it is possible to increase the size of your dataset and make your model more robust to unexpected inputs.

<img src="/img/data_augment.png" alt="Augmenting data by applying transform" class="img-responsive"  />