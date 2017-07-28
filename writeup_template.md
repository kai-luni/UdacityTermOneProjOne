**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

[imageWhite]: ./examples/whiteLine.jpg "White Lines"
[imageCanny]: ./examples/canny.jpg "Canny "
[imageCut]: ./examples/cut.jpg "Cute Picture"
[imageFinal]: ./examples/final.jpg "Final Image"

---

### Reflection

### 1. Description of the pipeline

My pipeline consisted of 5 steps. First, I used thrsholds to pick out white and yellow pixel which might be street lines.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
