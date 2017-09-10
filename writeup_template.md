# **Finding Lane Lines on the Road** 

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

[can_image1]: ./output_images_can/solidWhiteCurve.jpg "solidWhiteCurve"
[can_image2]: ./output_images_can/solidWhiteRight.jpg "solidWhiteRight"
[can_image3]: ./output_images_can/solidYellowCurve.jpg "solidYellowCurve"
[can_image4]: ./output_images_can/solidYellowCurve2.jpg "solidYellowCurve2"
[can_image5]: ./output_images_can/solidYellowLeft.jpg "solidYellowLeft"
[can_image6]: ./output_images_can/whiteCarLaneSwitch.jpg "whiteCarLaneSwitch"

[reg_image1]: ./output_images_reg/solidWhiteCurve.jpg "solidWhiteCurve"
[reg_image2]: ./output_images_reg/solidWhiteRight.jpg "solidWhiteRight"
[reg_image3]: ./output_images_reg/solidYellowCurve.jpg "solidYellowCurve"
[reg_image4]: ./output_images_reg/solidYellowCurve2.jpg "solidYellowCurve2"
[reg_image5]: ./output_images_reg/solidYellowLeft.jpg "solidYellowLeft"
[reg_image6]: ./output_images_reg/whiteCarLaneSwitch.jpg "whiteCarLaneSwitch"

[fin_image1]: ./output_images_fin/solidWhiteCurve.jpg "solidWhiteCurve"
[fin_image2]: ./output_images_fin/solidWhiteRight.jpg "solidWhiteRight"
[fin_image3]: ./output_images_fin/solidYellowCurve.jpg "solidYellowCurve"
[fin_image4]: ./output_images_fin/solidYellowCurve2.jpg "solidYellowCurve2"
[fin_image5]: ./output_images_fin/solidYellowLeft.jpg "solidYellowLeft"
[fin_image6]: ./output_images_fin/whiteCarLaneSwitch.jpg "whiteCarLaneSwitch"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of below steps. 

  1. Convert the images to grayscale.
  2. Apply Gaussian filter to blur the image. I used the kernel size of 5
  3. Apply Canny edge detection filter to the blurred image. I used the 40 and 120 as the parameter with some trial and error.
  4. Applied filter to select edges only in the interested region.
  5. Applied hough transform to connect the edges pixels to get lines. I played with lot of different parameter options and each of them gave different results. I finally settled on the 3, 15, 5 values.
  6. Finally I super imposed the lines on the original image using the provided utility method weighted_img.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...

The images after canny edge detection are as below.
![alt text][can_image1]
![alt text][can_image2]
![alt text][can_image3]
![alt text][can_image4]
![alt text][can_image5]

The images after applying region of interest filter are as below.
![alt text][reg_image1]
![alt text][reg_image2]
![alt text][reg_image3]
![alt text][reg_image4]
![alt text][reg_image5]


The images after superimposing the hough transformed lines on original image are as below.
![alt text][fin_image1]
![alt text][fin_image2]
![alt text][fin_image3]
![alt text][fin_image4]
![alt text][fin_image5]



### 2. Identify potential shortcomings with your current pipeline

I see following shortcomings in this basic implementation.

1. It is not working for the third video. When I debugged I found that it doesn't seem to handle the shadows, different lighting conditions and also other edges on the side of the road.
2. It probably won't handle curved roads well.
3. It might have issues when there is downhill/uphill roads.
4. If there are vehicles infront the car or in the adjacent lane.

### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...
1. I think it might be worth to fitler the image with yellow and white color to detect the lines.
2. Handle curved roads
3. Detect other vehicles on the road and ignore their edges. Color filter might solve to some extent but there could be white and yellow colored vehicles as well.

