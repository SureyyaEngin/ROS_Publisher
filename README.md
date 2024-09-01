# ROS Publisher Node Example

This project demonstrates how to create a simple ROS publisher node in Python. The publisher node sends a message to a specific topic at a regular interval. Below, you'll find a detailed guide on how to set up and run this example, along with an explanation of the code.

## Table of Contents

- [Overview](#overview)
- [Python Code Explanation](#python-code-explanation)
- [Setup Instructions](#setup-instructions)
  - [Building the Project](#building-the-project)
  - [Running the Nodes](#running-the-nodes)
  - [Viewing the Published Messages](#viewing-the-published-messages)
- [Conclusion](#conclusion)

## Overview

This project is a basic example of a ROS (Robot Operating System) publisher node. The node is responsible for publishing messages to a topic named `/talking_topic`. This is useful for scenarios where you need to continuously send data or information to other nodes in the ROS ecosystem.

## Python Code Explanation

### What Does This Code Do?

- **Publisher Node**: The code defines a ROS node named `publisher_node` which publishes a message to the topic `/talking_topic` at a rate of 1 message per second.
- **Message Content**: The message published is a string containing `"Hello Lala - "` followed by the current time (`rospy.get_time()`).
- **rospy.Publisher**: This function is used to create a publisher object. The parameters include the topic name (`talking_topic`), the message type (`String`), and the queue size (`10`), which controls how many messages to store for subscribers if they are not receiving messages quickly enough.
- **Loop**: The `while not rospy.is_shutdown()` loop ensures that the node keeps publishing messages until the node is stopped.

## Setup Instructions

### Building the Project

To build the project, follow these steps:

1. **Navigate to the Project Directory**:
   
   ```bash
   cd /path/to/your/catkin_workspace
   ```

2. **Build the Workspace**:

   ```bash
   catkin_make
   ```

3. **Source the Workspace**:

   ```bash
   source devel/setup.bash
   ```

### Running the Nodes

1. **Start the ROS Master Node**:
   
   Open a new terminal and run:

   ```bash
   roscore
   ```

2. **Run the Publisher Node**:
   
   Go back to the first terminal (or open a new one) and run:

   ```bash
   rosrun [your_package_name] publisher_node.py
   ```

   For example:

   ```bash
   rosrun ROS_Publisher publisher_node.py
   ```

   You should see an output like this:

   ```
   [INFO] [1614540798.697452]: Publisher Node Started, now publishing messages
   ```

### Viewing the Published Messages

1. **List All Active Topics**:
   
   Open a new terminal and type:

   ```bash
   rostopic list
   ```

   You should see output similar to this:

   ```
   /rosout
   /rosout_agg
   /talking_topic
   ```

   Here, `/talking_topic` is the topic created by our publisher node.

2. **View the Messages Published to `talking_topic`**:

   Run the following command:

   ```bash
   rostopic echo /talking_topic
   ```

   This will show you the messages being published by the `publisher_node`. The output should look like this:

   ```
   data: "Hello Lala - 1614540884.6985677"
   ```

   A new message will be displayed every second.

## Conclusion

This `README.md` file provides a comprehensive guide to setting up and running a basic ROS publisher node. The example demonstrates the fundamental concepts of message publishing in ROS, making it a great starting point for those new to ROS.

If you have any questions or need further assistance, feel free to reach out or consult the ROS documentation.
