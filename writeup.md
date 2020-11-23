# **Finding Lane Lines on the Road** 

## Writeup Template

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 6 steps:
1. The image is converted to a grayscale
2. Applied a Gaussian Noise with kernel size = 5
3. Applied a Canny transformation
4. The masked image (region of interest) is calculated
5. Calculate the hough lines based on the region of interest
6. Draw the recognised lines with red, overlapping the original lines on the pictures (videos)

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by calculating the slope of the lines as ${\frac {y_2-y_1} {x_2-x_1}}$. Then the angle of each line is calculated as ${\theta = \frac{180} {\pi}arctan\frac{y_2-y_1} {x_2-x_1} }$

Te line with the following rules are considered as the road lines:
$20^{\circ} <|\theta| < 40^{\circ} $
$\theta < 0$ - Left line
$\theta > 0$ - right line
Others are omitted.


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when the road type, brightness, etc is changed (e.g. if the road contains shadows)

Another shortcoming could be what would happen if he road has been repaired recently and the new road line has not being painted yet


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to draw solid line till, at least half a way to the horizont based on extrapolation data and assume that the line is not changed during the straightforward driving
