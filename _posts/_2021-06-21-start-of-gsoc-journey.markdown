---
layout: post
title:  "The start of my journey as a GSoC student"
date:   2021-07-12 08:00:20 +0530
---
Hi, I am Rishabh Vasudevan and I will be working as a Google Summer of Code Student with Drogue IOT, which is a part of the JBOSS community (Red Hat or IBM) on the project “Hey Rodney” wake word detection.

## Background

Early February I was going through the list of all the previous year organisations that had projects on machine learning. At that time I came across the JBOSS community website which had listed their idea list for GSoC’21. Among the projects I found the machine learning project “Hey Rodney” wake word detection. I have had previous experience with Natural Language Processing but not particularly in Trigger/Wake word detection.

I came in contact with the mentor of the project ( Jens Reimann ) who is also now my mentor for GSoC’21 and asked him a few questions about the project to increase my understanding of what the organisation was looking for. I saw YouTube videos, read research papers and a lot of blog posts on the topic. And then finally came up with a plan to implement the project.

## Overview of the project

The project is to make a program that will record X amount of seconds or until silence after it detects that the wake word “Hey Rodney” has been said. After that the program should send the recorded data to the cloud where the recording would be converted to text using speech to text transcription. 

__Optional Part:__ Making the same program run on an embedded device.

## About the Proposal

The proposal was split into 4 parts
- Collection of data
- Extraction of features
- Training the model
- Deploying it

__Collection of data:__  The first part of the project is collecting the data, we will request people to send audio samples of them saying “Hey Rodney”. For negatives and background we will be using the Google speech command dataset or the Mozilla common voice dataset.

__Extraction:__ The second step would be to extract features from the data so that our machine learning model can work with it.

__Training the model:__ The third step is to different models( simple convolution, convolution layer + Gated Recurrent Unit Layer) with multiple different parameters to find the optimal value between size of the model and accuracy( the size of the model is of high importance as later it has to run on embedded systems).

__Deployment:__  The fourth and the final step would be to put the final program together that will be able to recognize the wake word and also record the voice till silence or X amount of seconds and then send it to the cloud for further processing.

## The initial phase of data collection

Data collection is the single most important step in solving any machine learning problem. And there have been some problems in formulating an easy method for people to submit their voice samples.

As default apps in Windows and Mac do not provide support to change the sample rate or the encoding so we have to rely on third party apps to collect the data.

We have decided to use GitHub as a place where we will collect all the voice samples and people can submit their samples by making an issue in the repository. Collecting the data in a public repository also follows the spirit of open source.

## Conclusion

I am very excited for this journey and I am sure that I will learn a lot of things on the way.

I will keep updating you guys with more blogs on the topic and the journey. 

Thank you for reading

