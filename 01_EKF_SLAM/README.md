# 01 EKF-SLAM（扩展卡尔曼滤波 SLAM）

## 简介

EKF-SLAM 是最经典的 SLAM 算法之一，使用**扩展卡尔曼滤波器（Extended Kalman Filter）**同时估计机器人位姿与路标（landmark）位置。

## 核心思路

1. **状态向量**：将机器人位姿 $(x, y, \theta)$ 与所有路标坐标拼接成一个大的状态向量。
2. **预测步（Prediction）**：根据运动模型将状态均值和协方差向前传播。
3. **更新步（Update）**：当观测到路标时，用观测模型修正状态估计。

## 优缺点

| 优点 | 缺点 |
|------|------|
| 理论简洁，易于理解 | 状态向量随路标数量线性增长，计算复杂度 O(n²) |
| 在高斯噪声假设下最优 | 线性化误差导致非线性场景下精度下降 |
| 实时性较好（小规模地图）| 不适合大规模地图 |

## 算法流程

```
初始化状态向量与协方差矩阵
循环：
    1. 预测：x̂ = f(x̂, u)，P = F·P·Fᵀ + Q
    2. 对每个观测 z_i：
       a. 计算期望观测 ẑ_i = h(x̂)
       b. 计算卡尔曼增益 K = P·Hᵀ·(H·P·Hᵀ + R)⁻¹
       c. 更新状态 x̂ = x̂ + K·(z_i - ẑ_i)
       d. 更新协方差 P = (I - K·H)·P
```

## 参考论文 / 资料

- Smith, R., Self, M., & Cheeseman, P. (1990). *Estimating Uncertain Spatial Relationships in Robotics*.
- Thrun, S., Burgard, W., & Fox, D. (2005). *Probabilistic Robotics*. Chapter 10.

## 学习笔记

> 待补充……
