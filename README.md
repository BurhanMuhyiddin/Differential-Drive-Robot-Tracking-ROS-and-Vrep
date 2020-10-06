# Differential Drive Robot Object Tracking
The purpose of the project is to simulate "Pioneer" dd robot in Coppeliasim(Vrep) that can track a specified object based on its color. The project has been implemented in Python programming language. The information exchange between Coppeliasim and Python has been established through "remote API". The information exchange between Python codes has been done by impleneting ROS.

# Running the program
This is very simple to run the program
1. Open the Coppeliasim (Vrep) scene in vrep and start the simulation. The file is under the path of (your catkin workspace)//src/dd_robot_image_processing/coppeliasimFile
2. Launch the "start_project.launch". This will launch the needed two nodes
3. Now yo can turn to the simulation environment and try to change the position of the object and you will see that the robot will start to track it

# Some information about the project
Some more information about the project

## Camera frame acquisition and processing
The frames are acquired from the vision sensor that has been added to the Pioneer robot through remote API. After the frames have been obtained (HSV) color detection has been applied to them and the contour of the object has been drawn. After finding contour, the center of the object has been calculated and the its difference with the center of the window has been calculated. All of these operations done using OpenCV. And finally, this difference is published to the /center topic.

## Driving robot
On the subscriber node which has been subscribed to the /center topic, the robot's kinematics has been calculated based on the obtained information. Additionally the distance between the robot and the object is calculated and the robot stops when it reaches to the predifined distance to the object.

# Some additions and improvements that should be done
While this simulation has been done successfully it doesn't represent the real environment. As there is noise in the camera in real environment. So, some additional processings should be done to the frames obtained. Additionally the control of th robot for tracking the object is not quite stable as it jerks when tracking object. This can be eliminated using D controller in the project.

# Author
Burhan Muhyiddin
