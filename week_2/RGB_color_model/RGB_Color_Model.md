# RGB color model
## (task for grade 3)
The goal of this task is to divide the image into 3 components: R, G, and B, and draw these components as shown below:
![RGB_Color_Model](\week_2\Assets\rgb_color_model1.png)

Let us start by creating 3 additional images, for storing the 3 color channels of the original image, named: img_r, img_g and img_b. This is done using the createImage() function:

img_r=createImage(256,256);
Use this method to create the 3 variants of the image (img_r, img_g and img_b) and put the code directly below the instruction for loading of the original image.

Next step is to to resize the original image. We want to fit all 4 images into the canvas of size 512x512, as shown in the image above. Since the original image size is 512x512 pixels, we will scale it down to 256x256, using its resize() member function:

img.resize(256,256);
Place this instruction within the setup() function, after creating canvas (i.e. after createCanvas). After checking if your code works properly, remove the image instruction used to display the picture on the screen (temporarily).

In order to modify the content of an image, we need access to its pixel array. To do this, we will need 2 additional functions. The loadPixels function is used to copy the contents of the image into its pixels array. In order to modify the pixels array, loadPixels function MUST be used first! After modifying the array, the updatePixels function must be used to apply these modifications back to the original image.

The pixels array is a 1-dimensional array, consisting of 1-byte values placed one after another (documentation here):

Each group of 4 consecutive values represents 1 pixel, with values representing R,G,B and A (A for alpha, a.k.a. transparency)
Next, we have groups of width pixels (i.e. 4-element groups), where all groups together make 1 complete row of pixels
Finally, if we take height number of rows together, we form the complete image.
For Retina displays, the number of pixels in each row and the number of rows in the image is increased d times (d can be read from the pixelDensity function). Therefore, the number of pixels for Retina is d*d times the number of pixels in regular screen.

![RGB_Color_Model](\week_2\Assets\rgb_color_model2.png)

In order to iterate all the pixels in an image, the following procedure is applied:

  img.loadPixels();
  for(x=0;x<img.width;x++)
    for(y=0;y<img.height;y++) {      
      pos=4*(y*img.width+x);
      img.pixels[pos] // R value
      img.pixels[pos+1] // G value
      img.pixels[pos+2] // B value
      img.pixels[pos+3] // A value
  }
  img.updatePixels();
In the case of Retina displays, this procedure is slightly more complicated:

  img.loadPixels();
  d=pixelDensity();
  for(x=0;x<img.width;x++)
    for(y=0;y<img.height;y++)
      for(dx=0;dx<d;dx++)
        for(dy=0;dy<d;dy++) {      
          pos=4*(dy*y*img.width+dx*x);
          img.pixels[pos] // R value
          img.pixels[pos+1] // G value
          img.pixels[pos+2] // B value
          img.pixels[pos+3] // A value
        }
  img.updatePixels();
Another way of making this work on Retina display is to simply deactivate the Retina functionality by setting the pixelDensity to 1:

pixelDensity(1);
Copy R, G and B values to the appropriate channels of the img_r, img_g and img_b. Do not forget to set alpha for each pixel to 255! By default, the entire picture is set to 0, which would make it completely transparent. Also, note that you can set all the pixels in all images in a single loop.

After filling the images with appropriate pixel values, run updatePixels() outside the loop, in order to update all the images (i.e. use this method for each individual image).

Finally, draw all images on canvas, using the image function. The image containing the R component (img_r) should be placed at (0,0), G at (256,0), and B at (0,256).

The fourth image should look like the original, but in order to show how the RGB model works, we will create a new image that will be the sum of the 3 components. In the preload() function, create another image called img_sum. At the end of the setup method do 3 summation operations using the blend() method:

 img_sum.blend(img_r,0,0,256,256,0,0,256,256,ADD);
Add all 3 components to the img_sum image and draw it at (256,256).
