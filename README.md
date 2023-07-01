# Video-stabilization
This GitHub repository offers a video stabilization solution using template matching algorithms. It includes code for identifying correspondences between frames and applying stabilization techniques to reduce motion artifacts, resulting in smoother and more stable videos.

# Template Matching
Template-based methods for video stabilization rely on tracking a fixed template or patch of pixels within the video frames. The template can be a specific image feature, such as an object or a region of interest, or a fixed-size patch selected from the video frame. The method tracks the movement of the template or patch across frames and uses this information to estimate the camera motion between frames. The camera motion is then compensated by transforming the frames to align them with a reference frame.

Template-based methods have the advantage of being computationally efficient and robust to changes in scene content. However, they may struggle with scenes that contain a lot of motion or changes in the template over time. They may also require careful selection and initialization of the template or patch to be tracked.


# Methodology

The algorithm used in this implementation is a simple template-based method, where a small template is defined in the first frame of the video, and its position is tracked in subsequent frames. The camera motion is estimated by calculating the motion vector between the current frame and the previous frame, and this motion is used to shift the current frame in the opposite direction, essentially stabilizing the video.

The code begins by reading in the input video file and defining a few parameters, such as the size and location of the template and the search region. The 
template is defined as a small rectangle in the first frame of the video, and its position is tracked in subsequent frames. The search region is defined as an area around the template where the algorithm searches for the template in the current frame.

The algorithm then enters a loop where it reads in each frame of the video, and for each frame, it performs the following steps:

1. It finds the location of the template in the current frame by using the template matcher function. The template matcher function takes as input the current frame, the template, and the search region, and outputs the position of the best match for the template in the current frame.
2. It calculates the motion vector between the current frame and the previous frame by subtracting the position of the template in the previous frame from the position of the template in the current frame.
3. It updates the search region based on the estimated motion vector, so that the search region is centered around the predicted location of the template in the next frame.
4. It shifts the current frame in the opposite direction of the estimated motion vector, using the imtranslate function, to stabilize the video.
5. It saves the stabilized frame to an output video file and displays the original and stabilized frames side by side.
   
The process is repeated for each frame in the video, resulting in a stabilized video file.
![image](https://github.com/prnvrain/Video-stabilization/assets/133137164/8a39b7ef-6308-4640-9a01-215e0f041040)

It is important to carefully tune the parameters to achieve optimal results for a specific video stabilization application. Experimentation with different 
parameter values and thorough testing on sample videos can help identify the optimal parameter values for a given use case.

