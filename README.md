# Finding lane lines in images


### Overview of the pipeline

The goal of the project was to superimpose straight lines over lane markings in an image of a road using basic image processing techniques.

The pipeline used consist of the following steps:

1. **Convert** the input rgb color image **to grayscale**
2. Reduce image noise with a **gaussian filter**
3. Apply **canny edge detection** to the image
4. Constrain the resulting binary edge image to a **region of interest** that outlines an area where the lane markings will probably be
5. Apply a **Hough transform** for detecting a set of straight lines
6. **Extract left and right lane lines** from this set and draw them onto a blank canvas image
7. **Overlay** the original color image with the resulting lane line image 

In order to realize steps 5 and 6 I adapted the pre-implemented draw_lines() function:

- Only straight lines with an absolute slope between 20 and 80 degrees relative to the x-axis get processed further
- Lines belonging to the left/right lane markings are distinguished by the sign of their slope value
- The values for slope and position of the final left/right lane line are calculated as a weighted average over all processed lines (weight = length of a line)
- Based on these averaged slope and position values, a single straight lane line gets drawn for the left and right lane markings respectively


### Potential shortcomings of the pipeline

A problem of the current pipeline is the heavy dependence on a hardcoded region of interest (ROI):
- Lanes outside of the ROI never get detected. Therefore if the vehicle exhibits a significant yaw angle relative to the course of the lane (e.g. during a fast lane change) the detection of lanes may not be possible.
- As we assume that all edges inside the ROI belong to lane markings, other structures (e.g. another car driving in front of the ego vehicle) might wrongly get detected as lanes too.

While applying the pipeline to the "challenge" video, I noticed that if the real lane is not a straight line, the current approach gives only a very rough estimate of the real course of the lane.

Another thing I noticed while watching the videos is that the lane lines often appear jittery and not very stable.

It's also a challenge to choose parameter values (e.g. for the canny edge detection or the Hough transform) that work in all lighting conditions. That's why the pipeline sometimes does not identify lanes in the "challenge" video (see [extra.mp4](../extra.mp4)).


### Possible improvements to the pipeline

To improve the stability of lane tracking in videos, the values for slope and position of a lane line could be filtered over time (e.g. lowpass filter).

For better representing the real course of the lane, a polynomial (e.g. parabola) could be used instead of a straight line. 

If information about the movement of the vehicle is available, a possible improvement to the pipeline could also be to adapt the region of interest according to the rotation of the vehicle.


