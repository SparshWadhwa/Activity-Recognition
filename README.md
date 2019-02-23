# Activity-Recognition

>  deep learning to perform human activity recognition.

## Dataset
 UCI HAR dataset is used as an example.
 This dataset can be found in [here](https://archive.ics.uci.edu/ml/machine-learning-databases/00240/).

 dataset needs further preprocessing before being put into the network. 

| #subject | #activity | Frequency |
| --- | --- | --- |
| 30 | 6 | 50 Hz |


## Network structure

CNN structure

Convolution + pooling + convolution + pooling +   dense + dense + dense + output

That is: 2 convolutions, 2 poolings, and 3 fully connected layers. 

About the inputs

That dataset contains 9 channels of the inputs: (acc_body, acc_total and acc_gyro) on x-y-z. So the input channel is 9.

Dataset providers have clipped the dataset using sliding window, so every 128 in `.txt` can be considered as an input. In real life, you need to first clipped the input using sliding window.

So in the end, reformatted the inputs from 9 inputs files to 1 file, the shape of that file is `[n_sample,128,9]`, that is, every windows has 9 channels with each channel has length 128. When feeding it to Tensorflow, it has to be reshaped to `[n_sample,9,1,128]` as it is  expected there is 128 X 1 signals for every channel.
