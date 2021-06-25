# Turtlebot3 with SLAM
Steps of How to Use Turtlebot3 with SLAM approach to create and save a map :

Because am using mac I had a trouble when am tiring to download Ros and Ros packages so I use her the Ros Development studio ( http://rosds.online/ ) 

This is the three sources that I use to Turtlebot3 with SLAM approach to create and save a map all of them in github :
1)	https://github.com/ROBOTIS-GIT/turtlebot3.git
2)	https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git
3)	https://github.com/ROBOTIS-GIT/turtlebot3_msgs.git

the first thing that I did is to upload this files I upload file 1 and 3 in   $ catkin_ws/src/ and file 2 in $ simulation_ws/src/  and I compile the $ catkin_ws/ by ``` $ catkin_make ``` and I do the same for $ simulation_ws/ by ``` $ catkin_make ```

so first we going to specify what turtlebot3 model we are using in the simulation_ws file hit ``` $ export TURTLEBOT3_MODEL=burger```  so now that we did that we can actually launch our simulation so we are going to type ``` $ roslaunch turtlebot3_gazebo turtlebot3_world.launch```  now it’s launching the simulation so it’s waiting for the services and in order for us to see it we goanna open gazebo and this is it this is the simulation 

![image](https://user-images.githubusercontent.com/86170422/123352331-bf22aa80-d567-11eb-8f5a-1f5f69ec2774.png)

Now that we have this we can go ahead and launch the slam node and (be caurful of launching file that is use to launch the slam node but it’s already publishing a (robot_state_publisher) so if you have one in the background that you were using it for other things it might five you an error so we’re gonna launch that so we’re gonna type in a new shell we’re gonna specify the robot model against    ``` $ export TURTLEBOT3_MODEL=burger``` and then we’re going to launch the g-mapping node of the slam node and the methods is the g-mapping which you can do different methods of mapping but we’re just going to go with the default usually is g-mapping so we’re gonna write the command ``` $ roslaunch  turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping ```so we’re gonna launch that and to look at this we’re going to open up our Rviz (in graphical tools )

![image](https://user-images.githubusercontent.com/86170422/123352498-14f75280-d568-11eb-9ab7-ad8644ae2b8c.png)

So now that we’re here and the mapping is already begun you can see that it’s incomplete so in order to navigate autonomously and things like that you’re going to want to have a full map of your environment so to do this we’re just going to move the turtlebot around so in a new shell you again specify the turtlebot you always have to specify the turtlebot ``` $ export TURTLEBOT3_MODEL=burger ``` and you’re going to ``` $ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch ``` and this is gonna allow us to move turtlebot and this is it after we move it 

![image](https://user-images.githubusercontent.com/86170422/123352672-7e776100-d568-11eb-8ada-28a27ec67ab2.png)

So you’re going to use this map in navigation so you’re going to want to save it so the last step is to save this map so we’re going to open up a new shell and we’re going to use the map server node in order to save it so here we’re going to type this command ``` $ rosrun map_server map_saver -f ~/map ```

![image](https://user-images.githubusercontent.com/86170422/123352727-a1a21080-d568-11eb-9ad7-bef66a4480f1.png)


![image](https://user-images.githubusercontent.com/86170422/123352742-a666c480-d568-11eb-8f63-d19a04b28926.png)


And now you have your map ready to go .




