# **Finding Lane Lines on the Road** 

## Writeup 



[image1]: ./lzTest1.jpg
[image2]: ./Challenge.JPG


### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps

1.Convert the images to grayscale

2.Apply a Gaussian noise filter

3.Use CannyEdge algorithm to find edges

4.Filter out irrelevant area of the image

5.Use Hough Transform to get lines 

In order to draw a single line on the left and right lanes, I modified the draw_lines() function:

1.Seperate lines into left lines and right lines by slope ((y2-y1)/(x2-x1))

2.Use 1st order polyfit to get single line function on each side

3.Use predined ymax and ymin to calculate the end points for both left and right line

In the following image blue line marks the region of interest, this region should be calibrated for vedios  

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline

Shortcomings:
When the background color is close to bright white or yellow, lines can not be detect properly.

Sharp curves will mislead the line into wrong direction.

Engine hood, road boundary, other vehicles are all disturbances for line detection.


### 3. Suggest possible improvements to your pipeline

The parameters of CannyEdge, HoughLines, the size and shape of mask area should be carefully calibrated according to camera setup and
environment condition. Maybe these parameters can be changed addaptively in runtime.

![alt text][image2]
