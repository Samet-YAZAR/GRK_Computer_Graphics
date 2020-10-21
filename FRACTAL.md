# GRK_Computer_Graphics
This repository includes tasks and solutions for GRK (Computer Graphics)course 

##Fractal
###(task for 5 points)
The iterative algorithm giving the above solution is as follows:

1. define 3 points (pairs of x and y coordinates) to represent the tips (corners) of the triangle - you can initialize them in the setup function
2. start by erasing the screen to black at the start of the draw function
3. set the three pixels, defined by the coordinates in point 1, as white
4. define a new pair of coordinates (eg. called cx and cy) to represent the current point and set them to the value of the first pair of points (eg. x1 and y1)
5. using a for loop, repeat the following for cca. 30000 iterations (you can debug using a lower value, but the above image used 30k points)
  * generate a random value from 0..3 and round it down (using floor) to a whole number:
  * use switch to check the 3 conditions:
      - if the random value is 0:
           - set cx to the half-way point with cx and x1: cx=(cx+x1)/2;
           - do the same for cy i y1
           - paint the pixel cx,cy as white
     - if the random value is 1:
           - do the same as the above but between cx i x2 and cy i y2
     - in all other cases (default):
           - do the same as the above but between cx i x3 and cy i y3
           
The above algorithm generates an image of the Sierpinski's triangle between and 3 points on the screen in an iterative manner. The more iteration you use to run the algorithm, the better the final result. The algorithm works because the mathematical definition of the Sierpinski's triangle fractal says that any point belonging to the set is exactly on the midpoint of a line connecting a corner of the triangle and some other point belonging to this set.

If you want, you can try and animate the above image by changing the location of the triangle corners in every frame of the animation. You also need to change the noLoop() command in the setup function to a frameRate(25) command. Then you can change the corner coordinates (x1/y1, x2/y2, x3/y3) by adding some random vectors (dx1/dy1, dx2/dy2, dx3/dy3) to them at the start of the draw function. You can also implement bouncing of the corners by inverting these vectors if the value if the corner pixel leaves the canvas area (as in a simple bouncing ball animation). This animation will probably not run very smoothly. This is because instead of using the set command, we should be directly manipulating the pixels array, as described on this page.
![fractal](/Assets/fractal.png)
