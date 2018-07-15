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
[image2]: ./test_images_output/solidWhiteCurve.jpg    "Solid White Curve"
[image3]: ./test_images_output/solidWhiteRight.jpg    "Solid White Right"
[image4]: ./test_images_output/whiteCarLaneSwitch.jpg "White Car Lane Switch"
[image5]: ./test_images_output/solidYellowCurve.jpg   "Solid Yellow Curve"
[image6]: ./test_images_output/solidYellowCurve2.jpg  "Solid Yellow Curve2"
[image7]: ./test_images_output/solidYellowLeft.jpg    "Solid Yellow Left"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I used grayscale conversion function. Second, I applied gaussian blue to remove the noise. In the third step, I used canny edge detection. The fourth step is region of interest to focus the region to abstract lines. Lastly, hough transform is applied to get lines.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by lines
Under my presumption, there is no intensive change in the picture.

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![result1][image2]
![result2][image3]
![result3][image4]
![result4][image5]
![result5][image6]
![result6][image7]


### 2. Identify potential shortcomings with your current pipeline
This pipeline mainly three potential shortcomins.

One potential shortcoming would be what would happen when the pipeline cannot find any line by hough transform.
If such situation, the pipeline cannot interporate the line with using average function. There is no line data to be used calculate the interporation.

At seond, another shortcoming could be sensitivity to noise of the data. This pipeline is sensitive to the noise and intensive change of the line data. Then, the data

The third shortcoming is lack of robustness. This pipeline should not be applied to the third movie for challenge section. The pipeline is strongly dedicated to the first and second movie excersize.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to apply low pass filter to decrease the impact of data noise and the influence of intensive change of the line data.
This improvement requires the sequential processing

Another potential improvement could be to 
