# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

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

Step 1: Convert image to grayscale

[image1]: ./examples/1-grayscale.png "Grayscale"

Step 2: Gaussian blur image

[image1]: ./examples/2-blurred.png "Gaussian blur"

Step 3: Apply Canny edge detection
Step 4: Mask image
Step 5: Draw Hough lines

I added a couple of new functions to help extrapolate the line segments.

`sort_lines(img, lines)` takes the line segments returned from `hough_lines()` and returns an array of points respectively for the left and right lanes markers.

`draw_fit_lines` is a replacement for `draw_lines`, which takes the output from `sort_lines` and then uses `cv2.fitLine` to get the best-fit line for each lane marker. The lowest Y value in each array of points is used to calculate the start and end points for the best-fit line.

### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
