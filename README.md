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
|<img width="300" alt="x gradient" src="xgrad.jpg"> |  <img width="300" alt="y graident" src="ygrad.jpg"> |

I then computed the gradient magnitude image through np.sqrt(xgrad² + ygrad²) and subsequently normalizing it. To compute the edge image, I binarized the gradient magnitude image, using a threshold of 0.25.

| Combined Gradient Magnitude | Binarized Edge Image | 
|:-------------------------:|:-------------------------:|
|<img width="300" alt="x gradient" src="gradient.jpg">  |  <img width="300" alt="y graident" src="edge.jpg"> |

### Derivative of Gaussian (DoG) Filter:

## Approach 1: Blurring the Image First

Although convolving with our finite difference operators gets us the correct edge images, it picks up a lot of noise. Using Gaussian filters, we can smooth out these previous results!
I first created a 2D Gaussian kernel using an outer product of two 1D Gaussian filters, using cv2.getGaussianKernel() with a kernel size of 10 and sigma of 2. Convolving the original image with this 2D Gaussian kernel produces a blurrier image, preserving the general shape and structure of the iamge, but just making the edges softer.
<img height="300" alt="blurrier " src="blurred.jpg">

I then repeated similar steps as the previous part with the blurred image, convolving the blurred image with the X and Y finite difference operators.

| Blurred X Partial Derivative | Blurred Y Partial Derivative | 
|:-------------------------:|:-------------------------:|
|<img width="300" alt="blurred x gradient" src="blurredxg.jpg">  |  <img width="300" alt="blurred y gradient" src="blurredyg.jpg"> |

Using the same procedure, we compute the gradient magnitude of this blurred image and subsequently binarized the gradient magnitude image (with a threshold of 0.2) to get the blurred edge image. Compared to the non-blurred image, we can see that both the blurred gradient magnitude image and blurred edge image have much thicker but smoother outlines around the edges. Both these resulting images have less noise compared to the results from the non-blurred images, especially at the bottom of the image, where the grainy noise from the original binarized edge image are completely absent in the blurred binarized edge image.

| Combined Blurred Gradient Magnitude | Binarized Edge Image| 
|:-------------------------:|:-------------------------:|
|<img width="300" alt="blurred gradient" src="blurred_gradient.jpg">  |  <img width="300" alt="blurred edge" src="blur_edge.jpg"> |

## Approach 2: DoGx and DoGy

As an alternative approach, instead of first blurring the image with the 2D Gaussian filter and then convolving with the D_x and D_y finite difference operators, we can convolve the 2D Gaussian filter with the D_x and D_y finite difference operators to get the DoG_x and DoG_y, and convolve these with the original image. I then followed the same steps as the above approach to calculate and show the gradient magnitude image as well as the blurred binarized edge image (with the same threshold as the above approach - 0.2), which are identical to the results from the previous approach.

| DoG_x (D_x of 2D Gaussian) | DoG_y (D_y of 2D Gaussian) | 
|:-------------------------:|:-------------------------:|
|<img width="300" alt="gaussian x filter" src="dx_gauss.jpg">  |  <img width="300" alt="gaussian y filter" src="dy_gauss.jpg"> |

| Blurred X Partial Derivative | Blurred Y Partial Derivative | 
|:-------------------------:|:-------------------------:|
|<img width="300" alt="blurred x gradient approach 2" src="dx_gaussim.jpg">  |  <img width="300" alt="blurred y gradient approach 2" src="dy_gaussim.jpg"> |

| Combined Blurred Gradient Magnitude | Binarized Edge Image| 
|:-------------------------:|:-------------------------:|
|<img width="300" alt="blurred gradient approach 2" src="blurred_gauss.jpg">  |  <img width="300" alt="blurred edge approach 2" src="blur_edge2.jpg"> |

### Image "Sharpening"!

# Taj Mahal 

We can further use the low-pass Gaussian filter to sharpen blurry images! Given an image, I separated it into the three separate color channels, and then blurred each channel by convolving it with a 2D Gaussian filter. To extract the "details" of the image, I then subtracted each blurred channel by the channel. 

| Blurred Taj Mahal | High Frequency Details of Taj Mahal | 
|:-------------------------:|:-------------------------:|
|<img width="300" alt="blurred taj mahal" src="blurred_taj.jpg">  |  <img width="300" alt="taj mahal details" src="details.jpg"> |

The sharpened image was thus the original channel + the details * alpha. I used alpha = 1.5 to get this sharpened version of the Taj Mahal image.

| Original Taj Mahal | Sharpened Taj Mahal | 
|:-------------------------:|:-------------------------:|
|<img width="300" alt="blurred taj mahal" src="taj.jpg">  |  <img width="300" alt="taj mahal details" src="taj_sharp.jpg"> |

I tried this sharpening technique on several other images!

### Hybrid Images



