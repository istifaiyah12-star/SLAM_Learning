# 参考资源（Resources）

## 书籍

| 书名 | 作者 | 简介 |
|------|------|------|
| 《概率机器人》（Probabilistic Robotics）| Thrun, Burgard, Fox | SLAM 理论圣经，覆盖 EKF/粒子滤波/图优化 |
| 《视觉 SLAM 十四讲》（第 2 版）| 高翔 等 | 中文最系统的视觉 SLAM 入门书 |
| 《State Estimation for Robotics》| Barfoot | 系统介绍李群上的状态估计 |
| 《Multiple View Geometry in Computer Vision》| Hartley, Zisserman | 视觉几何基础，相机模型、对极几何 |

## 在线课程

- [Coursera: State Estimation and Localization for Self-Driving Cars](https://www.coursera.org/learn/state-estimation-localization-self-driving-cars)
- [Udacity: Self-Driving Car Engineer Nanodegree](https://www.udacity.com/course/self-driving-car-engineer-nanodegree--nd013)
- [深蓝学院 SLAM 课程](https://www.shenlanxueyuan.com/)

## 开源项目

| 项目 | 链接 | 说明 |
|------|------|------|
| ORB-SLAM3 | https://github.com/UZ-SLAMlab/ORB_SLAM3 | 完整视觉/视觉惯性 SLAM |
| Cartographer | https://github.com/cartographer-project/cartographer | Google 激光 SLAM |
| LOAM | https://github.com/laboshinl/loam_velodyne | 3D 激光里程计与建图 |
| LIO-SAM | https://github.com/TixiaoShan/LIO-SAM | 激光+IMU 因子图 SLAM |
| VINS-Mono | https://github.com/HKUST-Aerial-Robotics/VINS-Mono | 单目视觉惯性 SLAM |
| OpenVINS | https://github.com/rpng/open_vins | 开放的视觉惯性里程计框架 |
| g2o | https://github.com/RainerKuemmerle/g2o | 图优化通用框架 |
| GTSAM | https://gtsam.org/ | 因子图优化库 |
| Sophus | https://github.com/strasdat/Sophus | 李群/李代数 C++ 库 |
| OpenSLAM | https://openslam-org.github.io/ | 多种 SLAM 算法集合 |

## 数据集

| 数据集 | 传感器 | 链接 |
|--------|--------|------|
| KITTI | 双目 + Velodyne + GPS/IMU | https://www.cvlibs.net/datasets/kitti/ |
| TUM RGB-D | RGB-D + IMU | https://cvg.cit.tum.de/data/datasets/rgbd-dataset |
| EuRoC MAV | 双目 + IMU | https://rpg.ifi.uzh.ch/docs/IJRR17_Burri.pdf |
| MulRan | 3D LiDAR + GPS/IMU + Radar | https://sites.google.com/view/mulran-pr |
| Hilti SLAM | LiDAR + 相机 + IMU | https://hilti-challenge.com/ |

## 重要论文

| 年份 | 论文 | 会议/期刊 |
|------|------|-----------|
| 1986 | Smith & Cheeseman, *On the Representation and Estimation of Spatial Uncertainty* | IJRR |
| 2002 | Montemerlo et al., *FastSLAM* | AAAI |
| 2006 | Grisetti et al., *Improved Techniques for Grid Mapping with Rao-Blackwellized Particle Filters* | TRO |
| 2010 | Grisetti et al., *A Tutorial on Graph-Based SLAM* | IEEE ITS Magazine |
| 2011 | Kümmerle et al., *g2o: A General Framework for Graph Optimization* | ICRA |
| 2012 | Kaess et al., *iSAM2* | IJRR |
| 2014 | Zhang & Singh, *LOAM* | RSS |
| 2015 | Mur-Artal et al., *ORB-SLAM* | TRO |
| 2017 | Forster et al., *On-Manifold Preintegration* | TRO |
| 2018 | Qin et al., *VINS-Mono* | TRO |
| 2018 | Engel et al., *Direct Sparse Odometry* | TPAMI |
| 2021 | Campos et al., *ORB-SLAM3* | TRO |
