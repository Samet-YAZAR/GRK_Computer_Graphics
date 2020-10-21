# Gradients
## (task for 3.5 points)
Before you start doing this task, make sure you have saved the previous task somewhere and/or open a new tab with the same page and 
copy the necessary code from the previous solution.

The goal of this task is to draw a grayscale gradient, running smoothly from left to right, start with black and ending in white.

The task is easily accomplished by assigning the value of the X coordinate as the grayscale color of the pixel. This will however work only partially. 
The gradient will work for a short time (on the left side of the image), but the whole right side will be completely white.

This is caused by the fact that the canvas is 800 pixels wide, however we only have 256 different shades of gray. 
After drawing the final white pixel (at coordinate 255), the latter colors will be clipped to the maximum allowable value of 255.
The same would be true for values below 0 (if we attempted to draw them).

To correct this problem we need to change the value being set in the color function in such a way in order to:

* if x = 0, grey shade = 0
* if x = 799, grey shade = 255
everything in between should be set proportionally (linearly) between those two limits
Computing such a value is simple:

divide the value of the x coordinate with the width variable (provided by the library) - this will gives us a value between 0 (inclusive) and 1 (exclusive)
for the different pixels running from left to right
multiply the above value by 256 (the number of shades of gray) to receive a value between 0 and 255 (both inclusive)
(task for 4 points)
After you manage to draw the above gradient, save the solution and modify it to receive a more complex color gradient, as shown below. This consists of two components:

a linear gradient going from upper left to lower right, changing the blue component from 0 (black) to 255 (maximally blue)
a circle gradient going from red in the middle to green on the outside
