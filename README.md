# Sudoku Solver

This is a project based on Computer Vision to solve a sudoku given in an image effeciently. 

This is the sample image used for this project:   
![Sample Image](/images/sud3.jpeg)

## Part 1: Isolating the Sudoku

This was done using various OpenCV Image Processing Algorithms. 

I first converted the image to Grayscale and applied Gaussian Blur on it. The image was then thresholded to convert it into a binary image(simply black or white).    
I then found the contours of the image (lines joining points having same intensity). The largest 4 sided contour gives us the boundaries of our Sudoku!   
The image was then cropped using the corners of the images using ```getPerspectiveTransform``` method of OpenCV.

The isolated sudoku looked like this:   
![Isolated](/images/isolated_sud.png) 

## Part 2 : Recognizing the digits

The isolated sudoku was divided into 81 individual squares. If majority of the pixel values of a square were greater than a specific amount, the square was declared empty.

To recognize the digits in non-empty squares, I trained a CNN model in Keras on the MNIST Dataset for digit recognition.   
Accuracy of the model: ```98.47``` percent on the test dataset. 
   
![Model](/images/model.jpg)

This model was run on the blocks to recognize the digits. Any error in recognizing due to non 100% accuracy was removed manually 

## Part 3: Solving the Sudoku

This was done using an efficient backtracking algorithm in Python.

The final solved sudoku looked this this:    
![Solved](/images/solved.jpg)
