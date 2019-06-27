## Classifying Cancer Malignancy

## Introduction

The goal here was to create as capable a classification model to identify cancer as either malignant or benign. This utilizes a common machine learning dataset, the Wisconsin Breast Cancer set. High levels of accuracy are possible with this set, although it is unfortunately small a dataset. Logistic regression yielded very legible, highly accurate results (F1 values ~.95). Random forest models yielded marginal improvements to F1.


## Content

The dataset consists of information about cells gathered from Fine Needle Aspiration samples of cancerous masses - both aggregated (mean radius, average measure of smoothness, etc) and also the most extreme or 'worst' in the sample (largest cell radius measurement, etc.).

It was clear from basic EDA that the average size of cells from the sample was by itself an very powerful predictor of whether the mass was malignant or benign. Consider the following scatter of instances with average radius on the x axis and a less important variable on the y, with malignant/benign encoded as color:

![scatter](https://github.com/max-miller/Flatiron_cancer/blob/master/radius%20smoothness%20scatter.png?raw=true)

It's clear how powerful size is on its own: that below a certain size (around 10) all of the cases are benign and that above a certain size (around 17) all the cases are malignant. The task becomes simply finding the features that best illumninate the space in between. A simple logistic regression taking into account only the mean radius feature with no scaling or any other work already scores in the 80s for both accuracy and F1. Consider this confusion matrix for such a model:

![confusion matrix](https://github.com/max-miller/Flatiron_cancer/blob/master/simple%20log%20confusion%20matrix.png?raw=true)

The basic logistic regression properly classifies nearly all benign cases, and properly classifies around 3/4 of malignant cases. Searching for the most illuminating features and engineering a handful of new features quickly raises F1 rates from logistic regression models to around .92 and normalizing the features raises F1 rates to around .95.

The most predictive model found was a random forest model, maxing out at an F1 of .96. At this point you begin running into the limitation that is the size of the dataset: these are models that only have 3 or 4 misclassifications in a test set of around 150. A larger dataset might yield more insights on the margins.
