| 问题                                                         |                           解决方法                           |
| ------------------------------------------------------------ | :----------------------------------------------------------: |
| rosrun package_name tab不出节点名字                          | 1.**查看CMakeList.txt中间的顺序**  2.如果CMakeList中出现`find_package(ament_cmake REQUIRED)`说明这个包版本为ROS2，换一个包3.注意在新开的工作空间（还没有在.bashrc中加入source的）需要先source |
| I*mportError: No module named catkin.environment_cache<br/>CMake Error at /opt/ros/melodic/share/catkin/cmake/safe_execute_process.cmake:11 (message):<br/>  execute_process(/usr/bin/python2<br/>  "/home/liuisyang/build/catkin_generated/generate_cached_setup.py") returned<br/>  error code 1* (开启Clion时报错) |                                                              |
| *error: expected constructor, destructor, or type conversion before ‘(’ token<br/> PLUGINLIB_DECLARE_CLASS(pointcloud_to_laserscan, PointCloudToLaserScanNodelet, pointcloud_to_laserscan::PointCloudToLaserScanNodelet, nodelet::Nodelet);<br/>                        ^<br/>make[2]: *** [CMakeFiles/pointcloud_to_laserscan.dir/src/pointcloud_to_laserscan_nodelet.cpp.o] Error 1<br/>make[1]: *** [CMakeFiles/pointcloud_to_laserscan.dir/all] Error 2<br/>make: *** [all] Error 2*  (下载的包pointcloud_to_laserscan编译时报错) | 将该处代码修改为:`PLUGINLIB_EXPORT_CLASS(pointcloud_to_laserscan::PointCloudToLaserScanNodelet, nodelet::Nodelet);` |
| *Policy CMP0054 is not set: Only interpret if() arguments as variables or<br/>  keywords when unquoted.  Run "cmake --help-policy CMP0054" for policy<br/>  details.  Use the cmake_policy command to set the policy and suppress this<br/>  warning.* |                                                              |
| 单独的pointcloud_to_laserscan功能包可以在编译空间运行，但是放在一起和别个功能包就不行 | 尝试了catkin clear然后重新编译依旧不行.从终端用apt-get install下可以使用。**在包缺失的时候先用终端下载，如果不可以再网上自己找包** |
| 对‘ros::NodeHandle::~NodeHandle()’未定义的引用 subscribe_scan_node.cpp:(.text+0x5ff)：对‘ros::Subscriber::~Subscriber()’未定义的引用 subscribe_scan_node.cpp:(.text+0x60e)：对‘ros::NodeHandle::~NodeHandle()’未定义的引用 |                   下次遇见先排除拼写错误。                   |
| launch文件中无法成功加载world文件                            |             在launch文件中把相对路径改成绝对路径             |
| launch文件中无法开启自己写的节点，但是在终端可以打开运行     |                    launch文件错误（同下）                    |
| mon launch报错：*what():  Could not find node 'subscribe_scan_node' in package 'subscribe_scan'* | 在launch文件中开节点的方法   `<node pkg="pkg_name" type="node_name" name="any"/>`其中`node_name`对应node.cpp中ros::init(argc,argv,"name")中的name.和cpp文件名无关 |
| 回调函数laserCallback返回值一直为0.45                        | 把min的初始化`double min = msg->range_min;`改为`double min = msg->range_max;`或者一个很大的值。`for (int i = 0; i < msg->ranges.size(); ++i) {     if (msg->ranges[i] < min)         min = msg->ranges[i];`因为后面的代码是不断和初始值比较，（关于为什么一开始最小值为0.45还不清楚，但键盘操控的最小值大约为0.8）所以如果一开始就是一个很小的值就一直不会变. |

## 第二课作业（2022.7.12）





| 问题                                                         | 解决方法                                                     |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| 在移除原先包，引入一个在原先基础上升级的功能包时报错`CMake Error: The source directory "/home/liuisyang/catkin_ws/src/smb_common/smb_description" does not exist.` | 1.在编译空间catkin clean 再重新built，因为之前旧的软件包时生成的那些中间文件和可执行文件的影响2.设计文件路径的问题，如果不确定的话可以自己跑一遍 |
