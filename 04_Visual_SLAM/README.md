# 04 Visual SLAM（视觉 SLAM）

## 简介

视觉 SLAM 使用**相机**作为主要传感器，通过提取图像特征或直接利用像素强度来估计相机运动并构建地图。

## 主要分类

### 1. 特征点法（Feature-based）

提取并匹配图像特征点（关键点 + 描述子）来估计相机运动。

| 系统 | 相机类型 | 特点 |
|------|----------|------|
| [ORB-SLAM2](https://github.com/raulmur/ORB_SLAM2) | 单目/双目/RGB-D | 完整 SLAM 系统，含回环检测 |
| [ORB-SLAM3](https://github.com/UZ-SLAMlab/ORB_SLAM3) | 单目/双目/RGB-D/鱼眼 + IMU | 支持 VI-SLAM |
| [RTAB-Map](http://introlab.github.io/rtabmap/) | RGB-D/双目 | 长时间建图，ROS 集成好 |

### 2. 直接法（Direct）

直接最小化像素光度误差来估计运动，无需特征提取。

| 系统 | 相机类型 | 特点 |
|------|----------|------|
| [DSO](https://github.com/JakobEngel/dso) | 单目 | 稀疏直接法，精度高 |
| [LSD-SLAM](https://github.com/tum-vision/lsd_slam) | 单目 | 半稠密直接法 |
| [SVO](https://github.com/uzh-rpg/rpg_svo) | 单目/双目 | 半直接法，速度快 |

### 3. 半直接法（Semi-direct）

- **SVO**：先用直接法追踪，再用特征点法精化，兼顾速度与精度。

## 视觉里程计核心模块

```
图像获取
  → 特征提取（ORB / SIFT / SURF）或直接法光流
  → 特征匹配 / 追踪
  → 位姿估计（PnP / 对极几何 / 单应矩阵）
  → 局部 BA（Bundle Adjustment）优化
  → 关键帧管理
  → 回环检测（DBoW2 / NetVLAD）
  → 全局位姿图优化
```

## 地图类型

- **稀疏地图**：路标点（ORB-SLAM）
- **半稠密地图**：部分像素深度（LSD-SLAM、DSO）
- **稠密地图**：全像素深度（TSDF、OctoMap + RGB-D）

## 常用数据集

| 数据集 | 传感器 | 链接 |
|--------|--------|------|
| TUM RGB-D | RGB-D + IMU | https://cvg.cit.tum.de/data/datasets/rgbd-dataset |
| EuRoC MAV | 双目 + IMU | https://rpg.ifi.uzh.ch/docs/IJRR17_Burri.pdf |
| KITTI | 双目 + LiDAR + GPS | https://www.cvlibs.net/datasets/kitti/ |

## 参考论文 / 资料

- Mur-Artal, R. et al. (2015). *ORB-SLAM: A Versatile and Accurate Monocular SLAM System*. TRO.
- Engel, J. et al. (2018). *Direct Sparse Odometry*. TPAMI.
- 高翔等 (2017). *视觉 SLAM 十四讲*.

## 学习笔记

> 待补充……
