Matthew Merovitz PA Line Follower

This package is a ROS node that subscribes to the image topic published by the camera sensor and attempts to follow a yellow line in the image. The code uses the OpenCV library for image processing.

When the node receives an image, it first applies a color filter to isolate the yellow color in the image. It then creates a binary mask where white pixels represent the yellow color in the image.

The node then focuses only on a 20-pixel band near the top of the image by masking out the rest of the image. It computes the centroid of the white pixels in the masked image and displays a red circle around the centroid on the original image.

If the centroid is found, the node tries to keep the centroid in the center of the image by adjusting the linear and angular velocity of the robot. If the centroid is not found, the node turns randomly until it finds the line.

The code uses a proportional control strategy to calculate the angular velocity based on the distance between the centroid and the center of the image. The linear velocity is set to a constant value of 0.2 m/s.

The code also includes some logic to handle situations where the robot loses track of the line. If the robot was already following the line before losing it, it simply turns around and continues to follow the line. Otherwise, it turns randomly until it finds the line again.

To run, run the following command:

roslaunch followerpkg follower.launch