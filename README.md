# Computer-visioin
Overview

This code is designed to detect persons in a CCTV camera video and capture their images if they fall within a specified region of interest (ROI). The ROI coordinates are given in a JSON file, and the video is provided as a file. The output of the code is a video file that has the ROI highlighted and any detected persons within the ROI are captured as images. Persons outside the ROI are redacted (blacked out) in the output video.

Dependencies

The code requires the following libraries:

cv2 (for image processing and video manipulation)
json (for parsing the JSON file with the ROI coordinates)
Code details
The code begins by loading the JSON file with the ROI coordinates and extracting the coordinates for the two ROIs.

The video file is then loaded using the cv2.VideoCapture() function.

An object detector is initialized using the cv2.CascadeClassifier() function and the specified XML file.

A video writer is set up to create the output video file. The output video file is initialized with the same size as the first frame of the input video.

The input video is then processed frame by frame. For each frame, it is first converted to grayscale using the cv2.cvtColor() function. The grayscale frame is then passed to the object detector to detect any objects. If any objects are detected, they are checked to see if they fall within one of the ROIs. If an object falls within an ROI, the frame is cropped to the ROI and the image is saved. If an object does not fall within an ROI, it is redacted (blacked out) in the frame. The processed frame is then written to the output video file.

The video writer is released and any open windows are closed at the end of the code.

Usage

To use the code, modify the jpath and vpath variables to specify the paths to the JSON file with the ROI coordinates and the input video file, respectively. The code can then be run to process the video and create the output video file.

Problem

An error occurred while processing the video:

Copy code
OpenCV(4.5.5) D:\a\opencv-python\opencv-python\opencv\modules\objdetect\src\cascadedetect.cpp:1689: error: (-215:Assertion failed) !empty() in function 'cv::CascadeClassifier::detectMultiScale'
