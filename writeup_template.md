**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

[imageWhite]: ./reportPictures/whiteLine.jpg "White Lines"
[imageCanny]: ./reportPictures/2 canny.jpg "Canny "
[imageCut]: ./reportPictures/cut.jpg "Cute Picture"
[imageFinal]: ./reportPictures/final.jpg "Final Image"

---

### Reflection

### 1. Description of the pipeline

My pipeline consisted of 4 steps. First, I used thrsholds to pick out white and yellow pixel which might be street lines and color them white, the rest is draw black to get the optimum of a contrast.

<img src="reportPictures/1 whiteLine.jpg" width="480"/>

In step two Canny Edge Detection is used to mark all edges on the picture.

<img src="reportPictures/2 canny.jpg" width="480"/>

In step three a tetragon is defined and applied on the picture, to cut out the edges that are of no interest. This is possible as the the area of interest for lanelines is always about the same.

<img src="reportPictures/3 reportPictures/3 cut.jpg" width="480"/>

In the final step Hough Line Transform is applied to find straight lines in the edges. In order to draw a single line on the left and right lanes, I modified the draw_lines() function by firstly seperating the slopes into positive and negative ones, this is possible as there are just two lines to be drawn of which one has a rising slope and one has a falling slope.

For each line 4 values are need to draw it, x1, y1 of the start and x2, y2 of the end. y1 is the lower edge of the screen and y2 is the upper edge of the tetragon. For x1 I first need the mean slope of that line. For that I exclude outlies, which are slopes that stay further from the mean value as the standard deviation of all slopes is. With this estimated slope I take all remaing lines, take one point of them and estimate there x value at the lower edge of the screen, which is x1. From all this estimated x1 values I take the mean value again. With the now estimated x1, y1 and slope I can also estimated x2 at the hight of y2.

As the light condition in the extra challenge are worse, I included a mechanism  that draws the last found line as long as the algortihm can not see the lane line anymore. This one is drawn blue instead of red to make it visible that the algorithm is blind at this moment.

<img src="reportPictures/4 final.jpg" width="480"/>

### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming is visible in the challenge video, the lane line can not be found under every condition and would need to be further improved before it can be used in a practical application. For a practical application in a self driving car its also questionable if its enough to just find the lines in certain areas of the screen and just two of them. Here in Germany par example, if the is a construction side there would be yellow lines drawn over the white ones and they have a higher importance then. For a real life application the algorithm would be much more complex.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to to further improve the contrast to find the lane lines und different weather conditions. Another possible improvement would be to find all lane lines on the screen to make the algorithm applicable for practical application. Another possible improvment would be to smoothen the change of position of the lines so they dont jump around.
