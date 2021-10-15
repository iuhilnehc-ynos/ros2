# Overview

It's just for running content filtered topic demo

# Steps

## Development Setup

Please refer to https://docs.ros.org/en/galactic/Installation/Linux-Development-Setup.html to build environment.

## Download repositories

Use the similar traditional steps to download all ros2 repos

```
$ mkdir ros2-cft && cd $_
$ git clone -b topic-cft-demo https://github.com/iuhilnehc-ynos/ros2.git
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
  [INFO] [launch]: All log files can be found below /home/chenlh/.ros/log/2021-10-15-11-16-42-014534-OptiPlex-7080-759362
  [INFO] [launch]: Default logging verbosity is set to INFO
  [INFO] [subscriber_member_function_with_content_filtered_topic-1]: process started with pid [759364]
  [subscriber_member_function_with_content_filtered_topic-1] [WARN] [1634267802.140929276] [minimal_subscriber_with_content_filtered_topic]: Content filtered topic is not enabled for the subscription.
  [INFO] [parameter_blackboard-2]: process started with pid [759375]
  [subscriber_member_function_with_content_filtered_topic-1] [INFO] [1634267804.155788410] [minimal_subscriber_with_content_filtered_topic]: I heard a ParameterEvent for Node '/parameter_blackboard',
  [subscriber_member_function_with_content_filtered_topic-1] Parameter event:
  [subscriber_member_function_with_content_filtered_topic-1]  new parameters:
  [subscriber_member_function_with_content_filtered_topic-1]   use_sim_time=false
  [subscriber_member_function_with_content_filtered_topic-1]
  [subscriber_member_function_with_content_filtered_topic-1] [INFO] [1634267804.156980885] [minimal_subscriber_with_content_filtered_topic]: I heard a ParameterEvent for Node '/parameter_blackboard',
  [subscriber_member_function_with_content_filtered_topic-1] Parameter event:
  [subscriber_member_function_with_content_filtered_topic-1]  new parameters:
  [subscriber_member_function_with_content_filtered_topic-1]   qos_overrides./parameter_events.publisher.durability=volatile
  [subscriber_member_function_with_content_filtered_topic-1]
  [subscriber_member_function_with_content_filtered_topic-1] [INFO] [1634267804.157087250] [minimal_subscriber_with_content_filtered_topic]: I heard a ParameterEvent for Node '/parameter_blackboard',
  [subscriber_member_function_with_content_filtered_topic-1] Parameter event:
  [subscriber_member_function_with_content_filtered_topic-1]  new parameters:
  [subscriber_member_function_with_content_filtered_topic-1]   qos_overrides./parameter_events.publisher.history=keep_last
  [subscriber_member_function_with_content_filtered_topic-1]
  [subscriber_member_function_with_content_filtered_topic-1] [INFO] [1634267804.157188950] [minimal_subscriber_with_content_filtered_topic]: I heard a ParameterEvent for Node '/parameter_blackboard',
  [subscriber_member_function_with_content_filtered_topic-1] Parameter event:
  [subscriber_member_function_with_content_filtered_topic-1]  new parameters:
  [subscriber_member_function_with_content_filtered_topic-1]   qos_overrides./parameter_events.publisher.depth=1000
  [subscriber_member_function_with_content_filtered_topic-1]
  [parameter_blackboard-2] [INFO] [1634267804.157181812] [parameter_blackboard]: Parameter blackboard node named '/parameter_blackboard' ready, and serving '5' parameters already!
  [subscriber_member_function_with_content_filtered_topic-1] [INFO] [1634267804.157285881] [minimal_subscriber_with_content_filtered_topic]: I heard a ParameterEvent for Node '/parameter_blackboard',
  [subscriber_member_function_with_content_filtered_topic-1] Parameter event:
  [subscriber_member_function_with_content_filtered_topic-1]  new parameters:
  [subscriber_member_function_with_content_filtered_topic-1]   qos_overrides./parameter_events.publisher.reliability=reliable
  [subscriber_member_function_with_content_filtered_topic-1]

  // after running 'RMW_IMPLEMENTATION=rmw_cyclonedds_cpp ros2 param set /parameter_blackboard param1 True' successfuly

  [subscriber_member_function_with_content_filtered_topic-1] [INFO] [1634267950.696183383] [minimal_subscriber_with_content_filtered_topic]: I heard a ParameterEvent for Node '/_ros2cli_759763',
  [subscriber_member_function_with_content_filtered_topic-1] Parameter event:
  [subscriber_member_function_with_content_filtered_topic-1]  new parameters:
  [subscriber_member_function_with_content_filtered_topic-1]   use_sim_time=false
  [subscriber_member_function_with_content_filtered_topic-1]
  [subscriber_member_function_with_content_filtered_topic-1] [INFO] [1634267951.203208601] [minimal_subscriber_with_content_filtered_topic]: I heard a ParameterEvent for Node '/parameter_blackboard',
  [subscriber_member_function_with_content_filtered_topic-1] Parameter event:
  [subscriber_member_function_with_content_filtered_topic-1]  new parameters:
  [subscriber_member_function_with_content_filtered_topic-1]   param1=true
  [subscriber_member_function_with_content_filtered_topic-1]

  // after running 'RMW_IMPLEMENTATION=rmw_cyclonedds_cpp ros2 param set /minimal_subscriber_with_content_filtered_topic param1 True' successfuly

  [subscriber_member_function_with_content_filtered_topic-1] [INFO] [1634267992.896036432] [minimal_subscriber_with_content_filtered_topic]: I heard a ParameterEvent for Node '/_ros2cli_759807',
  [subscriber_member_function_with_content_filtered_topic-1] Parameter event:
  [subscriber_member_function_with_content_filtered_topic-1]  new parameters:
  [subscriber_member_function_with_content_filtered_topic-1]   use_sim_time=false
  [subscriber_member_function_with_content_filtered_topic-1]
  [subscriber_member_function_with_content_filtered_topic-1] [INFO] [1634267993.402053398] [minimal_subscriber_with_content_filtered_topic]: I heard a ParameterEvent for Node '/parameter_blackboard',
  [subscriber_member_function_with_content_filtered_topic-1] Parameter event:
  [subscriber_member_function_with_content_filtered_topic-1]  changed parameters:
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

### RMW implementation with FastDDS

- console A

  ```
  $ source install/setup.bash
  $ RMW_IMPLEMENTATION=rmw_fastrtps_cpp ros2 launch cft_demo cft_demo.launch.py
  ```

  <details><summary> log </summary>
  <p>

  ```shell
  $ RMW_IMPLEMENTATION=rmw_fastrtps_cpp ros2 launch cft_demo cft_demo.launch.py
  [INFO] [launch]: All log files can be found below /home/chenlh/.ros/log/2021-10-15-13-02-38-825345-OptiPlex-7080-771765
  [INFO] [launch]: Default logging verbosity is set to INFO
  [INFO] [subscriber_member_function_with_content_filtered_topic-1]: process started with pid [771767]
  [subscriber_member_function_with_content_filtered_topic-1] [INFO] [1634274158.977323323] [minimal_subscriber_with_content_filtered_topic]: get_cft_expression_parameters filter_expression: [node = %0]
  [subscriber_member_function_with_content_filtered_topic-1] [INFO] [1634274158.977455637] [minimal_subscriber_with_content_filtered_topic]: get_cft_expression_parameters expression_parameters: [[/minimal_subscriber_with_content_filtered_topic]]
  [INFO] [parameter_blackboard-2]: process started with pid [771779]
  [parameter_blackboard-2] [INFO] [1634274161.026538373] [parameter_blackboard]: Parameter blackboard node named '/parameter_blackboard' ready, and serving '5' parameters already!

  // after running 'RMW_IMPLEMENTATION=rmw_fastrtps_cpp ros2 param set /parameter_blackboard param1 True' successfuly
  no log

  // after running 'RMW_IMPLEMENTATION=rmw_fastrtps_cpp ros2 param set /minimal_subscriber_with_content_filtered_topic param1 True' successfuly
  [subscriber_member_function_with_content_filtered_topic-1] [INFO] [1634274227.221200127] [minimal_subscriber_with_content_filtered_topic]: I heard a ParameterEvent for Node '/minimal_subscriber_with_content_filtered_topic',
  [subscriber_member_function_with_content_filtered_topic-1] Parameter event:
  [subscriber_member_function_with_content_filtered_topic-1]  new parameters:
  [subscriber_member_function_with_content_filtered_topic-1]   param1=true
  [subscriber_member_function_with_content_filtered_topic-1]

  // after running 'RMW_IMPLEMENTATION=rmw_fastrtps_cpp ros2 param set /minimal_subscriber_with_content_filtered_topic param2 True' successfuly
  [subscriber_member_function_with_content_filtered_topic-1] [INFO] [1634274244.016694246] [minimal_subscriber_with_content_filtered_topic]: I heard a ParameterEvent for Node '/minimal_subscriber_with_content_filtered_topic',
  [subscriber_member_function_with_content_filtered_topic-1] Parameter event:
  [subscriber_member_function_with_content_filtered_topic-1]  new parameters:
  [subscriber_member_function_with_content_filtered_topic-1]   param2=true
  [subscriber_member_function_with_content_filtered_topic-1]

  // after running 'RMW_IMPLEMENTATION=rmw_fastrtps_cpp ros2 param set /minimal_subscriber_with_content_filtered_topic test_param True'
  [subscriber_member_function_with_content_filtered_topic-1] [INFO] [1634274263.433119503] [minimal_subscriber_with_content_filtered_topic]: I heard a ParameterEvent for Node '/minimal_subscriber_with_content_filtered_topic',
  [subscriber_member_function_with_content_filtered_topic-1] Parameter event:
  [subscriber_member_function_with_content_filtered_topic-1]  new parameters:
  [subscriber_member_function_with_content_filtered_topic-1]   test_param=true
  [subscriber_member_function_with_content_filtered_topic-1]
  [subscriber_member_function_with_content_filtered_topic-1] [INFO] [1634274263.433403877] [minimal_subscriber_with_content_filtered_topic]: set_cft_expression_parameters filter_expression: [node = %0 AND changed_parameters[0].name = %1]
  [subscriber_member_function_with_content_filtered_topic-1] [INFO] [1634274263.433618413] [minimal_subscriber_with_content_filtered_topic]: set_cft_expression_parameters expression_parameters: [[/minimal_subscriber_with_content_filtered_topic][test_param]]
  [subscriber_member_function_with_content_filtered_topic-1] [INFO] [1634274263.434009827] [minimal_subscriber_with_content_filtered_topic]: get_cft_expression_parameters filter_expression: [node = %0 AND changed_parameters[0].name = %1]
  [subscriber_member_function_with_content_filtered_topic-1] [INFO] [1634274263.434203090] [minimal_subscriber_with_content_filtered_topic]: get_cft_expression_parameters expression_parameters: [[/minimal_subscriber_with_content_filtered_topic][test_param]]
  [subscriber_member_function_with_content_filtered_topic-1] [WARN] [1634274263.434314164] [minimal_subscriber_with_content_filtered_topic]: Though set cft expression parameters successfully and get the expected options, but the behavior is not expected.

  // after running `RMW_IMPLEMENTATION=rmw_fastrtps_cpp ros2 param set /parameter_blackboard param2 True` to get the following message is unexpected.
  [subscriber_member_function_with_content_filtered_topic-1] [INFO] [1634274281.437482955] [minimal_subscriber_with_content_filtered_topic]: I heard a ParameterEvent for Node '/_ros2cli_772314',
  [subscriber_member_function_with_content_filtered_topic-1] Parameter event:
  [subscriber_member_function_with_content_filtered_topic-1]  new parameters:
  [subscriber_member_function_with_content_filtered_topic-1]   use_sim_time=false
  [subscriber_member_function_with_content_filtered_topic-1]
  [subscriber_member_function_with_content_filtered_topic-1] [INFO] [1634274281.950060086] [minimal_subscriber_with_content_filtered_topic]: I heard a ParameterEvent for Node '/parameter_blackboard',
  [subscriber_member_function_with_content_filtered_topic-1] Parameter event:
  [subscriber_member_function_with_content_filtered_topic-1]  new parameters:
  [subscriber_member_function_with_content_filtered_topic-1]   param2=true
  [subscriber_member_function_with_content_filtered_topic-1]

  ```

  </p>
  </details>

- console B

  ```
  $ source install/setup.bash
  $ RMW_IMPLEMENTATION=rmw_fastrtps_cpp ros2 param set /parameter_blackboard param1 True
  $ RMW_IMPLEMENTATION=rmw_fastrtps_cpp ros2 param set /minimal_subscriber_with_content_filtered_topic param1 True
  $ RMW_IMPLEMENTATION=rmw_fastrtps_cpp ros2 param set /minimal_subscriber_with_content_filtered_topic param2 True
  // after creating a 'test_param' parameter for '/minimal_subscriber_with_content_filtered_topic', it's expected that the executable '/minimal_subscriber_with_content_filtered_topic' can only focus on
  // if the 'test_param' is updated.
  $ RMW_IMPLEMENTATION=rmw_fastrtps_cpp ros2 param set /minimal_subscriber_with_content_filtered_topic test_param True
  $ RMW_IMPLEMENTATION=rmw_fastrtps_cpp ros2 param set /parameter_blackboard param2 True
  ```
