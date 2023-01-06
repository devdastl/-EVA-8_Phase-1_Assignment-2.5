# -EVA-8_Phase-1_Assignment-2.5

## Introduction
In this jupyter notebook we are training a model which will take two inputs - 1. input image & 2. random number between 0&9 generated and will generate two predection. 1. image prediction & 2. prediction of summation of random number and predicted image (0 to 9).

## Data generation strategy
We have written custom Dataset module which takes MNIST dataset and modify it for your training. This module generate a random number and one-hot encode it as well as add this random number with image label. 
Each index of new dataset contains tupple of 4 values.
1. image - tensor containing image of 1x28x28
2. label - integer value whose image is in tensor.
3. random number (0-9) - one-hot encoded random number as tensor of 1x10
4. summation value - one-hot encoded summation of random number and label
<br>
example if label is 7 and random number is 5 the summation will be 12

## model architecture
![Alt text](util/img.jpg?raw=true "Title")
