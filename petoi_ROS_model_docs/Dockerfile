# This is an auto generated Dockerfile for ros:ros-base
# generated from docker_images/create_ros_image.Dockerfile.em
FROM osrf/ros:noetic-desktop-full

# non-interactive
ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y git ros-noetic-effort-controllers

# Set up the catkin workspace
RUN mkdir -p /app/catkin_ws/src
WORKDIR /app/catkin_ws
RUN /bin/bash -c "source /opt/ros/noetic/setup.bash; catkin_make"

# clone the opencat repo
WORKDIR /app/catkin_ws/src
RUN git clone https://github.com/PetoiCamp/ros_opencat.git

# source /opt/ros/noetic/setup.bash
# source /app/catkin_ws/devel/setup.bash
RUN echo "source /opt/ros/noetic/setup.bash" >> /root/.bashrc
RUN echo "source /app/catkin_ws/devel/setup.bash" >> /root/.bashrc

# Set up the entrypoint
ENTRYPOINT ["/bin/bash"]
