# Painting
## (Task for 4.5 points)

For this task, reproduce the image below by manipulating pixels on the screen. You can use only the methods described above and the random function
![painting](/Assets/painting.png)

Tips
* make sure to draw everything in the right order - suggested order is:
  1. sky (may be set as background color)
  2. grass
  3. flowers
  4. walls
  5. roof
* flowers on the grass are simply 1000 pixels with random X/Y coordinates and random color
* to generate a random value, for example, between 10 and 20, you can use this function:
random(10,20);
* make sure to round the value before using is as a coordinate, or it won't work correctly:
floor(random(10,20));
* the roof is probably the most complex thing to draw - keep in mind you can use more than one variable in a single loop:
for(y=50,w=0; y<200; y++,w+=2)
* the image doesn't have to match 100% - small changes in sizes and colors are allowed
