# Human activity recognition using accelerometer data

  <p align="center">
    <a • href="https://github.com/Yair192">Yair Stolero</a> 
    <a • href="">Shlomi Buhadana</a>
  </p>

This project we developed and examined differenet network to identify human activity from 6 different classes using accelerometers data only.

<p align="center">
  <img width="760" height="400" src="https://media.springernature.com/lw685/springer-static/image/chp%3A10.1007%2F978-3-030-51379-5_9/MediaObjects/482899_1_En_9_Fig1_HTML.png">
</p>

## Background

The goal is to develop a system using IMU (Inertial Measurement Unit) sensors in smart wearables to detect user activity through deep learning. The system will utilize accelerometer data collected from smartphones carried by individuals performing six different exercises (Downstairs, Jogging, Sitting, Standing, Upstairs, Walking). The dataset includes timestamps, person IDs, and acceleration measurements for the x, y, and z axes.

By training a neural network on this dataset, we aim to enable the network to accurately identify the activity being performed based on previously unseen accelerometer data. The neural network will learn to differentiate between the six activities by analyzing the provided data. Consequently, when presented with new data, the trained neural network will be capable of predicting the ongoing activity of the user at any given time.

## Data

The data being used released by the Wireless Sensor Data Minining (WISDM) Lab [1] [2].
The data has 1,098,207 examples and 6 classes (Walking, Jogging, Upstairs, Downstairs, Sitting, Standing) by the following distribution:    

Walking - 38.6%     
Jogging - 31.2%    
Upstairs - 11.2%    
Downstairs - 9.1%    
Sitting - 5.5%    
Standing - 4.4%    

Every example has it's user id, activity label, time stamp, x axis data, y axis data , z axis data.
The sampling rate is 20 Hz.

## Data processing 

The data was divided into windows and was labeled as the main activity in the specific window.
Also, due to the inbalanced data, the train-test split was done by the uder id.

## Models

In order to get good comparison between different methods, we examined 4 different neural networks.

1. First, we developed a 1D CNN as in [3]. In this method, the networks trains on every axis seperetly.
2. The second network is 2D CNN. Here, we defined a kernal that takes into acount more then 1 axis in it's training.
3. LSTM network.
4. GRU.
   
## Files in the repository

|File name         | Purpsoe |
|----------------------|------|
|`window_size`| Numner of samples being taken in one segment|
|`step_size`| The step between two different segments|
|`leack_slope`| The size of the negative slop in LeakyReLU activation function|
|`batch_size`| The size of the batch|
|`learning_rate`| The gradient descent learning rate|
|`epochs`| Nubmber of epochs for training|


## Parameters

|File name         | Purpsoe |
|----------------------|------|
|`/data/WISDM_ar_v1.1_raw.txt`| file contains the raw acc measurements|
|`/data/WISDM_ar_v1.1_raw_about.txt`| dataset information|
|`/code/cnn_1d.ipynb`| Notebook that contains the 1D CNN code|
|`/code/cnn_2d.ipynb`| Notebook that contains the 2D CNN code|
|`/code/lstm.ipynb`| Notebook that contains the LSTM code|
|`/code/gru.ipynb`| Notebook that contains the GRU code|


## References
[1] WISDM: WIreless Sensor Data Mining: https://www.cis.fordham.edu/wisdm/dataset.php

[2] Jennifer R. Kwapisz, Gary M. Weiss and Samuel A. Moore (2010). Activity Recognition using Cell Phone Accelerometers: https://www.cis.fordham.edu/wisdm/includes/files/sensorKDD-2010.pdf

[3] https://github.com/mohan-mj/Activity-Detection-using-IMU-sensor



