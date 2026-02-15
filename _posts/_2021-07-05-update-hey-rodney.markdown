---
layout: post
title:  "Update for Hey Rodney wake word detection "
date:   2021-07-12 08:00:25 +0530
---
As the first evaluation is coming close and it starts in less than a week. I decided to give an update of what is the position of the project

There was some delay in the project  as I had my college end semester lab practicals and final exams till the 25th of June.

## Updates:

-  I started out with writing the audio classification script manually which is the  audio processing and model training, but then I found that Shawn Hymel has a script that does exactly what I was planning to do. Therefore I started working with that.

- The model accuracy was very low and it did not overlap background noise to the audio sample which made it so that the model could not recognise audio sample when there was backround noise.

-  I made a lot of changes in the script to remove unneccary parts and made it one single script for audio processing and training. I also changed the training model and made it to a model with 3 layers of convolution and 3 layers of maxpool with regularisation and dropout to it.

-  The model also had a very big negative bias as the amount of positive samples was way less than the negative samples. This led to the fact that the model predicted negative outcome more often than not so even a lot of positive samples were marked as negative. I added a multiplicity factor to the script which multiples the number of positive samples and makes the number of positive and negative samples comparable.

-  I also added a function in the script to randomly overlaps background noises to the audio sample at various different sound levels in the audio processing part. This would make the model more robust and will make sure that it can handle background noise also.

-  I also added the conversion of model from .h5 to tflite in the end of the script

- I made a python script which when given wav files will output the prediction given by the model in the form of an excel sheet. There will be three columns index, actual answer and predicted answer.

- I have also made a script which will take input from the laptop mic at a sample rate of 8000 Khz and then it convert the sound sample to its respective MFCC ( The MFCC parameters are kept same as the one in processing as otherwise it would give wrong predictions ). The MFCC is then reshaped and made to pass through the model. After that the prediction is printed and whenever the prediction is over 0.8 the model will program prints activated.

-  The next thing that I have to work on is to make a docker container which will have all these scripts so that it is easy to use on any operating system.

## Shifting of a deliverable


I requested my mentor to change the date of one deliverable to which he agreed, the deliverable was to provide a model that will be able to differentiate between voice and silence I asked for this change because even after a lot of research I could not find a concrete way to go foward with that yet. Most VAD models use RNN's in them and models with RNN's cannot be converted to tflite. So I will have to use a VAD with a CNN network architecture.

## Discarding of the CNN + GRU model

I discarded the CNN + GRU model as they work good in case of speech classification but not as good in case of wake word detection. Reason being that speech and language have a pattern that can be learned by the model whereas wake word detection is more like image classification where the MFCC acts as the image. Therefore CNN model will provide more accuracy and will also be of smaller size.
Another reason was also that models containing a RNN layer cannot be converted to tflite which is also a further goal of the project in order to make it run on embedded systems.

## Challenges faced

- While adding background noise to the speech samples librosa.load was giving a some
 trouble as whenever I was loading files more than 1 sec long the cpu usage dropped and the program became unbearably slow. So to tackle that I made a python script to break the background sound to multiple 1 sec long wav files. By doing this the problem got solved.

-  The model was not making good predictions on my voice as it had background noise and it had not trained on samples with background noise, The function to add random background noises at different volumes fixed this problem.

-  The initial tests of the model were giving very poor results. Which I later on found out was because of the imbalance in the amount of negative samples to positive samples. I added a part in the function which multiplies the amount of positive samples by the number provided and it 