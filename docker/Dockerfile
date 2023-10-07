FROM ros:noetic-perception

RUN apt update && apt install -y git 

ENV ROS_WS /opt/ros_ws
RUN mkdir -p $ROS_WS/src
WORKDIR $ROS_WS/src
COPY . livox2pointcloud
RUN git clone https://github.com/Livox-SDK/livox_ros_driver

WORKDIR $ROS_WS 
RUN bash -c '. /opt/ros/noetic/setup.bash && catkin_make -DCMAKE_BUILD_TYPE=Release'

COPY ./docker/entrypoint.sh /
ENTRYPOINT ["/entrypoint.sh"]
