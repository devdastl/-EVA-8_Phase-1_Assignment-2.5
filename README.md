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
![Alt text](img.JPG?raw=true "model architecture")
<br>
Above image shows model architecuture and how it takes two input i.e. image and random number and generate two output which is prediction of image and prediction of sum of random number and predicted label.
<br>
Here blue boxes represent forward prop for image tensor and green one represent forward prop for random number. We concatinate them and generate new tensor(orange block).

## Loss Function
Here we are using two different loss function. first one focuses on calcuating loss for image prediction and other focuses on calculating loss for summation prediction.
We are using cross entropy loss and finally summing both losses and calcuating gradients.

## Result evaluation
To evaluate the result we are using test dataset. We also divided evaluation into two parts first part evaluate image prediction accuracy and second part evaluate summation predicition accurary. we are also using number of correct prediction to evaluate the results.
<br>
we achieved approx 97% test accuracy for image prediction and approx 13% for summation prediction.

## Training logs
`0%|          | 0/469 [00:00<?, ?it/s]<ipython-input-2-03f2047c8575>:42: UserWarning: Implicit dimension choice for log_softmax has been deprecated. Change the call to include dim=X as an argument.
  return F.log_softmax(x), F.log_softmax(x1)
loss1=0.08650920540094376 loss2=2.5102756023406982 batch_id=468: 100%|██████████| 469/469 [00:24<00:00, 19.09it/s]`
<br>
OR We can also write our logs without pbar
<br>
```
loss1=2.303016424179077 loss2=2.9650540351867676 batch_id=0
loss1=2.3026371002197266 loss2=2.958984375 batch_id=1
loss1=2.3028502464294434 loss2=2.962730884552002 batch_id=2
loss1=2.3031225204467773 loss2=2.9567818641662598 batch_id=3
loss1=2.302233934402466 loss2=2.9504618644714355 batch_id=4
loss1=2.3026344776153564 loss2=2.9659128189086914 batch_id=5
loss1=2.303717851638794 loss2=2.951589584350586 batch_id=6
.
.
.
.
.
loss1=0.09619013965129852 loss2=2.48510479927063 batch_id=456
loss1=0.05284047871828079 loss2=2.558839797973633 batch_id=457
loss1=0.09095383435487747 loss2=2.5078513622283936 batch_id=458
loss1=0.10185061395168304 loss2=2.5609710216522217 batch_id=459
loss1=0.04554629325866699 loss2=2.589529037475586 batch_id=460
loss1=0.07082869857549667 loss2=2.553356647491455 batch_id=461
loss1=0.060965508222579956 loss2=2.566615581512451 batch_id=462
```
<br>
Training is done in one epoch!

## Evaluation logs
```
losses for image and summation is - loss1-25.502456665039062, loss2-2.5247411727905273 
 correctly predicted for this batch is img-122, sum-20
losses for image and summation is - loss1-10.713116645812988, loss2-2.454127550125122 
 correctly predicted for this batch is img-126, sum-23
losses for image and summation is - loss1-10.502182006835938, loss2-2.5715250968933105 
 correctly predicted for this batch is img-127, sum-20
losses for image and summation is - loss1-0.3733340799808502, loss2-2.341416597366333 
 correctly predicted for this batch is img-16, sum-3


Test set: Average loss for image prediction: 0.1040, Accuracy: 16/10000 (97%)

Test set: Average loss for summation prediction: 0.0203, Accuracy: 16/10000 (13%)
```
