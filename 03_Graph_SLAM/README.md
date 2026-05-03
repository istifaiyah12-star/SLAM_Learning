# 03 Graph-based SLAM（图优化 SLAM）

## 简介

图优化 SLAM 是目前主流的后端优化框架。机器人运动轨迹和传感器观测被建模为一个**位姿图（Pose Graph）**或**因子图（Factor Graph）**，通过非线性最小二乘优化求解最优轨迹与地图。

## 核心思路

- **节点（Node）**：机器人位姿（2D: $(x,y,\theta)$，3D: SE(3)）。
- **边（Edge）**：相邻位姿间的相对约束（里程计）或回环检测约束。
- **优化目标**：最小化所有边上的误差平方和（加权），即最大后验估计（MAP）。

## 常用优化库

| 库 | 语言 | 特点 |
|----|------|------|
| [g2o](https://github.com/RainerKuemmerle/g2o) | C++ | 图优化通用框架，SLAM 中广泛使用 |
| [GTSAM](https://gtsam.org/) | C++/Python | 因子图，支持 iSAM2 增量优化 |
| [Ceres Solver](http://ceres-solver.org/) | C++ | Google 出品，通用非线性最小二乘 |
| [Sophus](https://github.com/strasdat/Sophus) | C++ | 李群/李代数工具库 |

## 位姿图优化流程

```
1. 前端（Front-end）：
   - 里程计 / 视觉里程计 / 激光里程计 → 生成节点和里程计边
   - 回环检测 → 生成回环边

2. 后端（Back-end）：
   构建因子图
   非线性最小二乘：
       min Σ eᵢᵀ Ωᵢ eᵢ
   迭代求解（Gauss-Newton / Levenberg-Marquardt）
   → 输出全局一致的位姿图
```

## 回环检测

回环检测是消除累积误差的关键：
- **视觉**：词袋模型（BoW，DBoW2/DBoW3）、NetVLAD
- **激光**：Scan Context、M2DP、点云描述子匹配

## 参考论文 / 资料

- Grisetti, G. et al. (2010). *A Tutorial on Graph-Based SLAM*. IEEE Intelligent Transportation Systems Magazine.
- Kümmerle, R. et al. (2011). *g2o: A General Framework for Graph Optimization*. ICRA.
- Kaess, M. et al. (2012). *iSAM2: Incremental Smoothing and Mapping Using the Bayes Tree*. IJRR.

## 学习笔记

> 待补充……
