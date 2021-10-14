# Overview

It's just for running content filtered topic demo

# Steps

## Download repositories

Use the similar traditional steps to download all ros2 repos

```
$ mkdir ros2-cft && cd $_
$ git clone -b topic-cft-demo https://github.com/iuhilnehc-ynos/ros2.git
$ mkdir src
$ vcs import src < ros2/ros2.repos
$ vcs import src < ros2/cft-demo.repos
```

## Install necessary dependency packages

```
$ rosdep update
$ rosdep install --from-paths src --ignore-src --rosdistro galactic -y
```

## Build ros2

- Ignore unrelated repos

```
$ pushd src
$ touch ./ros2/rviz/COLCON_IGNORE \
    ./ros-visualization/COLCON_IGNORE
$ popd
```

- build

```
$ colcon build --cmake-args -DBUILD_TESTING:BOOL=OFF
```

## Run cft demo

### RMW implementation with CycloneDDS

- console A

```
$ source install/setup.bash
$ RMW_IMPLEMENTATION=rmw_cyclonedds_cpp ros2 launch cft_demo cft_demo.launch.py
```

- console B

```
$ source install/setup.bash
$ RMW_IMPLEMENTATION=rmw_cyclonedds_cpp ros2 param set /minimal_subscriber_with_content_filtered_topic test_param True
```

- log

```
todo
```

### RMW implementation with FastDDS

- console A

```
$ source install/setup.bash
$ RMW_IMPLEMENTATION=rmw_fastrtps_cpp ros2 launch cft_demo cft_demo.launch.py
```

- console B

```
$ source install/setup.bash
$ RMW_IMPLEMENTATION=rmw_fastrtps_cpp ros2 param set /minimal_subscriber_with_content_filtered_topic test_param True
```

- log

```
todo
```

