
### Overview of the pipeline

The goal of the project was to superimpose straight lines over the lane markings in an image of a road using basic image processing techniques.

The pipeline I used consist of the following steps:
1. Convert the input rgb color image to **grayscale**
2. Reduce image noise with a **gaussian filter**
3. Apply **canny edge detection** to the image
4. Constrain the resulting binary edge image to a **region of interest** that outlines an area, where the lane markings will probably be
5. Apply a **Hough transform** for detecting a set of straight lines
6. **Extract left and right lane lines** from this set and draw them onto a blank canvas image
7. **Overlay** the original color image with the detected lane lines  

In order to realize steps 5 and 6 I adapted the pre-implemented draw_lines() function:
- Only straight lines with an absolute slope between 40 to 80 degrees relative to the x axis get processed further
- Lines belonging to the left/right lane markings are distinguished by the sign of their slope value
- The values for slope and position of the final left/right lane line are calculated as a weighted average over all processed lines (weight = length of a line)
- Based on these averaged slope and position values, a single straight lane line gets drawn for the left and right lane respectively


###2. Potential shortcomings of the pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


###3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
