# rm_controls

> https://rm-control-docs.netlify.app/quick_start/rm-controls_101#%E5%87%86%E5%A4%87-can-%E8%AE%BE%E5%A4%87

## 用法

### 		1mon launch发布control和gazebo

### 		2rqt->Robot Tools ->Controller Manage->管理对应控制器

### 		3`rosrun plotjuggler plotjuggler` 暂停后shift查看值

### 		4rqt->Configuration->Dynamic Reconfigure动态调节controller参数如pid

### 		5rqt->Topic->Manager Topic 对指定话题发布参数



# ROS_control

> [https://www.guyuehome.com/890](https://www.guyuehome.com/890)

### 在机器人应用(功能包)和实际(仿真)机器人中起到中间者的作用连接两者的作用



[![clip_image008](https://www.guyuehome.com/Uploads/wp/2017/03/clip_image008_thumb.png)](https://www.guyuehome.com/Uploads/wp/2017/03/clip_image008.png)

#### 		controller manager 控制controller的加载加载运行停止等

#### 		controller可以发布值来控制joint(图为ros_controllers自带的controllers)

​				[![clip_image010](https://www.guyuehome.com/Uploads/wp/2017/03/clip_image010_thumb.png)](https://www.guyuehome.com/Uploads/wp/2017/03/clip_image010.png)

#### 		hardware resource对上提供硬件接口

#### 		hardware interface为硬件层 和真实世界直接通过write()和read()进行交互

​					transmissions 机器人传动系统通过URDF来配置

​					joint limits 关节限位,从URDF或者YAML



