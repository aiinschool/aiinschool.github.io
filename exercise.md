---
layout: page
permalink: /exercise
---

# Exercise: Classification of Cats and Dogs

**Put together a deep learning network for classifying images using what we've learnt so far.**

**Tasks:**
* **Choose one of the optional datasets to create, either "Cats and Dogs" or "Cifar 10" dataset, using instructions in the sections below. Go through it carefully as the settings are different!**
* **Create and train the model.**
* **Load a few images from the internet and test classify to see if your model works.**

## Optional Dataset 1: Creating the Cats and Dogs Dataset

This dataset contain images of cats and dogs is obtained from Keggle/Microsoft research. The dataset contains 25,000 images in total, half of which are dogs and the other half are cats.

<img src="/img/dog.6.jpg" alt="Cat" class="img-responsive " style="max-width:150px;max-height:150px" /> | <img src="/img/cat.9.jpg" alt="" class="img-responsive " style="max-width:150px;max-height:150px" /> | <img src="/img/dog.34.jpg" alt="" class="img-responsive " style="max-width:150px;max-height:150px" /> | <img src="/img/cat.24.jpg" alt="" class="img-responsive " style="max-width:150px;max-height:150px" /> | <img src="/img/dog.81.jpg" alt="" class="img-responsive " style="max-width:150px;max-height:150px" /> | <img src="/img/cat.39.jpg" alt="" class="img-responsive " style="max-width:150px;max-height:150px" />

To create this dataset, click on the `Datasets` tab, then `Images` and `Classification`.

You'll be taken to the `New Image Classification Dataset` page. Then:
* Set the `Image Type` as `Color`.
* Set the `width` and `height` of the image to `64` pixels. This will help our network train faster.
* Under `Training Images` type in the path `/data/catdog/train`
* Name the dataset `catsdogs_data`
* Press `Create`

<img src="/img/new_image_dataset.png"  alt="New dataset" class="img-responsive img-rounded img-screenshot"  />

## Optional Dataset 2: Creating the Cifar10 dataset

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

### Going further: Getting more data and augmenting them

Unlike previous machine learning approach, deep learning's performance has been shown to keep improving the more data and processing power you give to it. If you're struggling to raise accuracy, it may be that you need to incrase the size of your dataset or increase the size of your network.

<img src="/img/dl_moredata.png" alt="DNN performance increases with more data" class="img-responsive"  />

Many techniques can be applied to augment your data. For images, by inverting, scaling, rotating or adding noise, it is possible to increase the size of your dataset and make your model more robust to unexpected inputs.

<img src="/img/data_augment.png" alt="Augmenting data by applying transform" class="img-responsive"  />
