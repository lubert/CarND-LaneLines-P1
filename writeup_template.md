# **Finding Lane Lines on the Road** 

---

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/1-grayscale.png "Grayscale"
[image2]: ./examples/2-blurred.png "Gaussian blur"
[image3]: ./examples/3-canny.png "Canny"
[image4]: ./examples/4-masked.png "Canny"
[image5]: ./examples/5-hough.png "Canny"
[image6]: ./examples/6-merged.png "Canny"


---

### Pipeline

#### Step 1: Convert image to grayscale
![alt text][image1]

#### Step 2: Gaussian blur image
![alt text][image2]

#### Step 3: Apply Canny edge detection
![alt text][image3]

#### Step 4: Mask image
![alt text][image4]

#### Step 5: Draw Hough lines
![alt text][image5]

I added a couple of new functions to help extrapolate the line segments.

`sort_lines(img, lines)` takes the line segments returned from `hough_lines()` and returns an array of points respectively for the left and right lanes markers.

`draw_fit_lines` is a replacement for `draw_lines`, which takes the output from `sort_lines` and then uses `cv2.fitLine` to get the best-fit line for each lane marker. The lowest Y value in each array of points is used to calculate the start and end points for the best-fit line.

#### Final image:
![alt text][image6]

### Potential shortcomings


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### Possible improvements

A possible improvement would be to ...

Another potential improvement could be to ...
