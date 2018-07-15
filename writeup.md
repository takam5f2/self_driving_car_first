# **Finding Lane Lines on the Road** 

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

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by getting lines function expressed by "y = ax + b"
First processing is to classify lines into right lines and left lines. Then, I used slope to do so. The threshold value "0.5" is introduced because absolute value of slope for lines tend to be more than 0.5.
Second processing is to get line which can be expressed by function of "y = ax + b". This function is obtained with 2 steps. First step is to calculate average of both starting position and ending position of lines obtained by hough transform. Second step is to get coefficients of slope "a" and offset "b" used in the function "y = ax + b". To get slope "a" and offset "b", I find the function which can pass both the average starting position and ending position.
After getting the function expressed "y = ax + b", I calculated starting position and ending position interported line.

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![result1][image2] ![result2][image3] ![result3][image4]
![result4][image5] ![result5][image6] ![result6][image7]

### 2. Identify potential shortcomings with your current pipeline
This pipeline mainly three potential shortcomins.

One potential shortcoming would be what would happen when the pipeline cannot find any line by hough transform.
If such situation, the pipeline cannot interporate the line with using average function. There is no line data to be used calculate the interporation. In this situation, any interporated line cannot appear.

At seond, another shortcoming could be sensitivity to noise of the data. This pipeline is sensitive to the noise and intensive change of the line data. I used average function for getting the interporated line. If there is much noise, average position will be influenced by such noise and interporated line will not be appropriate one.

The third shortcoming is lack of robustness. This pipeline should not be applied to the third movie for challenge section. The pipeline is strongly overfitted to the first and second movie excersize. 


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to apply low pass filter to decrease the impact of data noise and the influence of intensive change of the line data.
This improvement requires to store data of the previous frame. Using data of previous frame, the pipeline has resistence to the noise and intensive change.

Second potential improvement could be to use another algorithm instead of average. In my implementation, average function can be influenced by noise strongly. Average function works under resumption that there is less noise and intensive change.
I found the tendancy that absolute value for slope of the straight line is more than 0.5 in the picture. As well as such activity, I should have analyze the tendancy of the lines to detect this accurately.

Last potential improvement could be to analyze pipeline design more carefully. I decided each tuning parameters with observation of the images. So that, my pipeline is overfitted to certain problems, but my pipeline cannot work well when it is applied another challenge such as the 3rd movie. I can improve this one for using many types of problems. I will find more sophisticated pipeline after applying it to another problem and modifying it. 
