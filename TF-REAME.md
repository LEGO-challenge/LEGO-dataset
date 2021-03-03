#### TensorFlow

<p align="center"><img src="https://github.com/LEGO-challenge/LEGO-dataset/blob/main/ReadMePictures/tensorflow.png"/ alt="tf-logo2"  width="237" height="53"></p>

TensorFlow is a is a free and open-source machine learning library that’s developed by google. It was initially released in 2015 and it’s used for several different tasks however we needed it for training an object detection model. We chose to use TensorFlow as our budget was quite restricted and TensorFlow is free to use. More importantly however there is a lot of documentation on it and many people have gone before us in working with it. This is important because we all went into this project as complete novices in the world of machine learning and image recognition. Another important part of our decision to use it is that there is a version of it that supports mobile devices which is called TensorFlow lite. This would mean that it’s possible to use a TensorFlow model, in an android app for instance, and the process of converting a regular TensorFlow model to be used in a mobile app is supposed to be relatively simple.

#### Our model

<p align="center"><img src="https://github.com/LEGO-challenge/LEGO-dataset/blob/main/ReadMePictures/resnet50.png"/ alt="renet-image"  width="340" height="128"></p>

When we were still in an earlier stage of the project someone on YouTube named Daniel West caught our attention. Daniel had made some videos regarding a LEGO sorting machine that he had built out of LEGO’s. The machine was set up using TensorFlow and because of this we figured Daniel would have some useful advice for us. We sent him an E-mail to see if we could set up a call and he responded that he was quite interested in our project. One of the biggest takeaways from the call for us was that we could not create a custom model for the project. We simply didn’t have the time and were also we too inexperienced. Daniels advice was to find a pretrained model and retrain it using our dataset so it meets  our requirements. After some reading on the internet we figured that a variation of RESNET would be a good option for us. 
