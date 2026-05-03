# 06 Visual-Inertial SLAM（视觉惯性 SLAM）

## 简介

视觉惯性 SLAM（VI-SLAM）融合**相机**与**惯性测量单元（IMU）**，结合视觉的精度与 IMU 的高频率，克服单纯视觉 SLAM 在快速运动、光线变化等场景下的不足。

## 融合方式

| 方式 | 描述 | 代表系统 |
|------|------|----------|
| 松耦合（Loosely Coupled）| 视觉里程计与 IMU 积分结果独立融合 | 部分 EKF 方案 |
| 紧耦合（Tightly Coupled）| 视觉残差与 IMU 预积分残差联合优化 | VINS-Mono、ORB-SLAM3 |

## 主要系统

| 系统 | 相机 | 特点 |
|------|------|------|
| [VINS-Mono](https://github.com/HKUST-Aerial-Robotics/VINS-Mono) | 单目 | 紧耦合，滑动窗口优化，回环检测 |
| [VINS-Fusion](https://github.com/HKUST-Aerial-Robotics/VINS-Fusion) | 单目/双目/RGB-D | VINS-Mono 扩展，支持 GPS 融合 |
| [OKVIS](https://github.com/ethz-asl/okvis) | 双目 | 关键帧非线性优化 |
| [MSCKF](https://github.com/KumarRobotics/msckf_vio) | 双目 | 多状态约束 EKF，计算高效 |
| [ORB-SLAM3](https://github.com/UZ-SLAMlab/ORB_SLAM3) | 单目/双目/RGB-D + IMU | 支持 VI 模式，地图重用 |
| [OpenVINS](https://github.com/rpng/open_vins) | 单目/双目 + IMU | MSCKF 变体，易于扩展 |

## IMU 预积分

IMU 预积分（Preintegration）是 VI-SLAM 的核心技术之一：
- 在两个关键帧之间对 IMU 数据积分，获得相对位姿约束。
- 避免每次优化时重新积分，提升效率。
- 参考：Forster, C. et al. (2017). *On-Manifold Preintegration for Real-Time Visual-Inertial Odometry*. TRO.

## 系统框架（以 VINS-Mono 为例）

```
图像 + IMU 数据
  → 特征提取与追踪（KLT 光流）
  → IMU 预积分
  → 初始化（视觉-惯性对齐，估计重力方向、尺度、偏置）
  → 滑动窗口紧耦合优化
     min Σ (视觉重投影误差 + IMU 预积分误差 + 边缘化先验)
  → 回环检测与全局位姿图优化
  → 输出位姿 + 稀疏地图
```

## 常用数据集

| 数据集 | 传感器 | 链接 |
|--------|--------|------|
| EuRoC MAV | 双目 + IMU (200Hz) | https://rpg.ifi.uzh.ch/docs/IJRR17_Burri.pdf |
| TUM-VI | 单目/双目 + IMU | https://cvg.cit.tum.de/data/datasets/visual-inertial-dataset |
| UZH-FPV | 单目 + IMU | https://fpv.ifi.uzh.ch/ |

## 参考论文 / 资料

- Qin, T., Li, P., & Shen, S. (2018). *VINS-Mono: A Robust and Versatile Monocular Visual-Inertial State Estimator*. TRO.
- Forster, C. et al. (2017). *On-Manifold Preintegration for Real-Time Visual-Inertial Odometry*. TRO.
- Mourikis, A. & Roumeliotis, S. (2007). *A Multi-State Constraint Kalman Filter for Vision-aided Inertial Navigation*. ICRA.

## 学习笔记

> 待补充……
