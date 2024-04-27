If you wish to run Bittle or Nybble Gazebo / rviz inside the container,
do the following first:
```
xhost +si:localuser:root
docker-compose build
docker-compose run --rm ros-rviz
```
Then proceed from **Launch Gazebo simulation** step in the docs.