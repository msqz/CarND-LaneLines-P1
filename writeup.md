# **Finding Lane Lines on the Road** 

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

## Reflection

### The pipeline

The pipeline contains following steps:

*(each step is illustrated with a result image)*
#### 1. Standardization 
`standardize()` - All images are resized to 960x540 px. That way the pipeline can handle also the challenge video.

![alt text][image1]

#### 2. Boosting yellows
`boost_yellow()` - It transforms the yellow parts of the image to be plain white (so they have max brightness). Thanks to that the edge detecton of the yellow line is easier, especially if it's in poor lighting (challenge video).

![alt text][image2]

#### 3. Converting to grayscale
`grayscale()` - Here the image is converted to grayscale.

![alt text][image3]


#### 4. Boosting contrast
`boost_contrast()` - A simple contrast increasing happens here. Everything above specified brightness becomes white (max brightness) and everything below gets darkened. That way the edge detection step.

![alt text][image4]

#### 5. Blurring
`gaussian_blur()` - The gradients get smoothed, so the edge detection algorithm can perform better.

![alt text][image5]

#### 6. Edges detection
`edges()` - The edges are extracted here.

![alt text][image6]

#### 7. Cropping the area
`region_of_interest()` - the image is cropped to cover only the area where lanes may be contained. There botton 100px is removed, to cut off the noise.

![alt text][image7]

#### 8. Lines detection
`lines()` - Lines are detected using Probabilistic Hough Transform. Those lines are processed by the `draw_lines()` function (described later) and new layer is created.

![alt text][image8]

#### 9. Merging lines with original image
`weighted()` - Layer containing projected lanes is applied to the standardized image.

![alt text][image9]


### The `draw_lines()` function
---
There are 3 modifications applied in the function:
1. Distinction between left and right side.

2. Calculation of the average slopes for each side.

3. Extrapolation to the top and bottom of the lane. It's done by calculating x-intercept points and drawing averaged slope from that points. The x coordinate comes from the line equation

    `y = ax + b`

    transformed to

    `x = (y - b) / a` 

### Potential shortcomings of current pipeline
---
When the dashed lane is not very dense (i.e. lines are short or there is a large distance between them), generated line might be distorted by noise.

### Posible improvements to pipeline
---

Covering more broad area (cropping wider region) could allow to detect lanes apart from the spacing between them. That would allow to use videos generated from different angles (vertical).
