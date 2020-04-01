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


1.1 Describe your pipeline. As part of the description.
     My pipeline consisted of 6 steps:
         1. Region masking
         2. Generate grayscale image
         3. Detect edge
         4. Color selection
         5. Hough transform
         6. Region masking 
            Purpose: to remove the edge of the region masking of step 1

1.2 Explain how you modified the draw_lines() function.
    In order to draw a single line on the left and right lanes, I modified the draw_lines() function by steps as follow:
        1. Group the (x,y) coordinate of the segmented line by their slope range. where
               nagetive slope is right lane & positive slope is left lane
        2. Use polyfit() to find line will fit in the left lane (x,y) data set
        3. Use polyfit() result to create the line
        4. Repeat the process for the right lane

1.3 If you'd like to include images to show how the pipeline works, here is how to include an image:
![alt text](https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "Logo Title Text 1")


![0-Original.png](http://localhost:8888/view/writeup_images/0-Original.png)
![0-Original.png](http://localhost:8888/view/writeup_images/1-RegionMasking.png)
![0-Original.png](http://localhost:8888/view/writeup_images/2-GrayScale.png)
![0-Original.png](http://localhost:8888/view/writeup_images/3-EdgeDetection.png)
![0-Original.png](http://localhost:8888/view/writeup_images/4-ColorSelection.png)
![0-Original.png](http://localhost:8888/view/writeup_images/5-LaneDetection.png)
![0-Original.png](http://localhost:8888/view/writeup_images/6-SuperPosition.png)


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when the lane line is really close the region of interest, the region masking at the last step might erase some of the data. 

Another shortcoming could be the lane drawing function is not as perfect as I expected. Lots of improvements are needed to draw the line lay over the lane in the image. 


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to, for the draw_lines() function, we could normalize the slope by eliminating the extreme points. In this way, we could get rid of some "horizontal line" effects in some frame of the videos.

Another potential improvement could be to, for the parameters for the edge detection, the function still will pick up some small items on the road. We need to tune the parameter futher. 



