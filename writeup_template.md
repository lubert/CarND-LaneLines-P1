# **Finding Lane Lines on the Road** 

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

I added a couple of functions to help extrapolate the line segments.

`sort_lines(img, lines)` takes the line segments returned from `hough_lines()` and returns an array of points respectively for the left and right lanes markers.

`draw_fit_lines` is a replacement for `draw_lines`, which takes the output from `sort_lines` and then uses `cv2.fitLine` to get the best-fit line for each lane marker. The lowest Y value in each array of points is used as a bound to calculate the start and end points for the best-fit line.

#### Final image:
![alt text][image6]

### Potential shortcomings

- The approximate best-fit lines do not work well for curves or turns
- The mask is highly tailored to the resolution of the test videos
- `sort_lines` sorts the lines based on which half of the image it appears. This doesn't work well for sharp turns
- Other edges and video artifacts can distort the best-fit line

### Possible improvements

- Better preprocessing of the image to remove unwanted edges. I tested out a pipeline with an extra step at the beginning filtering for white and yellow colors, and it seemed promising, though I didn't have time to completely finish it up.
- Generate a proportional mask based on the image dimensions
- Use a clustering algorithm to group the points into left/right lane markers
- Use a best-fit curve instead of a best-fit line
