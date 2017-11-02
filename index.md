---
layout: page
---

# Class 4: Creating Your Own AI - Image Recognition

We'll be using Deep Learning, convolution

* What's it being used for?
* What is it?
  * Subcategory of machine learning, namely neural networks
  * About Neural networks
  * About Deep Learning, why deep?
    * Hierachy of data
    * Before - manual features
    * Now - full pipeline
* Why is it possible now?
  * Data - big data
  * Computational power - Gpus
  * Algorithms - Convolution

## Nvidia DIGITS

For this class, you'll be using a web-based software called DIGITS that will allow you to interactively build and train a DNN.

<img src="/img/digits.png" class="img-responsive" alt="DIGITS" />



In order to access DIGITS, click the link below:

**LINK to digits**

## The Task: Image Classification of Cats and Dogs

What's the provided dataset??


## Creating the Dataset

We first need to put together a dataset for training our network using the images of the cats and dogs have already been loaded on to the machine.

Click on the `Datasets` tab, then `Images` and `Classification`

If asked for a username, type in your name and press `Submit`

You'll be taken to the `New Image Classification Dataset` page. Our training datset is located in the folder `/data/catsdogs/train`.

Set the `width` and `height` of the image to `64` pixels. This will help our network train faster.

Name the dataset `catsdogs_data`

Press `Create`

After a couple of minutes, a database will have been created that contains all of your images and labels. A database is used to allow images to be passed quickly to our network for training.

To explore the database that you've just created, press the `Explore the db` button.


## Creating a Model

Now that we have a dataset to work with, it's time to create a model and decide the architecture of our DNN.

<img src="/img/lenet.png" class="img-responsive" alt="Lenet Network" />


* Talk aboout convolution and pooling

Going back to the home page of DIGITS, click on the `Models` tab then on `Images` and `Classification`.

You'll be taken to the `New Image Classification Model` page, then:
* Under the `Select Dataset` box, click on the `catsdogs_data` to use the database that you've just created.
* Under `Training epochs` enter `10` to limit the amount of training we do to the network.
* We'll use the standard `LeNet` network
* Under `Model name` name your model `catsdogs`
* Then press `Create`

Your network will begin training for a couple of minutes. In the meanwhile you'll see a graph showing the status of our model being plotted in real-time.

The blue line is the `error` or `loss` in the `training` set. The higher the `loss` is, the more likely the model will give an incorrect result. As we're training our model, the `loss` will fluctuate but should show an overall decreasing trend until it stabilises after a certain amount of training. Its very unlikely that you will reach `0` `loss` and too low a value can cause `overfitting`, a scenario where your model fits the training data too well and can't be used to identify something it hasn't seen before.

The green line is the `loss` in the `validation` set. This `validation loss` should be decreasing with your `training loss`. When it doesn't it is a good indication that `overfitting` is occuring.



You'll get a final accuracy of....

## Improving the accuracy
Tricks in the toolbox of

### Get more data

### Add activation functions

### More training

### Add more filters

### Add more layers

### Reduce overfitting


<img src="/img/training-val-loss-divergent.png" class="img-responsive" alt="Divergent training validation loss" />



* The task: Image classification
* The process of training a (deep) neural network
* The dataset
  * The provided dataset
* Architecture (Segway to Caffe model)
  * fully connected
  * convolution
  * pooling
  * non-linearity
  * Let's train the first model
* Improving accuracy
  * increasing layers
* Reduce overfitting
  * dropout
