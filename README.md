# Overview

It's just for running content filtered topic demo

# Steps

## Development Setup

Please refer to https://docs.ros.org/en/galactic/Installation/Linux-Development-Setup.html to build environment.

## Download repositories

Use the similar traditional steps to download all ros2 repos

```
$ mkdir ros2-cft && cd $_
$ git clone -b topic-debug-connextdds-cft https://github.com/iuhilnehc-ynos/ros2.git
$ mkdir src
$ vcs import src < ros2/ros2.repos
$ vcs import src < ros2/cft-demo.repos
```

## Build ros2

- Ignore some unrelated repositories

```
$ pushd src
$ touch ./ros2/rviz/COLCON_IGNORE \
    ./ros2/ros1_bridge/COLCON_IGNORE \
    ./ros-visualization/COLCON_IGNORE
$ popd
```

- Set environment variables for connextdds

```
$ source /opt/rti.com/rti_connext_dds-5.3.1/resource/scripts/rtisetenv_x64Linux3gcc5.4.0.bash
```

- Build without test

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

  <details><summary> log </summary>
  <p>

  ```shell
  $ RMW_IMPLEMENTATION=rmw_cyclonedds_cpp ros2 launch cft_demo cft_demo.launch.py
  [INFO] [launch]: All log files can be found below /home/chenlh/.ros/log/2021-10-16-09-09-58-978526-OptiPlex-7050-637745
  [INFO] [launch]: Default logging verbosity is set to INFO
  [INFO] [subscriber_member_function_with_content_filtered_topic-1]: process started with pid [637749]
  [subscriber_member_function_with_content_filtered_topic-1] [WARN] [1634346599.136157374] [minimal_subscriber_with_content_filtered_topic]: Content filtered topic is not enabled for the subscription.
  [INFO] [parameter_blackboard-2]: process started with pid [637765]
  [subscriber_member_function_with_content_filtered_topic-1] [INFO] [1634346601.145742498] [minimal_subscriber_with_content_filtered_topic]: I heard a ParameterEvent for Node '/parameter_blackboard',
  [subscriber_member_function_with_content_filtered_topic-1] Parameter event:
  [subscriber_member_function_with_content_filtered_topic-1]  new parameters:
  [subscriber_member_function_with_content_filtered_topic-1]   use_sim_time=false
  [subscriber_member_function_with_content_filtered_topic-1]
  [subscriber_member_function_with_content_filtered_topic-1] [INFO] [1634346601.147536279] [minimal_subscriber_with_content_filtered_topic]: I heard a ParameterEvent for Node '/parameter_blackboard',
  [subscriber_member_function_with_content_filtered_topic-1] Parameter event:
  [subscriber_member_function_with_content_filtered_topic-1]  new parameters:
  [subscriber_member_function_with_content_filtered_topic-1]   qos_overrides./parameter_events.publisher.durability=volatile
  [subscriber_member_function_with_content_filtered_topic-1]
  [subscriber_member_function_with_content_filtered_topic-1] [INFO] [1634346601.147686713] [minimal_subscriber_with_content_filtered_topic]: I heard a ParameterEvent for Node '/parameter_blackboard',
  [subscriber_member_function_with_content_filtered_topic-1] Parameter event:
  [subscriber_member_function_with_content_filtered_topic-1]  new parameters:
  [subscriber_member_function_with_content_filtered_topic-1]   qos_overrides./parameter_events.publisher.history=keep_last
  [subscriber_member_function_with_content_filtered_topic-1]
  [subscriber_member_function_with_content_filtered_topic-1] [INFO] [1634346601.147824884] [minimal_subscriber_with_content_filtered_topic]: I heard a ParameterEvent for Node '/parameter_blackboard',
  [subscriber_member_function_with_content_filtered_topic-1] Parameter event:
  [subscriber_member_function_with_content_filtered_topic-1]  new parameters:
  [subscriber_member_function_with_content_filtered_topic-1]   qos_overrides./parameter_events.publisher.depth=1000
  [subscriber_member_function_with_content_filtered_topic-1]
  [subscriber_member_function_with_content_filtered_topic-1] [INFO] [1634346601.147944868] [minimal_subscriber_with_content_filtered_topic]: I heard a ParameterEvent for Node '/parameter_blackboard',
  [subscriber_member_function_with_content_filtered_topic-1] Parameter event:
  [subscriber_member_function_with_content_filtered_topic-1]  new parameters:
  [subscriber_member_function_with_content_filtered_topic-1]   qos_overrides./parameter_events.publisher.reliability=reliable
  [subscriber_member_function_with_content_filtered_topic-1]
  [parameter_blackboard-2] [INFO] [1634346601.147675102] [parameter_blackboard]: Parameter blackboard node named '/parameter_blackboard' ready, and serving '5' parameters already!

  // after running 'RMW_IMPLEMENTATION=rmw_cyclonedds_cpp ros2 param set /parameter_blackboard param1 True' successfuly

  [subscriber_member_function_with_content_filtered_topic-1] [INFO] [1634346661.898464533] [minimal_subscriber_with_content_filtered_topic]: I heard a ParameterEvent for Node '/_ros2cli_637819',
  [subscriber_member_function_with_content_filtered_topic-1] Parameter event:
  [subscriber_member_function_with_content_filtered_topic-1]  new parameters:
  [subscriber_member_function_with_content_filtered_topic-1]   use_sim_time=false
  [subscriber_member_function_with_content_filtered_topic-1]
  [subscriber_member_function_with_content_filtered_topic-1] [INFO] [1634346662.404084545] [minimal_subscriber_with_content_filtered_topic]: I heard a ParameterEvent for Node '/parameter_blackboard',
  [subscriber_member_function_with_content_filtered_topic-1] Parameter event:
  [subscriber_member_function_with_content_filtered_topic-1]  new parameters:
  [subscriber_member_function_with_content_filtered_topic-1]   param1=true
  [subscriber_member_function_with_content_filtered_topic-1]

  // after running 'RMW_IMPLEMENTATION=rmw_cyclonedds_cpp ros2 param set /minimal_subscriber_with_content_filtered_topic param1 True' successfuly

  [subscriber_member_function_with_content_filtered_topic-1] [INFO] [1634346682.923668390] [minimal_subscriber_with_content_filtered_topic]: I heard a ParameterEvent for Node '/_ros2cli_637853',
  [subscriber_member_function_with_content_filtered_topic-1] Parameter event:
  [subscriber_member_function_with_content_filtered_topic-1]  new parameters:
  [subscriber_member_function_with_content_filtered_topic-1]   use_sim_time=false
  [subscriber_member_function_with_content_filtered_topic-1]
  [subscriber_member_function_with_content_filtered_topic-1] [INFO] [1634346683.430102871] [minimal_subscriber_with_content_filtered_topic]: I heard a ParameterEvent for Node '/minimal_subscriber_with_content_filtered_topic',
  [subscriber_member_function_with_content_filtered_topic-1] Parameter event:
  [subscriber_member_function_with_content_filtered_topic-1]  new parameters:
  [subscriber_member_function_with_content_filtered_topic-1]   param1=true
  [subscriber_member_function_with_content_filtered_topic-1]
  ```

  </p>
  </details>

