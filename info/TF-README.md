#### TensorFlow

<p align="center"><img src="https://github.com/LEGO-challenge/LEGO-dataset/blob/main/ReadMePictures/tensorflow.png"/ alt="tf-logo2"  width="237" height="53"></p>

TensorFlow is a is a free and open-source machine learning library that’s developed by google. It was initially released in 2015 and it’s used for several different tasks. We used it for training an object detection model. A big advantage is that it is free to use, making it work with our restricted budget . More importantly are the loads of documentation on it. This is important because at the start of the project we were all as complete novices in the world of machine learning and image recognition. Another important part of our decision to use Tensorflow is that the models run on mobile using TensorFlow lite. This would mean that it’s possible to use a TensorFlow model, in an android app for instance. The process of converting a regular TensorFlow model for a mobile app is supposed to be relatively simple.

#### Our model

When we were still in an earlier stage of the project someone on YouTube named [Daniel West](https://www.youtube.com/watch?v=04JkdHEX3Yk "Daniel West's YouTube channel") caught our attention. Daniel had made some videos regarding a LEGO sorting machine that he had built out of LEGO’s. The machine was set up using TensorFlow and because of this we met a with video call. One of the biggest takeaways from the call for us was that we could not create a custom model for the project. We simply didn’t have the time and were also we too inexperienced. Daniels advice was to find a pretrained model and retrain it using our dataset so it meets our requirements. After some reading on the internet, we figured that a variation of RESNET would be a good option for us. 

<p align="center"><img src="https://github.com/LEGO-challenge/LEGO-dataset/blob/main/ReadMePictures/resnet50.png"/ alt="renet-image"  width="340" height="128"></p>
