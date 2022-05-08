#  Research track 2, assignment on Jupyter Notebook

## Description of the assignment
The idea of this assignment is to integrate a simple GUI to the core structure of the Research track 1 final assignment.  
The implementation of the GUI is done with Jupyter Notebook in ipython.  
The GUI also shows some dynamic plot representing important information about the robot motion.


 
## How to run the code
Remember to check if the .py files are executable.  
From a linux shell launch as first the environment and the mapping nodes:
```
roslaunch final_assignment simulation_gmapping.launch
```
```
roslaunch final_assignment move_base.launch
```
Then launch all the nodes that allows the jupyter GUI to interact with the robot environment:
```
roslaunch a3_code jupy_launcher.launch
```

Now from jupyter Notebook run the GUI program
```
User_interface.ipynb
```
Run all the cells. The interface will be shown as the output of the last cell in the file.

## Functionality of the interface

As first the interface allows the user to select between **autonomous navigation** and **manual driving**.  In the first case a second interface allows the user to insert the x and y coordinate to reach. Pressing the **start** button the robot will start moving.  
If the robot reaches the target or after a time out the interface will return a message and become again active for another operation.  
Back to the main menu, the second button allows the user to directly control the robot. A dedicated interface with a button for each direction and a checkbox for activating or deactivating the collision avoidance control will allow the user to directly control the robot.

## Contents of the map and graph

Below the main menu three graphs will be displayed.  The first one contains the actual position (x,y) coordinate of the robot. It is updated live and it keeps track of the trajectory of the robot.  The second graph, is a polar plot and shows the obstacle around the robot as seen from the laserScan sensor on board of the robot.  The third graph (initially empty) keeps track of the numbers of reached or not reached targets by the robot in the autonomous navigation mode.  
Only in case of manual control an additional figure will appear, showing a live 3D map of the environment around the robot. The map will auto-update while the robot moves in the environment.



## All that glitters is not gold

Some problems are related to the GUI provided by jupyter Notebook, The main problem is the extremely high reaction time of the interface, both when pressing a button and in the update of the plots.  From a practical point of view the reach coordinate task sends the action for reaching the target but the robot struggles to move. This cause the robot to fail in reaching the target nearly always. A second problem related to the high response time is the difficulty in manually driving the robot due to the lag between the instant in which you press a button and the instant in which the robot starts/stops moving in the 3D map.  Delay problems are also present in the live update of all the three plots where the update is not smooth but rather it is very discontinuous.   Note that all this problem (of course not the ones related to the plots) were not present in the non graphical UI implemented for the final assignment of RT1, where the overall environment was the same.


