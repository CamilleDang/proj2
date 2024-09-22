## Project 2: Fun with Filters and Frequencies! :) 

*Follow along with the code here: 

### Overview
This

###  Finite Difference Operator

We begin with this original image of a cameraman.

<img height="300" alt="cameraman og" src="cameraman.png">

I then defined two finite difference operators D_x and D_y, which I simply made with an np.array of [1, -1] respectively reshaped to a 1 x 2 matrix and 2 x 1 matrix, and convolved the original image with each of the operators (using scipy.signal.convolve2d) to get the x and y partial derivatives of the cameraman image. 

| X Partial Derivative | Y Partial Derivative | 
|:-------------------------:|:-------------------------:|
|<img width="500" alt="x gradient" src="xgrad.jpg"> |  <img width="500" alt="y graident" src="ygrad.jpg"> |

I then computed the gradient magnitude image through np.sqrt(xgrad ** 2 + ygrad ** 2) and subsequently normalizing it.

<img height="300" alt="combined gradient" src="gradient.jpg">

To compute the edge image, I binarized the gradient magnitude image, using a threshold of 0.25.

<img height="300" alt="binarized edge" src="edge.jpg">

### Derivative of Gaussian (DoG) Filter:
Hi
