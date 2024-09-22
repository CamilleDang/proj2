## Project 2: Fun with Filters and Frequencies! :) 

*Follow along with the code here: 

### Overview
This

###  Finite Difference Operator

We begin with this original image of a cameraman.

<img height="300" alt="cameraman og" src="cameraman.png">

I then defined two finite difference operators D_x and D_y, which I simply made with an np.array of [1, -1] respectively reshaped to a 1 x 2 matrix and 2 x 1 matrix, and convolved the original image with each of the operators to get the x and y partial derivatives of the cameraman image.



### Further Improvements:
After the naive implementation, I also implemented a crop function that takes in an image and a percentage, and returns the image after cropping that percentage of the image. I 
I then applied this function to each of the R, G, and B images, cropping each image by around 15% to get rid of borders that made channel alignment less accurate.
I also implemented the NCC align function and added the option to add various loss functions in the align function, but ended up preferring and using the Euclidean norm for the rest of my images.
