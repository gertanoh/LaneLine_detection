# **Finding Lane Lines on the Road** 
Data and Code skeleton from [https://github.com/udacity/CarND-LaneLines-P1](Udacity)


## Reflection
The goal of the project was to build a pipeline to dectect the lanes of the road.

### 1. Pipeline

The pipeline consisted of five steps.
After plotting out the images, the lanes road lines colors were identified.
* So the first step was to filter the lanes road colors.
On the tests images and videos, the yellow and white filter does not show better improvement. Therefore, this step could be removed. 
* Then, I applied grascale, then a gaussian filter to remove the noise and blur the image.
* The canny edge detector was applied with thresholds found using code at [link](https://www.pyimagesearch.com/2015/04/06/zero-parameter-automatic-canny-edge-detection-with-python-and-opencv/
). 
* The next step was the Hough line function. 
* To improve draw_lines, I used an average method. I computed the average slope and intercept on left and right lanes. I chose the y values: the bottom images and the middle of images. With the y values, slopes and intercepts, I was able to find the x values associated. For the videos tests, I had to modify the functions as for some frame, no lanes were found. The video was then jittery. I used an average of the previous frames lanes for the current video frame if none was found. Otherwise, the lane of the frame was the average of all previous frames lanes.

### 2. Shortcomings 
* This pipeline would not work with curvy lanes roads as the lanes are drawn by averaging lines.
* Also, when tried on the optional challenge, the pipeline did not work under the shadow.

### 3. Improvements
* A better color filter (filter in other color space) would improve the accuracy
* A better model for detecting the road (instead of lines, curves)

