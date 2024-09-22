## Project 2: Fun with Filters and Frequencies! :) 

*Follow along with the code here: 

### Overview
This

### Example of the input image from the Prokudin-Gorskii photo collection:

<img height="500" alt="cathedral jpg" src="cathedral.jpg">

### Naive Approach
I first started by taking each image (which has the 'red', 'green', and 'blue' filtered images stacked upon each other, as shown above) and extracting the three separate images. Then, I created an align function that takes in two images, and returns the best x and y offset that minimizes a loss between the first image's pixels and the second image's pixels within an a given window. By exhaustively searching for image1's x and y offset that minimizes the loss, the function will find the closest similarity between the two images as possible. I used the Euclidean distance as my loss function and searched over window sizes of [-15, 15] to find the x and y offset that returned the lowest Euclidean distance between the pixels of the first and second image.

Once the offset is found, we adjust the image accordingly: I adjusted the image in the align_final function after finding the optimal offset.
I effectively used this method for all three jpg files), using the **blue** channel as the base for all three.

### Further Improvements:
After the naive implementation, I also implemented a crop function that takes in an image and a percentage, and returns the image after cropping that percentage of the image. I 
I then applied this function to each of the R, G, and B images, cropping each image by around 15% to get rid of borders that made channel alignment less accurate.
I also implemented the NCC align function and added the option to add various loss functions in the align function, but ended up preferring and using the Euclidean norm for the rest of my images.
