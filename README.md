### You know the [find your brick April fool’s joke from LEGO](https://twitter.com/LEGO_Group/status/1112625676836880384?ref_src=twsrc%5Etfw%7Ctwcamp%5Etweetembed%7Ctwterm%5E1112625676836880384%7Ctwgr%5E%7Ctwcon%5Es1_&ref_url=https%3A%2F%2Fbrickshow.com%2F2019%2F04%2Fa-look-at-legos-april-fools-prank-for-2019%2F "the tweet from LEGO")? We tried to make that prank reality. There were some obstacles, and we would like to share our finds.

<p align="center"><img src="https://github.com/LEGO-challenge/LEGO-dataset/blob/main/ReadMePictures/Results.jpg"/ alt="accurate object detection results"  width="262" height="326"></p>

#### The origin
The LEGO challenge was pitched by a teacher at the Hague university of applied sciences. The idea was that there would be an app that people could use to search for a specific LEGO brick in a pile of bricks. The use of machine learning was not mandatory for this challenge, however it was seen as the most likely course of action. Several routes have been considered and investigated and eventually TensorFlow seemed to be the best option because a lot of information could be found on it and therefore it seemed to be fairly beginner friendly. This was very important as none of us had any experience with machine learning or AI for that matter.

<p align="center"><img src="https://github.com/LEGO-challenge/LEGO-dataset/blob/main/ReadMePictures/1200px-TensorFlowLogo.svg.png"/ alt="TensorFlow Logo"  width="120" height="100"></p>

#### Object detection
To train the object detection model we used [this tutorial from medium](https://medium.com/swlh/tensorflow-2-object-detection-api-with-google-colab-b2af171e81cc). It has been altered somewhat for it to work with our dataset. This is only the tip of the iceberg though, as most of our time and effort was spent learning about AI and machine learning and figuring out what worked for us and what didn't. For more information check out the 'info' folder (beware most of it will be Dutch).

While setting up the model went smoothly, there were a few problems while training the model. The biggest problem we ran into was the batch size. The model wouldn’t train if the number of pictures couldn't be divided by the batch size. We solved this problem by making the batch size 8 and both the train and test sets divisible by 8. 

A small hiccup we ran into was that no module named 'lvis' has been installed. That problem can be solved by adding the line `!pip install lvis` above the training section.

#### Classification
Before the object detection model we had a classification model. [This tutorial from codelab](https://codelabs.developers.google.com/codelabs/recognize-flowers-with-tensorflow-on-android#0 "the tutorial") has been used. Starting with a classification model did make this easier in the long run. The first thing that we realized is to make your own dataset. The dataset was consisted of 9 classes with over a thousand pictures of each class. The pictures have been made using the burst mode to make lots of pictures.

To make our dataset work we sorted the photographs of the different type of LEGO bricks into their own folder, with the class name as folder name. We uploaded it to Google Drive and used the drive mount to upload our dataset to Google Colab. To make another dataset work the amount of classes needs to be changed. Under "Add a classification head" section, in the first code cell is the line `tf.keras.layers.Dense(5, activation='softmax')`. Change the 5 into the number of classes the dataset has. 

We hope this information will help you with your own machine learning project.

Sincerely, 
The LEGO Challenge.
