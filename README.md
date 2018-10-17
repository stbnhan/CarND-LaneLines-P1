# **Finding Lane Lines on the Road** 

## CarND - Project 1

### Steven Han

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/laneLines_thirdPass.jpg "Example"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 6 steps:

1. First, I selected the color spectrum I wanted. This was done by filtering RGB values. This allowed the scope to be smaller as the filter picked out yellow and white lanes.

2. Then, I converted the images to grayscale which gives one color channel to apply image processing filters.

3. Image processing filters included:
  i.    Canny Filter - Edge detection by detecting sudden change in brightness (hence, grayscale is necessary)
  ii.   Gaussian Blur - This technique reduces noise from edge detection by smoothing out

4. As lanes are only present on bottom half of the camera feed, I selected a trapezoid shaped region of interest to filter out other cars and other obstacles out of region.

5. Hough transform technique was used to identify lines through voting procedure carried out in a parameter space. This gives the end coordinates of lines, which is then passed to draw detected lines.

6. Last but not least, I made the lines smoother by averaging & extrapolating lines. The left and right lanes were separated by its slope polarity, as well as filtering out any horizontal slopes by only considering extreme slopes.

An example of what the result looks like:
![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when different shades of lanes are present on the road. The current algorithm won't be able to detect lanes that are not clearly yellow or white (challenge problem).

Another shortcoming could be if the lanes were blocked by another vehicle coming in.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to use different color spectrum (such as HSV and HSL) to handle different brightness of the lanes.

Another potential improvement could be to add another camera for different angle view to cover more visibility.
