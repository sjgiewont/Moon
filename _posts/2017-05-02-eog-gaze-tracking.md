---
layout: post
title:  "2D Gaze Tracking Using EOG Signals"
date:   2017-05-02
excerpt: "Using machine learning techniques and electrooculography (EOG) signals to predict eye gaze position in real time."
project: true
feature: /assets/img/gaze_tracking_trial.png
tag:
- biorobotics 
- Machine Learning
- MATLAB
- Python
comments: false
---
    
     
#### Goal
Use EOG signals captured in real time to classify the eye gaze position of a user in real time. Similar projects have been able to classify a genral direction of movement in eyes using similar techniques. This is one of the first research projects that focuses on being able to classify not only the direction but also the relative position where the eyes are gazing. This high degree of accuracy will be accomplished by implementing an artificial neural fuzzy inference system. 

The EOG signals will be captured using electrodes and a BioRadio to perform differential amplification and digital conversion of the bio potential signals. 
MATLAB will be utilized to perform preprocessing of the signal. 
Once the data has been analyzed, a Fuzzy Neural Network (ANFIS) will be utilized to model what angle direction an eye is looking at. 

#### Data Collection
Raw data was collected to create a trainign set for the neural fuzzy network. A BioRadio with 2 Channels was used to collect vertical and horizontal movements of the eyes. Data was sampled at 960Hz. 

A ball on a computer screen would move horizontally and vertically across the screen. The balls coordinates are classified with the 2 channels of data collected. During these captures, no time data was captured, only position and coresponding EOG signal values. This data was stored in a simple matrix format. Over 35,000,000 data points were collected during the trials.

#### Post Processing
To simplify and clean the data the following was performed. 
- Normalize Data 
    - Take mean of signals when looking at center. 
    - Subtract the “centered” values from the current measured value. 
    - Reduces the drift between trials
    - Slide across 96 sample window size
- Down sample
    - Down sampling was executed to reduce data set sizes, reduce training time

#### MATLAB ANFIS
ANFIS was first implemented using a built in MATLAB library. This MATLAB function was capable of taking multiple inputs and mapping this data to a single dimension output. Since this issue is attempting ot map 2 inputs to 2 outputs, the 2-dimensional output was converted to a 1-dimensional mapped scale. This mapping would then alllow the output coordinates to be mapped to a single dimension array so it would be compatible with the MATLAB function. Upon analysis, the singl dimenison output values could then be converted back to a 2-dimensional map.   

Unfortunately, this mapping process created a large discontinuity in the training data; making it very difficult for ANFIS to analyis properly. 

#### Python ANFIS
To solve this issue, an open sourced ANFIS library written in Python, developed using SciPy and Numpy, was used. The benefit of this library was that it was able to setup ANFIS to evaluate 2 inputs and 2 outputs. 

Using a Python script, the training data was used to train the neural fuzzy netowrk. A Generalized Bell Curve Membership function was used. This was ran for various epoch amounts, with the best results occuring around 20 epochs.

#### Real-Time Integration
Once the ANFIS was trained, it was necessary the evaluate this network using real time data. Since the BioRadio drivers and testing animations being used required MATLAB, it was necessary to have MATLAB call Python scripts that would be responsible for evaluating the ANFIS for the current values being measured. The Python script would return coordinates to MATLAB, and then plot the predicted location. 

To test this system, a ball was programmed to move across the screen in a know path. The user would follow this ball with his eyes and the predicted position was displayed as a different color ball. Some of the results are shown below. 

![]({{ site.url }}/assets/img/gaze_tracking_result_plot.png)



