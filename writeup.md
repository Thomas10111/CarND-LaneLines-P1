# **Finding Lane Lines on the Road** 

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

[![removed brighter colors](threshold.png)]

My pipeline consists of five steps. First, 
- darker colors are removed by using the inRange() function,
[![removed brighter colors](threshold.png)]
- then the image is blurred with a gaussian filter,
- the next step detects edges, then
- irrelevant regions of the image are removed,
- finally, in the remaining image the Hough algorithm is used to detect lines .  

The detected lines are then filtered to remove unrealistic lines.

Beside the image processing pipeline two ideas are used to make the lane detection more robust. 
- For each lane a different region of interest is used, to reduce the number of wrongly detected lines
- Another idea is to start with a high requirement and then if no lines can be detected reduce the required quality.

In order to show the detected lines in the original image I use m and b from the two detected lines
- to calculate the intersection point of the two detected lines, and
- the intersection of the detected lines with the y axis.




If you'd like to include images to show how the pipeline works, here is how to include an image: 




### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...
How does the line detection pipeline work
- at night when lighting conditions are different
- in contruction areas when there are markers instead of lines, several (parallel) lines with different color, etc?
- in cities when left or right line is missing


### 3. Suggest possible improvements to your pipeline

By changing the required quality of the detected lines a factor how certain the lane detection pipeline is can be used for further decision making.
Currently only minimum required length is changed, this mechanism can be extended to play around with different parameters to get the highest certainty of the detected lines,
 
