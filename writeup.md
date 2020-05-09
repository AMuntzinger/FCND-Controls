# Controls Project Writeup #

This is the writeup for the C++ controls project from Flying Car Nanodegree.

## Body Rate Controller ##

The body rate controller is the first controller to be implemented, as it has the highest update frequency. 
The controller commands moments from the error between desired and actual body rates.
It also uses the given moments of inertia. The control gain for the body rate controller was parametrized in the parameter file QuadControlParams.txt.

## Roll Pitch controller ##
Next, I implemented the roll pitch controller. This controller calculates the desired body rates as input for the body rate controller. To this end, it uses the rotation matrix. 
Again, I also tuned the roll pitch gain parameter. 

## Altitude Controller ##
The altitude controller uses z-position and z-velocity errors to command a new thrust. I used a PID-controller, as it contains integral, proportional and differential parts. 

## Lateral Position Controller##
This controller calculates a desired horizontal acceleration based on desired lateral position/velocity/acceleration and current pose. Again, I chose the gain parameters appropriately.
The maximum horizontal velocity and acceleration had to be limited to the constraints of the vehicle.

## Yaw Controller ##
The yaw controller commands a yaw rate based on the yaw error times the gain parameter. A simple P-controller is sufficient here, as yaw is the least important variable.

## Motor Commands ##
Finally, I converted the calculated desired overall thrust and three moments to desired thrusts of the four propellers of the vehicle. 