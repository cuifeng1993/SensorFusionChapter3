# 深蓝学院《多传感器融合定位》第二期作业

深蓝学院, 多传感器融合定位与建图, 基于线面特征的激光里程计，第3章Lidar Odometry using LOAM代码框架.

---

## Overview

本作业旨在实现基于线面特征的激光前端里程计算法.

---

## Getting Started

### 及格要求: 推导残差模型的雅可比
[点击链接进入](SensorFusionChapter3/doc/)指南

### 良好要求: 编程实现新模型的解析式求导

启动Docker后, 打开浏览器, 进入Web Workspace. 启动Terminator, 将两个Shell的工作目录切换如下:

<img src="doc/terminator.png" alt="Terminator" width="100%">

在**上侧**的Shell中, 输入如下命令, **编译catkin_workspace**

```bash
# build
catkin config --install && catkin build
```

然后**启动解决方案**

```bash
# set up session:
source install/setup.bash
# launch:
roslaunch lidar_localization front_end.launch
```

在**下侧**的Shell中, 输入如下命令, **Play KITTI ROS Bag**. 两个数据集均可用于完成课程, 对代码功能的运行没有任何影响, 区别在于第一个有Camera信息

```bash
# play ROS bag, full KITTI:
rosbag play kitti_2011_10_03_drive_0027_synced.bag
# play ROS bag, lidar-only KITTI:
rosbag play kitti_lidar_only_2011_10_03_drive_0027_synced.bag
```

成功后, 可以看到如下的RViz界面:

<img src="doc/demo.png" alt="ALOAM Frontend Demo" width="100%">

本次作业的代码框架基于秦通大佬的[ALOAM](https://github.com/HKUST-Aerial-Robotics/A-LOAM)改造:

* 仅保留了**点云预处理**与**前端**两部分
* 在此基础上实现了与任佬框架的暴力集成, 上述功能并没有完全适配任佬框架的编码实践, 欢迎有追求的你在此基础上进行改造.

请你在此基础上实现**新模型的解析求导**. 请在提交的报告中, 清晰明了地分析你的实现, 将代码实现与你的公式推导相对应. **仅仅跑通框架, 不会得到此题目的分数**

**提示** 请全文搜索关键词**TODO**, 开始你的Coding. 加油!

### 优秀要求: 给出新模型基于evo的精度评测结果

**注意** 如果你没有提交残差模型的解析实现, 你不会得到此题目的分数

此处以Docker Workspace为例. 在Terminator中添加新窗口, 切换至如下目录:

```bash
/workspace/assignments/02-loams/src/lidar_localization/slam_data/trajectory
```

该目录下会输出:

* 作为Ground Truth的RTK轨迹估计, ground_truth.txt
* Lidar Frontend轨迹估计, laser_odom.txt

请使用上述两个文件, 完成**evo**的评估
