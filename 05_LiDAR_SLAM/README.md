# 05 LiDAR SLAM（激光 SLAM）

## 简介

激光 SLAM 使用**激光雷达（LiDAR）**扫描环境，通过点云匹配估计传感器运动并构建精确的二维或三维地图。

## 主要分类

### 2D 激光 SLAM（平面）

| 系统 | 特点 |
|------|------|
| [GMapping](http://wiki.ros.org/gmapping) | 粒子滤波，ROS 默认建图方案 |
| [Hector SLAM](http://wiki.ros.org/hector_slam) | 无里程计，基于扫描匹配 |
| [Cartographer (2D)](https://github.com/cartographer-project/cartographer) | Google 出品，图优化后端，支持回环 |

### 3D 激光 SLAM（点云）

| 系统 | 特点 |
|------|------|
| [LOAM](https://github.com/laboshinl/loam_velodyne) | 经典 3D 激光里程计与建图 |
| [LeGO-LOAM](https://github.com/RobustFieldAutonomyLab/LeGO-LOAM) | 轻量化 LOAM，适合地面机器人 |
| [LIO-SAM](https://github.com/TixiaoShan/LIO-SAM) | 激光 + IMU，因子图优化 |
| [KISS-ICP](https://github.com/PRBonn/kiss-icp) | 简洁高效的 ICP 里程计 |
| [Cartographer (3D)](https://github.com/cartographer-project/cartographer) | 支持 3D 子图拼接与回环 |
| [HDL Graph SLAM](https://github.com/koide3/hdl_graph_slam) | 基于 NDT/GICP 的图优化 SLAM |

## 核心算法

### 点云配准

- **ICP（Iterative Closest Point）**：迭代最近点，简单但易陷入局部最优。
- **NDT（Normal Distributions Transform）**：将点云表示为正态分布，收敛更稳定。
- **GICP（Generalized ICP）**：考虑点的协方差，精度更高。

### LOAM 思路

```
激光扫描
  → 特征提取（边缘点 edge / 平面点 planar）
  → 激光里程计（高频，帧间匹配）
  → 激光建图（低频，帧与局部地图匹配）
  → 输出位姿 + 点云地图
```

## 回环检测

- **Scan Context**：基于极坐标的点云全局描述子。
- **M2DP**：多视图 2D 投影描述子。
- **BoW3D**：三维词袋模型。

## 常用数据集

| 数据集 | 传感器 | 链接 |
|--------|--------|------|
| KITTI | Velodyne 64 + 双目 + GPS/IMU | https://www.cvlibs.net/datasets/kitti/ |
| MulRan | Ouster 64 + GPS/IMU + Radar | https://sites.google.com/view/mulran-pr |
| Newer College | Ouster 64 + 相机 | https://ori-drs.github.io/newer-college-dataset/ |

## 参考论文 / 资料

- Zhang, J. & Singh, S. (2014). *LOAM: Lidar Odometry and Mapping in Real-time*. RSS.
- Shan, T. & Englot, B. (2018). *LeGO-LOAM: Lightweight and Ground-Optimized Lidar Odometry and Mapping*. IROS.
- Hess, W. et al. (2016). *Real-Time Loop Closure in 2D LIDAR SLAM*. ICRA. (Cartographer)

## 学习笔记

> 待补充……
