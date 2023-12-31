To make the TurtleBot go around a person once it detects the person in its projected path, you will need to implement a path planning algorithm. You can use the A* algorithm which is a common path planning algorithm. Here is a step-by-step guide to achieve this:

Detection of the Person: You have already implemented this using YOLO. When the person is detected, you can retrieve the bounding box coordinates (x1, y1, x2, y2) of the detected person.
Mapping the Person's Position to the Robot's World: The bounding box coordinates are in the image frame, you'll need to map these coordinates to the robot's world. You can do this using the depth data from the depth sensor (if available) or estimating the distance based on the size of the bounding box. The position of the person can be represented as an obstacle in the robot's world map.
Path Planning: Use a path planning algorithm such as the A* algorithm to plan a path around the person. The A* algorithm finds the shortest path from the robot's current position to the target position, considering the person as an obstacle. You can use a library such as ROS's move_base package to accomplish this 1.
Moving the Robot: Once the path is planned, you can command the robot to follow the planned path. You can do this by publishing velocity commands to the appropriate topic, typically /cmd_vel.

Here is a simple pseudo code to illustrate the above steps:



This code is a simple illustration and may need to be adapted based on your specific application and environment. It assumes that you have a move_base server running which can handle path planning. If you don't, you might need to implement the A* algorithm yourself. There are many resources and libraries available online for this purpose.

Remember that real-world environments are dynamic and unpredictable. The robot will need to continually update its world map and re-plan its path accordingly. You might also need to handle edge cases such as when the person moves or when there are other obstacles in the environment.

For a more robust implementation, you could consider integrating a SLAM (Simultaneous Localization and Mapping) system with your robot. SLAM allows the robot to create a map of its environment while keeping track of its own position within the map, which can be very useful for path planning and navigation 3.
