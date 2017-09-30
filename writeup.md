### REFLECTION

####  1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.
Steps involved in pipeline were straightforward, as shown in the lesson:
    - convert to grayscale
    - apply canny transform
    - mask image to analyze area of interest only
    - transform lines into points in hough space
    - divide the lines into left/right, based on slope - used an inuitive approach to calculate which doesn't yield 100% accuracy, but is very fast.
    - draw the lines on image, with slope and intercept

####  2. Identify potential shortcomings with your current pipeline
The existing approach doesn't address below concerns:
    - lane lines missing OR hidden due to other vehicles
    - the slope based approach can sometimes lead to some inaccurate results - in which case a marked line flashes where there is no lane line  
####  3. Suggest possible improvements to your pipeline
Ideas
    - each image is currently identified individually. Extending results of one image to the next few (example - forward moving average) might improve accuracy of analysis.
    - occasional errors can also be reduced by above method.

### Thoughts (Writeup and Submission)

######  There is lot of jitter on the marked lines -
Though the solution is capable of identifying lane lines, it's not perfectly smooth. Making it perfectly smooth is surely possible, but would be very time-consuming.

######  Selection of area of interest is manual -
Depending on image size/resolution and orientation of road. So the algos developed could fail with different sample. Reducing that error would require a neural network doing this work by itself, using lot of sample data.

######  Tunable params -
Program/Algorithms developed contain severable tunable parameters such as rho, theta, etc. which require tuning that is time consuming. These could fail on sample data that has different characteristics then the data, based on which the params are configured.

######  Not all roads have lanes -
Roads in developing countries, such as India and its neighbours often have roads without lanes, especially inside the cities, and this obviously can't serve as a starting point for developing sdc's in such places. Those would need different approach. Food for thought, atleast for me.

*The course got me introduced to image processing in general and opencv, which is awesome. Learned a lot, had fun.*
