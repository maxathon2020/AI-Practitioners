# AI-Practitioners

- Must read document https://github.com/maxonrow/maxathon
- Project Link : https://platform-hackathon.maxonrow.com/#/projects/5f583a6f30c062001bf39a32
- Team Members Full Name : 

  1. Raj Saraiya : https://github.com/rajsaraiya009
  2. Aashay Bane : https://github.com/Aashaybane
  3. Isabella Zhang : https://github.com/HackIsa

# Physical Distancing Detector
   A tool to monitor physical distancing from CCTV camera,videos using Python,Deep learning and Computer Vision technology. This tool automatically estimates distance between people from uncalibrated RGB cameras which can be used to detect voilation of Physical Distancing norms.

   Based on several research, maintaining physical distancing has proven to be a very effective measure to avoid risk of COVID-19 infection. In order to ensure physical distancing protocol in public places and workplace,this tool can be useful by monitoring the movement and behaviour of people weather the concerned person is keeping a safe distance from each other or not through streaming real time video from the CCTV cameras.

   This tool has following features:

   * Detect humans in the frame with yolov3 pretrained model.
   * Calculates the distance between every human who is detected in the frame.
   * It can be seen how many people are at High, Low and Not at risk.
   
## File Structure:
```python
    eagle_eye.py : Detects and calculates distance between humans
    utills.py    : Contain functions to calculate distance, scale, transformed points
    plot.py      : Contain functions to draw bird eye view and frame
    models       : Contain yolo weights and cfg.
    (IMPT NOTE: weights file is not present because of size issue.It can be downloaded from google drive link which is provided below)  
    data         : Contain video sample
    output       : Contain output frames
    output_vid   : Contain output videos(Empty for now)
    requirement    : requierments.txt
```
## Google Drive Link for Yolo weights  

 https://drive.google.com/drive/folders/1vORghr-g7BNIxeQOmj50efjWT760U2Zo?usp=sharing

## Requirements:
```python
python version : 3.7.7
opencv: 4.2.0
tensorflow: 2.1.0
numpy :1.18.3
```

## Dataset Used
We used a pretrained YOLOv3 Model for this project.

## Clone the repository
git clone https://github.com/maxathon2020/AI-Practitioners.git

## Install required packages
The provided requirements.txt file can be used to install all the required packages. Use the following command.
```python
pip install –r requirements.txt
```

## How to run the Physical Distancing tool
```python
 * If following same directory structure   
     python eagle_eye.py
 * If paths for models, input video is different then given directory structure
     python eagle_eye.py --model='model path' --video_path='path to video file' --output_dir='output directory' --output_vid='output vid directory'
```

## How to use the Physical Distancing tool
 * Run following command(if directory structure is same) 
     python eagle_eye.py
     
 * You will get a frame where you can draw ROI and distance scale. It will take 8 points on first frame using mouse click 
   event. First four points will define ROI where we want to monitor social distancing. Also these points should form 
   parallel lines in real world if seen from above(birds eye view). Next 3 points will define 6 feet(unit length) 
   distance in horizontal and vertical direction and those should form parallel lines with ROI. Unit length we can take 
   based on choice. Points should pe in pre-defined order - bottom-left, bottom-right, top-right, top-left, point 5 and 6 
   should form horizontal line and point 5 and 7 should form verticle line. Horizontal and vertical scale will be
   different. Gif below will help understand points better.
   
 * We will transform prespective of ROI so that we can have top view of scene or ROI. This top view or bird eye view has 
   the property that points are distributed uniformally horizontally and vertically(scale for horizontal and vertical 
   direction will be different). So for bird eye view points are equally distributed, which was not case for normal view.
   
 * YOLO V3 is used to detect humans in frame and by calculating bottom center point of bounding boxe around humans, 
   we transform those points to bird eye view. And then calculates risk factor by calculating distance between
   points and then drawing birds eye view and drawing bounding boxes and distance lines between boxes on frame.
   
 * Distance calculation works best for ROI.


## Here is a demo containing the application output:

![Alt Text](https://github.com/maxathon2020/AI-Practitioners/blob/master/demo/demo.gif)

## Eagle Eye View 

![Alt Text](https://github.com/maxathon2020/AI-Practitioners/blob/master/demo/birds-eye-view.gif)


## Idea Credits 

 Landing.ai

## References

 Yolov3 object detection : https://www.learnopencv.com/deep-learning-based-object-detection-using-yolov3-with-opencv-python-c/ 
 
 Prespective Transform : https://opencv-python-tutroals.readthedocs.io/en/latest/py_tutorials/py_imgproc/py_geometric_transformations/py_geometric_transformations.html

