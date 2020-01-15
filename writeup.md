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

### 1. Pipeline

My pipeline consists of five steps. First, 
- darker colors are removed by using the inRange() function,
![removed darker colors](threshold.png)
- then the image is blurred with a Gaussian filter,
- the next step detects edges, then
![edge detection](canny.png)
- irrelevant regions of the image are removed,
- finally, in the remaining image the Hough algorithm is used to detect lines .  
![lines detected](detected.png)

The detected lines are then filtered to remove unrealistic lines.

Beside the image processing pipeline two ideas are used to make the lane detection more robust. 
- For each lane line a different region of interest is used to minimize disturnaces and wrongly detected lines
- The detect_line() function can be called with different parameters so that line detection can be changed

In order to draw the detected lane lines I use m and b from the two detected lines
- to calculate the intersection point of the two lines, and
- the intersection of the detected lines with the y axis.
With these three coordinates a triangle (without base line) can be drawn.


### 2. Potential Shortcomings with current Pipeline

Possible shortcomings of the lane line detection pipeline: 
- different lighting conditions, e.g. at night or` artificial light
- in contruction areas, when different line markers are used
- damaged or old line markers, e.g. several (parallel) lines with different color, etc?
- in cities, when left or right line is missing
- processing speed


### 3. Suggest Possible Improvements to your Pipeline

By changing the required quality of the detected lines a factor how certain the lane detection pipeline is can be used for further decision making.
Currently only minimum required length is changed, this mechanism can be extended to play around with different parameters to get the highest certainty of the detected lines,
 
