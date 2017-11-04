---
layout: page
---

# Class 4: Creating Your Own AI - Image Classification

In this class we'll be using a deep neural network (DNN) to perform classification of images. Classification is an approach where given an image, we will try to identify which of the pre-defined category it belongs to.

In order to do this you will put together a dataset from the labelled images provided, build a convolutional neural network model (a DNN with `Convolution` layers) and then train it.

You'll be using a web-based software called DIGITS that will allow you to interactively build and train a DNN.

<img src="/img/digits.png" class="img-responsive" alt="DIGITS" />

In order to access DIGITS, click the link below:

**LINK to digits**

## Putting together a simple model, classification of handwritten digits

To familiarise yourself with DIGITS, we'll put together a simple model that can classify handwritten digits of 0 to 9.

<img src="/img/mnistdigits.gif" alt="MNIST dataset" class="img-responsive img-rounded"  />

We'll use the MNIST dataset by LeCunn et al. of handwritten digits. The dataset contains 60,000 labelled images of numbers 0-9 for training and another 10,000 labelled images for testing. As the name suggests, the training set is used in training our model. The testing set is used only to check how well our model will classify something it hasn't seen before. This separation of data for training and testing is essential for estimating how well the model will perform.

As the images are labelled, you'll be training the model with an approach called `supervised learning`. As the weights between the connections of our neurons are random when we initially create the model, the network will likely give a wrong classification for any images that's passed to it. When training the model, because images are labelled, the network knows whether its decision was correct or not. This allows the weights in the network to be adjusted, leading to a correct prediction in the end.

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

### The Convolutional Model

Now that we have a dataset to work with, it's time to create a model and decide the architecture of our DNN. DIGITS happens to provide some standard models that can be used without configuration. This time we'll use the simplist one, the `LeNet` model, as shown below:

<img src="/img/lenet.png" class="img-responsive" alt="Lenet Network" />

You'll notice that the first few layers are rectangular in shape. You can think of this as neurons arranged in a grid, similar to how a grid of pixels form an image. In addition, there's two new types of layers, the `Convolution` layer (`conv1` and `conv2`) and the `Pooling` layer (`pool1` and `pool2`).

A `Convolution` layer is made up of multiple `feature maps`, each of the map scans over the input and detect for one single feature in an image e.g. one might be looking for a vertical line and another might look for a patch of a particular colour. As you connect up more `Convolution` layers, higher-level features (e.g. an entire face) can be detected in the later layers. An example of this is shown in the diagram below:
<img src="/img/feature_maps.png"  alt="New model" class="img-responsive img-rounded"  />

A `Pooling` layer reduces the dimensions of the previous layer. The MAX pooling operation represented in the diagram below selects the maximum value from each specific region in the previous layer:

<img src="/img/pooling.png"  alt="New model" class="img-responsive img-rounded"  />

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

The process of training the model is a loop of propagating data forwards then backwards through the network:
* An image is passed through the input and propagates forward through the network (called `forward propgation` or `inferencing`) and gives a prediction on which category the input image belongs to.
* The `error` or `loss` is calculated. The higher the `loss` value, the more likely the model will give an incorrect result.
* `Back propagation` then occurs where the weights in the network are adjusted so that the `loss` decreases.
* The process starts again using a different image.

<img src="/img/dnn_training.png" class="img-responsive" alt="Deep Neural Network training" />

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

## Exercise 1: Classification of Cats and Dogs

Put together a deep learning network for classifying images of cats and dogs using what we've learnt so far.

**Tasks**
* Create the dataset following the instructions in the section below. Go through it carefully as the settings are different!
* Create and train the model.
* Load an image from the internet and test classify to see if your model works.

### Creating the Cats and Dogs Dataset

We first need to put together a dataset for training our network using the images of the cats and dogs have already been loaded on to the machine.

Labelled images obtained from Keggle/Microsoft research will be used for training the model. The dataset contains 25,000 images in total, half of which are dogs and the other half are cats.  

<img src="/img/dog.6.jpg" alt="Cat" class="img-responsive " style="max-width:150px;max-height:150px" /> | <img src="/img/cat.9.jpg" alt="" class="img-responsive " style="max-width:150px;max-height:150px" /> | <img src="/img/dog.34.jpg" alt="" class="img-responsive " style="max-width:150px;max-height:150px" /> | <img src="/img/cat.24.jpg" alt="" class="img-responsive " style="max-width:150px;max-height:150px" /> | <img src="/img/dog.81.jpg" alt="" class="img-responsive " style="max-width:150px;max-height:150px" /> | <img src="/img/cat.39.jpg" alt="" class="img-responsive " style="max-width:150px;max-height:150px" />

