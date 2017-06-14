# **Finding Lane Lines on the Road** 
## Reflection

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I blurred image using gaussian blur function with
kernel size of 7. Then used Canny edge detection method to detect edges. I tweaked lo and high thresholds several times. Then defined
ROI to get masked edges. Used masked edge images to detect lines using Hough transform. 

In order to draw a single line on the left and right lanes, I modified draw_lines() fucntion to group lines detected in to
left lane ( postive slope) and right lane( negative slope). used soem threshodlgin to elimintate horizontal lines. 
After grouping all the points taht define each line in the output of Hough transform, used fitlien method to define a line
that best fits points in each group. The slope and intercept of each best fit line is calculated. Chose starting and ending
Y-coordinate value taht rmaisn same for both lanes. Used the x = (y - b)/m to calculate the start and end x coordinates for each lane.


## 2. Identify potential shortcomings with your current pipeline
Parameters used to define ROI, canny edge detection adn hough transform are suitable for given camera mounting position.
If camera position changes the pipline may not be able to adapt accoprdinly to fix the issue
Also, for video frames, soem fmraes were missing lane lines as my algorithm failed to find lines that match the criteria. This


## 3. Suggest possible improvements to your pipeline

Improve draw_lines algorithm to not miss lane lines entirely.
Use better polynomial fitting models to group hough tanrasform line points into lanes to cover curves
Learn the camera position and adapt the ROI and other parameters accordingly