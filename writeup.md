# **Finding Lane Lines on the Road** 


---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./test_images_output/segments/solidWhiteCurve.jpg "Solid White Curve"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 6 steps:
1. convert the input image to gray scale image
2. apply blur effect on the gray scale image
3. generate Canny edges detection image from the blurred gray scale image
4. create masked region data from the Canny edges image data
5. generate Hough Lines data using the masked region data
6. produce the final image by apply weighted image transformation using Hough Lines data and the original input image


In order to draw a single line on the left and right lanes, I modified the draw_lines() function as follow:

1. calculate slope for each line points
2. track left line data by evaluate for negative slope value, otherwise track right line data 
3. once left and right lines data collected, peform the following steps to draw a single continuous line
    * get average of the slope, y-intercept, x-point, y-point
    * calculate the low/min x-point and high/max x-point
    * draw the line using low/min x-point and high/max x-point


Example of lines visualization image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


The current lanes detection pipeline is not work well with sharp turn lanes and blurry lanes.



### 3. Suggest possible improvements to your pipeline


