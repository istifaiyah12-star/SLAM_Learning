# SLAM_Learning

**slam学习记录，分各种slam算法**

本仓库记录个人学习各类 SLAM（Simultaneous Localization and Mapping，即时定位与地图构建）算法的笔记、代码与心得，按算法类别进行分类整理。

---

## 目录结构

```
SLAM_Learning/
├── 01_EKF_SLAM/          # 基于扩展卡尔曼滤波的 SLAM
├── 02_Particle_Filter_SLAM/  # 基于粒子滤波的 SLAM（FastSLAM）
├── 03_Graph_SLAM/         # 图优化 SLAM（g2o、GTSAM、iSAM 等）
├── 04_Visual_SLAM/        # 视觉 SLAM（ORB-SLAM、DSO、LSD-SLAM 等）
├── 05_LiDAR_SLAM/         # 激光 SLAM（Cartographer、LOAM、LeGO-LOAM 等）
├── 06_Visual_Inertial_SLAM/  # 视觉惯性 SLAM（VINS-Mono、MSCKF 等）
└── resources/             # 参考资料、论文链接、书单
```

---

## 各算法简介

| 序号 | 类别 | 代表算法 | 传感器 |
|------|------|----------|--------|
| 01 | 滤波 SLAM | EKF-SLAM | 测距/里程计 |
| 02 | 滤波 SLAM | FastSLAM / Particle Filter | 测距/里程计 |
| 03 | 图优化 SLAM | g2o、GTSAM、iSAM2 | 通用 |
| 04 | 视觉 SLAM | ORB-SLAM2/3、DSO、LSD-SLAM | 单/双目/RGB-D 相机 |
| 05 | 激光 SLAM | Cartographer、LOAM、LeGO-LOAM、KISS-ICP | 2D/3D 激光雷达 |
| 06 | 视觉惯性 SLAM | VINS-Mono、VINS-Fusion、MSCKF | 相机 + IMU |

---

## 学习路线建议

1. **数学基础**：概率论、矩阵运算、李群李代数
2. **状态估计基础**：卡尔曼滤波、粒子滤波
3. **图优化基础**：因子图、最小二乘、g2o/Ceres 库使用
4. **视觉里程计**：特征点法（ORB）、直接法（DSO）
5. **激光里程计**：点云匹配（ICP、NDT）
6. **融合系统**：IMU 预积分、紧耦合 / 松耦合

---

## 参考资源

- 《概率机器人》（Probabilistic Robotics）—— Thrun, Burgard, Fox
- 《视觉 SLAM 十四讲》—— 高翔
- [OpenSLAM](https://openslam-org.github.io/)
- [ORB-SLAM3](https://github.com/UZ-SLAMlab/ORB_SLAM3)
- [Cartographer](https://github.com/cartographer-project/cartographer)
- [LOAM](https://github.com/laboshinl/loam_velodyne)
- [VINS-Mono](https://github.com/HKUST-Aerial-Robotics/VINS-Mono)

---

> 持续更新中……
