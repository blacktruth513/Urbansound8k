# UltrasoundAudio8k
###Sound Classification using Librosa, ffmpeg, CNN, Keras, XGBOOST, Random Forest.
### Dataset and its structure

1. We can use Urban Sound Classification ( https://urbansounddataset.weebly.com/ ) dataset which is quite popular.
2. Whichever dataset you are using, it is important to understand its structure and how to extract required features out of them.
3. For UrbanSound8K dataset, it can be downloaded using the following link ( https://goo.gl/8hY5ER  ). It downloads a compressed tar file of size around 6GB.
4. On extracting it, it contains two folders named 'audio' and 'metadata'.
5. Audio folder contains 10 folders with name fold1, fold2 and so on, each having approximately 800 audio files of 4s each.
6. Metadata folder contains a .csv file having various columns such as file_id, label, class_id corresponding to label, salience etc.
7. Complete description can be found here https://urbansounddataset.weebly.com/urbansound8k.html

### Research Paper and Resources to follow

1. https://github.com/meyda/meyda/wiki/audio-features
2. https://github.com/tyiannak/pyAudioAnalysis/wiki/3.-Feature-Extraction
3. https://medium.com/@ageitgey/machine-learning-is-fun-part-6-how-to-do-speech-recognition-with-deep-learning-28293c162f7a
4. https://towardsdatascience.com/urban-sound-classification-part-1-99137c6335f9
5. https://www.analyticsvidhya.com/blog/2017/08/audio-voice-processing-deep-learning/

### Library To Use

We can use librosa library which can be installed using 
> pip install librosa

It uses ffmpeg as backend to convert and read some of the audio files. So to install ffmpeg, you can use 
> apt-get install ffmpe

Librosa library can read audio files and convert them to there amplitude values for each sample of audio. Let us say there is an audio file of 4s and sampling rate of audio file is 22050 Hz. This means that audio file is made using amplitude samples such that 22050 samples of amplitudes are recorded in each second. Hence a 4s audio file with sampling rate 22050 can be expressed as an array of 4\*22050=88200 size 


#### How to Load Audio Files and Extract Features

Using load method of librosa library, we can read audio files. It takes file path as input and returns an array having amplitude samples along with sampling rate of file.

Librosa library has many methods already build to extract features mentioned in resources which then returns another array of features.
We can use various combinations of those features. This is something you can play around and try how and which features like mfcc, spectral features, energy etc affect the classification of audio. 

For eg, in first stage you can extract only mfcc features and then build up a model and check the accuracy. Then try the same with other features. In order to further improve accuracy, you can also try to use more than one type of features and check the results.

### Using CNN to classify sound

This is a very classical way of sound classification as it is observed that similar type of sounds have similar spectrogram (read resource 3 to understand more about spectrogram). A spectrogram is a visual representation of the spectrum of frequencies of sound or other signal as they vary with time. And thus we can train a CNN network which takes these spectrogram images as input and using it tries to generalize patterns and hence classify them.

### MFCC Guide
The first step in any automatic speech recognition system is to extract features i.e. identify the components of the audio signal that are good for identifying the linguistic content and discarding all the other stuff which carries information like background noise, emotion etc.

The main point to understand about speech is that the sounds generated by a human are filtered by the shape of the vocal tract including tongue, teeth etc. This shape determines what sound comes out. If we can determine the shape accurately, this should give us an accurate representation of the phoneme being produced. The shape of the vocal tract manifests itself in the envelope of the short time power spectrum, and the job of MFCCs is to accurately represent this envelope. This page will provide a short tutorial on MFCCs.

Mel Frequency Cepstral Coefficents (MFCCs) are a feature widely used in automatic speech and speaker recognition. They were introduced by Davis and Mermelstein in the 1980's, and have been state-of-the-art ever since. Prior to the introduction of MFCCs, Linear Prediction Coefficients (LPCs) and Linear Prediction Cepstral Coefficients (LPCCs) (click here for a tutorial on cepstrum and LPCCs) and were the main feature type for automatic speech recognition (ASR), especially with HMM classifiers. This page will go over the main aspects of MFCCs, why they make a good feature for ASR, and how to implement them. 
##### www.practicalcryptography.com/miscellaneous/machine-learning/guide-mel-frequency-cepstral-coefficients-mfccs/
