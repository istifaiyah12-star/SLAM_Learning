# 02 Particle Filter SLAM / FastSLAM（粒子滤波 SLAM）

## 简介

基于粒子滤波的 SLAM 算法（代表：**FastSLAM**）使用一组加权粒子来表示机器人路径分布，每个粒子独立维护一组路标的 EKF 估计，从而将联合 SLAM 问题分解为若干独立的低维问题。

## 核心思路

- **粒子**：每个粒子 $s^{[k]}$ 代表一条可能的机器人轨迹，并携带对应的路标地图。
- **重要性采样**：根据运动模型采样新位姿，再用观测似然对粒子加权。
- **重采样**：按权重选取粒子，避免粒子退化。
- **地图更新**：每个粒子内部用独立 EKF 更新各路标估计（FastSLAM 1.0 / 2.0）。

## 优缺点

| 优点 | 缺点 |
|------|------|
| 可处理非线性/非高斯噪声 | 粒子数量影响精度与计算量 |
| 可表示多假设分布 | 粒子退化问题（粒子贫化） |
| 路标独立，地图更新高效 | 路径历史不可回溯（无后端优化）|

## FastSLAM 算法流程（简版）

```
初始化粒子集合 {s^[k]} k=1..N
循环：
    1. 运动更新：对每个粒子按运动模型采样新位姿
    2. 观测更新：
       a. 数据关联（已知或未知路标）
       b. 用 EKF 更新对应路标
       c. 计算粒子权重 w^[k] ∝ p(z | s^[k])
    3. 归一化权重
    4. 重采样
```

## 变体

- **FastSLAM 1.0**：基于里程计提议分布采样。
- **FastSLAM 2.0**：将最新观测纳入提议分布，降低采样方差。
- **Rao-Blackwellized Particle Filter（RBPF）**：用于栅格地图的粒子滤波 SLAM（如 GMapping）。

## 参考论文 / 资料

- Montemerlo, M. et al. (2002). *FastSLAM: A Factored Solution to the Simultaneous Localization and Mapping Problem*. AAAI.
- Thrun, S., Burgard, W., & Fox, D. (2005). *Probabilistic Robotics*. Chapter 13.
- [GMapping (ROS)](http://wiki.ros.org/gmapping)

## 学习笔记

> 待补充……