- console B

  ```
  $ source install/setup.bash
  $ RMW_IMPLEMENTATION=rmw_cyclonedds_cpp ros2 param set /parameter_blackboard param1 True
  $ RMW_IMPLEMENTATION=rmw_cyclonedds_cpp ros2 param set /minimal_subscriber_with_content_filtered_topic param1 True
  ```

### RMW implementation with ConnextDDS

- console A

  ```
  $ source install/setup.bash
  $ RMW_IMPLEMENTATION=rmw_connextdds ros2 launch cft_demo cft_demo.launch.py
  ```

- console B

  ```
  $ source install/setup.bash
  $ RMW_IMPLEMENTATION=rmw_connextdds ros2 param set /parameter_blackboard param1 True
  $ RMW_IMPLEMENTATION=rmw_connextdds ros2 param set /minimal_subscriber_with_content_filtered_topic param1 True
  $ RMW_IMPLEMENTATION=rmw_connextdds ros2 param set /minimal_subscriber_with_content_filtered_topic param2 True
  // after creating a 'test_param' parameter for '/minimal_subscriber_with_content_filtered_topic', it's expected that the executable '/minimal_subscriber_with_content_filtered_topic' can only focus on
  // if the 'test_param' is updated.
  $ RMW_IMPLEMENTATION=rmw_connextdds ros2 param set /minimal_subscriber_with_content_filtered_topic test_param True
  $ RMW_IMPLEMENTATION=rmw_connextdds ros2 param set /parameter_blackboard param2 True
  $ RMW_IMPLEMENTATION=rmw_connextdds ros2 param set /minimal_subscriber_with_content_filtered_topic test_param False
  $ RMW_IMPLEMENTATION=rmw_connextdds ros2 param set /minimal_subscriber_with_content_filtered_topic param3 True
  ```
