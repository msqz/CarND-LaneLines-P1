# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./writeup_images/1_standardized.jpg "Standardized"
[image2]: ./writeup_images/2_boosted_yellow.jpg "Boosted yellow"
[image3]: ./writeup_images/3_gray.jpg "Grayscale"
[image4]: ./writeup_images/4_boosted_contrast.jpg "Boosted contrast"
[image5]: ./writeup_images/5_blurred.jpg "Blurred"
[image6]: ./writeup_images/6_edges.jpg "Edges"
[image7]: ./writeup_images/7_region.jpg "Region"
[image8]: ./writeup_images/8_lines.jpg "Lines"
[image9]: ./writeup_images/9_weighted.jpg "Weighted"


---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I .... 

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
