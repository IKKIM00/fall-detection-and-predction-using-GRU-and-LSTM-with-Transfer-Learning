# SmartFall Dataset Description

![스크린샷 2020-07-14 오후 8 20 59](https://user-images.githubusercontent.com/37397258/88628418-e4edc800-d0e8-11ea-945f-954084acb49d.png)

- all fall data samples are equally 25 points
- the cycle repeats with 'ADL-FALL-ADL-FALL'

# SmartFall LSTM & GRU Classification

![스크린샷 2020-07-17 오후 1 34 49](https://user-images.githubusercontent.com/37397258/88629889-cbe61680-d0ea-11ea-9217-b091feff8100.png)
- To make input dataset, I have partioned data into 40 points
- If all 25 points of fall data is included in partioned 40 points, I labelled it as 'FALL'
- Unless, it's all labelled as 'ADL'
- Since there is huge data imbalance between Fall and ADL, I shrinked ADL data portion as same as Fall data 
- I also implemented cyclic learning rate

# SmartFall LSTM & GRU Classification Results

|               |Precision|Recall|F1 Score|Accuracy|
|:---------------|-----------:|--------:|----------:|----------:|
|SmartFall LSTM|0.9963|0.8411|0.9121|0.9189|
|SmartFall GRU|0.9963|0.8442|0.9139|0.9205|

# MobiAct Dataset
- To compare the result between MobiAct dataset and SmartFall dataset, I resampled MobiAct dataset similar to SmartFall dataset
- To make input data, I have resampled all MobiAct Fall data's fall parts to 30 points and added 10 samples of ADL at the front and the end of fall samples 
- Then I used partioned data with window size of 40(same as SmartFall data window size) to make input dataset
- You can find MobiAct Dataset at below url
- https://bmi.hmu.gr/the-mobifall-and-mobiact-datasets-2/
- You can see partioning code throught MobiAct_DataParsing.ipynb

# Transfer Learning using MobiAct Dataset
- I have used pretrained model using SmartFall Dataset to MobiAct Dataset but because of the difference of data collected domain performance was really bad
- The chart below describe the result of training SmartFall data & testing on SmartFall data, using pretrained model to test on MobiAct data, relearning pretrained model using MobiAct data

![스크린샷 2020-07-28 오후 4 57 55](https://user-images.githubusercontent.com/37397258/88636212-8f6ae880-d0f3-11ea-83f3-b91e025f320b.png)

- The chart shows that relearning through pretrained model works well 
