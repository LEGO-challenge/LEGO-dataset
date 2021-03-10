
# De setup 
### How to use the dataset?
The dataset consist of images of LEGO bricks. These images have been labelled using XML files. To label them a tool called LabelImg has been used. The installation and usage instructions is on its [GitHub]( https://github.com/tzutalin/labelImg) page. Before labelling the images have been rescaled, downsizing them to 240x320px. This has saved a lot of storage space. 
## Shortened version of the tutorial
For this project a [tutorial]() posted by Nisarg Kapkar on Medium.com has been used. This being his tutorial he has full rights to take this down at any point in time. To make sure this project remains usable there is a shortened version of the tutorial down below.

### Step 1- Setup (Get and label images, Label_map, etc.)
It’s essential to provide properly labelled images, these will be used to train the model later on. The images for this step can be from the internet. Our dataset has been uploaded in the data folder, feel free to try it yourself. If you want to label your own images, you can use LabelImg. It has also been used for our dataset and it worked great. 
It is required to split the dataset in a testset (about 20% of the images) and a trainset (about 80% of the images). In case the model starts giving a large number of false positives it would be advised to increase the relative size of amount the test images.

At this point in time to finish up the step you need to fulfil the following steps:
- Create label_map.pbtxt. It contains all the classes the model needs to recognize. This is a labelmap with three types of fruit:
```
item {
    id: 1
    name: 'apple'
}
item {
     id: 2
     name: 'orange'
}
item {
     id: 3
     name: 'banana'
}
```
- Download a pre-trained model to apply transfer learning [TensorFlow 2 Detection Model Zoo]( https://github.com/tensorflow/models/blob/master/research/object_detection/g3doc/tf2_detection_zoo.md)
- Download generate_tfrecords.py script from [this GitHub page](
https://github.com/sglvladi/TensorFlowObjectDetectionTutorial/tree/master/docs/source/scripts).
This GitHub page has been forked

### Step 2- Setting up the google drive setup
To start off it's required to make a folder and call it "TensorFlow"

Once done it is time to import the files from step 1 into the just created structure
-	Add train and test images (Including their xml.files) to training_demo/images/train and training_demo/images/test
-	Add the label_map.pbtxt file to training_demo/annotations
-	Add the generate_tfrecord.py script to scripts/preprocessing
-	Extract the downloaded pre-trained-model and add the extracted folder to training_demo/pre-trained-models
-	Go to training_demo/models and make a new folder with the name of the pre named model you downloaded copy the pipeline.config file from training_demo/pre-trained-models/ssd_resnet50_v1_fpn_640x640_coco17_tpu-8 and past it into the newly created folder

after all this your structure should look like this:

```
TensorFlow
├───scripts
│   └───preprocessing
│     └───generate_tfrecord.py 
└───workspace
    └───training_demo
        ├───annotations
        │   └───label_map.pbtxt 
        ├───exported-models
        ├───images
        │   ├───test
        │   │     └───test images with corresponding XML files
        │   └───train
        │         └───train images with corresponding XML files
        ├───models
        │   └───my_ssd_resnet50_v1_fpn
        │     └───pipeline.config
        └───pre-trained-models
            └───ssd_resnet50_v1_fpn_640x640_coco17_tpu-8
```

It is possible to change the structure, but it requires renaming the paths in the code, so it can be found. This way a different pre trained model can be used, or two sets of prerequisites can be stored under different names.

### Step 3: Open the notebook
The original version of the notebook can be found [here]( https://github.com/Nkap23/TensorFlow_with_Colab_tutorial). There is also a forked version on our github. Copy the url from the github. Go to Google colab and open a new notebook. Click on the github tab, enter the url and open the notebook. 
To run the notebook on Google Colab go to runtime>change runtime type and select GPU as hardware accelerator. 
### Step 4-11: Run the code
Run the cells of code. Connect with the google drive where the TensorFlow folder is located in the first cell of code. Run the other cells of code up to step 11
For step 12 and 13 a few things need to be changed in the TensorFlow folder. Here are the direct instructions from the original tutorial:
### Step 12: Copying some files (orginal tutorial)
Copy the “model_main_tf2.py” file from “TensorFlow\models\research\object_detection” and paste it in training_demo folder. We will need this file for training the model.
Copy the “exporter_main_v2.py” file from “TensorFlow\models\research\object_detection” and paste it in training_demo folder. We will need this file to export the trained model.
### Step 13: Configure the pipeline file (orginal tutorial)
Go to ‘training_demo/models/my_ssd_resnet50_v1_fpn’. (or the folder you have created for the downloaded model in your ‘training_demo/models’ directory)
Open the pipeline.config file. (you can open a file in Colab by simply double-clicking it)
Change the lines shown below according to your dataset. (set paths according to your folders name and downloaded pre-trained-model)

**Line 3:**<br>
num_classes: 3 (#number of classes your model can classify/ number of different labels)

**Line 131:**<br>
batch_size: 16 (#you can read more about batch_size here)

**Line 161:**<br>
fine_tune_checkpoint: "pre-trained-models/ssd_resnet50_v1_fpn_640x640_coco17_tpu-8/checkpoint/ckpt-0" (#path to checkpoint of downloaded pre-trained-model)

**Line 162:**<br>
num_steps: 250000 (#maximum number of steps to train model, note that this specifies the maximum number of steps, you can stop model training on any step you wish)

**Line 167:**<br>
fine_tune_checkpoint_type: "detection" (#since we are training full detection model, you can read more about model fine-tuning here)

**Line 168:**<br>
use_bfloat16: false (#Set this to true only if you are training on a TPU)

**Line 172:**<br>
label_map_path: "annotations/label_map.pbtxt" (#path to your label_map file)

**Line 174:**<br>
input_path: "annotations/train.record" (#path to train.record)

**Line 182:**<br>
label_map_path: "annotations/label_map.pbtxt" (#path to your label_map file)

**Line 186:**<br>
input_path: "annotations/test.record" (#Path to test.record)

### Step 14: TensorBoard
Run the code to start the tensorboard. At first , you might receive a message saying “No dashboards are active for the current data set”. But once the training start, there will be training metrics. 
### Step 15: The training.
Before the fun will start you need to check if the code !pip install lvis –make code thingy-
Is present. We weren’t able to train the model without it. The Lvis enables reading and interaction with the (visual) annotation and helps evaluate the results.

### Step 16 -20: Save and test
You’re almost done! After training and saving the model it is time for testing. Upload some testing pictures to google drive, add the path to them in step 19 and test them in step 20. 
Near the bottom of step 20 there is a line with max_boxes_to_draw = 1. Change the number to to the amount of boxes you want to be drawn. Underneath there is the min_score_thresh. Every prediction underneath the threshold won’t be drawn. Changing the number will change the threshold. 
