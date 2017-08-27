# CarND-Vehicle-Detection

Provide a Writeup / README that includes all the rubric points and how you addressed each one. You can submit your writeup as markdown or pdf. 

# [Rubric 1] Histogram of Oriented Gradients (HOG)

1.1 Explain how (and identify where in your code) you extracted HOG features from the training images. Explain how you settled on your final choice of HOG parameters.
>> Code is in cell [9] & [17]
HOG parameters
* color_space = 'RGB' 
* orient = 9 HOG orientations
* pix_per_cell = 8 HOG pixels per cell (Rationale: achieve better fidelity)                                    
* cell_per_block = 2 HOG cells per block (Rationale: greater fidelity)
* hog_channel =  "ALL"  (Rationale: achieve better accuracy)
* spatial_size = (32,32)  (Rationale: achieve better accuracy)
* hist_bins = 32    # Number of histogram bins

1.2 Describe how (and identify where in your code) you trained a classifier using your selected HOG features (and color features if you used them).
>> Code is in cell [19]

* 92.302570104599 Seconds to complete features...
* Using: 9 orientations 8 pixels per cell and 2 cells per block
* Feature vector length: 8460
* 34.27 Seconds to train SVC...
* Test Accuracy of SVC =  0.9924

# [Rubric 2] Sliding Window Search

2.1 Describe how (and identify where in your code) you implemented a sliding window search. How did you decide what scales to search and how much to overlap windows?
>> Code is in cells [5] & [12]
* Step 1: I set the start and stop positions using the image dimensions
* Step 2: I calculated the number of sliding windows
* Step 3: I loop through to find x and y window positions
* Step 4: I created a list of window positions
* Step 5: I created an empty list to receive positive detection windows
* Step 6: I extract the test window from the original image
* Step 7: I extract features from respective window
* Step 8: I scaled and fed the features into the classifier
* Step 9: I ran a prediction using classifier
* Step 10: I returned a list of positive window detections

2.2 Show some examples of test images to demonstrate how your pipeline is working. How did you optimize the performance of your classifier?
* See python notebook for images
* Classifer performance was optimized by adjusting the region of interest to a narrower 'y-span'.  I also adjusted the overlap to 0.5.

# [Rubric 3] Video Implementation

3.1 Provide a link to your final video output. Your pipeline should perform reasonably well on the entire project video (somewhat wobbly or unstable bounding boxes are ok as long as you are identifying the vehicles most of the time with minimal false positives.)

Output video named 'project_video_output.mp4'

3.2 Describe how (and identify where in your code) you implemented some kind of filter for false positives and some method for combining overlapping bounding boxes.
>> Code is in cell [23] & [26]
* I implemented a thresholded Heatmap filter to and layered 5 heatmaps to to filter false positives.

# [Rubric 4] Discussion

4.1 Briefly discuss any problems / issues you faced in your implementation of this project. Where will your pipeline likely fail? What could you do to make it more robust?
* Issues related to this project stem from defining the function for sliding windows. I got stuck when defining the size of the windows to extract. This took some time to debug.
* Other issues came from trial and error R&D using different classifiers functions.
* Pipeline will likely fail in low light conditions, driving through tunnels
