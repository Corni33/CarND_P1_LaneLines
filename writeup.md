**Finding Lane Lines on the Road**


### Reflection

###1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I .... 

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...

If you'd like to include images to show how the pipeline works, here is how to include an image: 


The goal of the project is to superimpose straight lines over the lane markings in an image of a road using basic image processing techniques.

The pipeline I used goes as follows:

1. Convert the input rgb color image to **grayscale**
2. Reduce image noise with a **gaussian filter**
3. Apply **canny edge detection** to the image
4. Constrain the resulting binary edge image to a **region of interest** that outlines an area, where the lane markings will probably be
5. Apply a **Hough transform** for detecting a set of straight lines
6. **Extract left and right lane lines** from this set and draw them onto a blank canvas image
7. **Overlay** the original color image with the detected lane lines  



![alt text][image1]


###2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


###3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
