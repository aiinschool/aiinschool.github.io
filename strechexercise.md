---
layout: page
permalink: /stretchexercise
---

# Stretch Exercise: Improving the accuracy of your model
**Unlike MNIST, the cats and dogs dataset has much more variation and is therefore harder to for the model to make a prediction. Use one or a combination of techniques described in the following sections to maximise your accuracy. What's the highest accuracy that you can achieve?**

## Customising your network layers

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

## Use more filters in your convolution layers

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
    num_output: 100 #<-- Change the number of feature maps here
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

## Add activation functions

Activation functions such as `ReLU` adds non-linearity to our network and allows it to express more complexity. Try adding the `ReLU` layer after every `Pooling` layer in your network:

```
layer {
  name: "relu"
  type: "ReLU"
  bottom: "pool1"
  top: "pool1"
}
```

## Add more layers

Deeper networks also allows for more complex predictions. Try adding more `Convolution` layers to your model.
* Don't forget to add a `Pooling` and optionally `ReLU` layer after your new `Convolution` layer.
* Don't forget to change the `bottom` prameter of the `ip1` layer.


## More training

As the more feature maps and layers are added, the model will have to be trained for longer. This can be done by changing the number of training `epochs` while creating your model:

<img src="/img/training_epochs.png" alt="Changing epochs" class="img-responsive img-rounded img-screenshot"  />

## Reduce overfitting

It is also important to observe the `validation loss` (green line) along with the `accuracy` (orange line). The graph below shows an example of `training loss` (blue line) diverging from the `validation loss`:

<img src="/img/training-val-loss-divergent.png" alt="Divergent training validation loss" class="img-responsive img-rounded img-screenshot"  />

This is a clear sign of `overfitting` and it means that your model will more likely to misclassify images that it wasn't trained on. In order to reduce overfitting, a technique called `Dropout` where a certain percentage of random neurons are excluded from training. The neurons selected to be excluded change at every `forward propagation` step.

<img src="/img/dropout.png" alt="Applying dropout" class="img-responsive img-rounded img-screenshot"  />

The technique can be used in your model by introducing the `Dropout` layer and any layer below it will experience the dropout. The `dropout_ratio` determines the percentage of excluded neurons in the layer e.g. `0.6` means 60% of random neurons will not be used.  Try putting `Dropout` layers after the `Pooling` or `ReLU` layers.

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
