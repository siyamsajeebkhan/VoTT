# CNTK Object Detection Video Tagging Tool

This tool provides end to end support for generating datasets for and validating Object Detection Models with CNTK.

It supports the following scenarios:

- Computer Assisted Tagging of Objects In Video Using Custom implementation of Camshift Algorithm
- Exporting Tags to CNTK format for training a CNTK object recognition model.
- Running and validating a trained CNTK object recognition model on new videos to generate stronger models. (Windows only for now, GPU recommended)

## Table of Contents
 - [Prerequisites](#prerequisites)
 - [Tagging Job](#taggingjob)
 - [Review/Itterate CNTK Object Detction Model](#review)
 - [Upcoming Features](#upcoming)
 
<a name="prerequisites"></a>
## Prerequisites
 1. Install [CNTK and Dependencies](https://github.com/Microsoft/CNTK/wiki/Object-Detection-using-Fast-R-CNN#setup)
 2. Download and Extract the app [release package](https://github.com/CatalystCode/CNTK-Object-Detection-Video-Tagging-Tool/releases)
 3. Configure CNTK-Config.json with the following properties
 
  ```json
   {
    "cntkPath" : "{CNTK Path default is c:/local/cntk}", 
    "cntkEnv" : "{CNTK Enviorment default is cntk-py34}" 
   }
  ```
 4. Run the app
 
 <img src="/media/1_home.jpg" alt="Home Page" height="300px" width="500px"/>
 
<a name="taggingjob"></a>
## Tagging Job 
 1. Load a video.
  
  <img src="/media/2_load.jpg" alt="Home Page" height="300" width="500"/>
   
 2. Configure the tagging job specifying the following preferences
 
    - Frame Extraction Rate (Number of frames to tag per a second)
    - Tagging Region Type (Rectangle, Point, Square)
    - Export Frames Until (How far to export)
    - Output directory (Directory to export training data to)
    - Model Path (Path of trained model this is optional for tagging 
    - Labels (Labels for tagging)
 
  <img src="/media/3_Job_Configuration.jpg" alt="Home Page" height="300" width="500"/>
 
 3. Tag the video frame by frame.
 
  <img src="/media/4_Tagging_Job.jpg" alt="Home Page" height="300" width="500"/>

 4. Export Video to CNTK Format using Menu or Ctrl/Cmd + E
 
  <img src="/media/5_Export.jpg" alt="Home Page" height="300" width="500"/>

<a name="review"></a>
## Review/Itterate CNTK Object Detction Model 
 1. Train model using [Object Detection using FastRCNN](https://github.com/Microsoft/CNTK/wiki/Object-Detection-using-Fast-R-CNN#train-on-your-own-data)<br> **Note: The data is already in CNTK format you do not have to run C1_DrawBboxesOnImages.py or C2_AssignLabelsToBboxes.py**
 2. Load new video that the model hasn't been trained on.
 3. Configure the tagging job specifying the following preferences
 4. Apply model to new video using ctr/cmd + R
 5. When model finishes processing, validate tags, re-export, retrain
 6. Repeat step #1 on new videos until model preformance is satisfactory.  

<a name="upcoming"></a>
## Upcoming Features 
- Image Directory Tagging Support
- Tagging Project Management 
- UI enhancements 