Click on the `Datasets` tab, then `Images` and `Classification`.

You'll be taken to the `New Image Classification Dataset` page. Then:
* Set the `Image Type` as `Color`.
* Set the `width` and `height` of the image to `64` pixels. This will help our network train faster.
* Under `Training Images` type in the path `/data/catsdogs/train`
* Name the dataset `catsdogs_data`
* Press `Create`

<img src="/img/new_image_dataset.png"  alt="New dataset" class="img-responsive img-rounded img-screenshot"  />

## Exercise 2: Improving the accuracy of your model
Unlike MNIST, the cats and dogs dataset has much more variation and is therefore harder to for the model to make a prediction. Use one or a combination of techniques described in the following sections to maximise your accuracy. What's the highest accuracy that you can achieve?

### Customising your network layers

It is possible to customise your network by editing the network definition file. The network is composed of a series of layers connected to each other. For example, here's a `Convolution` and `Pooling` layer:

```
layer {
  name: "pool1"
  type: "Pooling"
  bottom: "conv1"
  top: "pool1"
  pooling_param {
    pool: MAX
    kernel_size: 2
    stride: 2
  }
}
layer {
  name: "conv2"
  type: "Convolution"
  bottom: "pool1"
  top: "conv2"
  param {
    lr_mult: 1
  }
  param {
    lr_mult: 2
  }
  convolution_param {
    num_output: 50
    kernel_size: 5
    stride: 1
    weight_filler {
      type: "xavier"
    }
    bias_filler {
      type: "constant"
    }
  }
}
```
The connection between layers are indicated by the `top` and `bottom` parameters. The `top` parameter is the output of the layer, and `bottom` parameter is the input. From the above example, it can be seen that the `Convolution` layer named `conv2` has the input `pool1` and outputs `conv2`.

To edit your model, on model creation page after chossing `LeNet`, click `Customize`.

<img src="/img/customize_network.png"  alt="Customise network" class="img-responsive img-rounded img-screenshot" />

This will take you to the network editor. You can click on the `Visualize` button to see the visulisation of the network graph.

<img src="/img/customizing_network.png"  alt="Network editor" class="img-responsive img-rounded img-screenshot" />

The network visulisation is shown below:

<img src="/img/network_graph.png"  alt="Network visulisation" class="img-responsive img-rounded img-screenshot" />

Once you've started training your customised model, it is possible to clone your model in order to keep the settings and changes in the model definition file so that you can make further changes. Just click on the `Clone Job` button of the model that's training or has already finished training.

<img src="/img/clone_job.png"  alt="Network visulisation" class="img-responsive img-rounded img-screenshot" />

### Use more filters in your convolution layer

Adding more filters in your `Convolution` layers allows it to detect more features which can allow the model to make more complex predictions. You can do this by increasing the `num_output` parameter. In this case, for `conv2` layer, the `50` filters has changed to `100`.

```
layer {
  name: "conv2"
  type: "Convolution"
  bottom: "pool1"
  top: "conv2"
  param {
    lr_mult: 1
  }
  param {
    lr_mult: 2
  }
  convolution_param {
    num_output: 100
    kernel_size: 5
    stride: 1
    weight_filler {
      type: "xavier"
    }
    bias_filler {
      type: "constant"
    }
  }
}
```

### Add activation functions

Activation functions such as `ReLU` adds non-linearity to our network and allows it to express more complexity. Try adding the `ReLU` layer after every `Pooling` layer in your network:

```
layer {
  name: "relu"
  type: "ReLU"
  bottom: "pool1"
  top: "pool1"
}
```

### Add more layers

Deeper networks also allows for more complex predictions. Try adding more `Convolution` layers to your model.
* Don't forget to add a `Pooling` and optionally `ReLU` layer after your new `Convolution` layer.
* Don't forget to change the `bottom` prameter of the `ip1` layer.


### More training

As the more filters and layers are added, the model will have to be trained for longer. This can be done by changing the number of training `epochs` while creating your model:

<img src="/img/training_epochs.png" alt="Changing epochs" class="img-responsive img-rounded img-screenshot"  />

### Reduce overfitting

<img src="/img/training-val-loss-divergent.png" alt="Divergent training validation loss" class="img-responsive img-rounded img-screenshot"  />

```
layer {
  name: "drop1"
  type: "Dropout"
  top: "pool1"
  bottom: "pool1"
  dropout_param{
    dropout_ratio: 0.5
  }

}
```


## Going further: Getting more data and augmenting them

<img src="/img/dl_moredata.png" alt="DNN performance increases with more data" class="img-responsive"  />
