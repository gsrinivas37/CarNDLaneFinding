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

My pipeline consisted of below steps. 

  1. Convert the images to grayscale.
  2. Apply Gaussian filter to blur the image. I used the kernel size of 5
  3. Apply Canny edge detection filter to the blurred image. I used the 40 and 120 as the parameter with some trial and error.
  4. Applied filter to select edges only in the interested region.
  5. Applied hough transform to connect the edges pixels to get lines. I played with lot of different parameter options and each of them gave different results. I finally settled on the 3, 15, 5 values.
  6. Finally I super imposed the lines on the original image using the provided utility method weighted_img.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
