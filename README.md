# Final_Assignment

Inside Final_assignment you will find: 
-rqt_graph of the simulation 
-CMakeList.txt is the best and user friendly software solution to build c++ project. 
-package.xml is the Package Manifest of the ros package. 
-script folder with python source code :
        laser scann SLAM for localisation and mapping. 
        Move_Base for move the Robot in the sourroundind environment -
-src folder with c++ file of the two nodes:
                  1) Goal_server.cpp that provide a random target betweeen the possibles coordinates: X_COORDINATES:[-4,-4,-4, 5, 5,5]
                                                                                                      Y_COORDINATES:[-3, 2, 7,-7,-3,1]
                  2) Interface.cpp ,a simply user interface ,that provide the four possible functions.

-srv folder with the request/reply of the custom service 
-config folder for rviz configuration 
-param folder for the configuration of the sourrounding enviroment 
-urdf folder (Universal Robotic Description Format) with the descriptions of the robot and sensors 
-wordls folder with the description of the house in which the simulation will run 
-docs folder with the documentation builded with DoxyGen and ReadMe.txt file 
-launch folder with the XML launch file for the simulation

Robot uses lasers to scanning the area and for seeing obstacles. Robot uses SLAM ( Simultaneous Localization and Mapping) in particular Gmapping, which is based on a particle filter (approach to estimate a probability density). Robot uses Dijkstra algorithm to move in the sourrounding environment. With simulation_gmapping.launch Rviz and Gazebo simulators will be executed. With move_base.launch dijkstra algorithm will be executed.

I develop (/src/interface.cpp) that allow to choose one of four possiible actions: 1)Choose randomly one of six possible target and Robot has to reach the goal. A custom service has been declared (srv/Random_Goal.srv) and one server to choose randomomly the goal has been implemented(/src/goal_service.cpp) 2)User has to set x and y coordinates for the goal (but one of the possible six) 3)Start to follow the walls. For this scope exists (/scripts/wall_follow_service_m.py) 4)Stop the Robot in the current position.


To launch the node digit the command:
1) roslaunch final_assignment my_launch_file1.launch that launch the simulators ---> Gazebo and Rviz , the Gmapping Algorithm to estalibish the correct position of the Robot
         This launch file execute also the Djikstra Algorithm to estailish the shortest path to reach the target and Slam_Gmapping passing the correct Ros Parameters
2) roslaunch final_assignment my_launch_file2.launch that executes the two nodes in C++ --> :goal_server and interface 



