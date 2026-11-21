<!--
"A Little Bit of Everything" 版：自我介绍 + 项目 + 技术栈 + GitHub 统计 + 社交入口。
仓库：https://github.com/RadiantForever/RadiantForever

以后有博客/知乎，直接加到「🌏 Elsewhere」一节。
-->

<div align="center">

<img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=600&size=22&duration=2800&pause=900&color=2F81F7&center=true&vCenter=true&width=700&lines=Robotics+%C2%B7+Motion+Control+%C2%B7+ROS2;Legged+%26+wheel-legged+locomotion;Train+in+simulation%2C+run+it+on+hardware" alt="typing" />

# Haihong Qiu · 邱海宏

[![Bilibili](https://img.shields.io/badge/Bilibili-475529500-00A1D6?style=flat-square&logo=bilibili&logoColor=white)](https://space.bilibili.com/475529500)
[![Email](https://img.shields.io/badge/Email-radiant__heart@163.com-EA4335?style=flat-square&logo=gmail&logoColor=white)](mailto:radiant_heart@163.com)
![Guangzhou](https://img.shields.io/badge/Guangzhou-China-6E7781?style=flat-square&logo=googlemaps&logoColor=white)
![Profile views](https://komarev.com/ghpvc/?username=RadiantForever&style=flat-square&color=6E7781&label=views)

</div>

## 🚀 About

- 🎓 广东工业大学 · 大三本科生
- 🎯 目标：机器人运动控制工程师 / 机器人系统工程师
- 📚 正在学：ROS 2、强化学习
- 📫 联系方式：radiant_heart@163.com · [B 站](https://space.bilibili.com/475529500)

## 🦿 Featured work

<table align="center">
  <tr>
    <td align="center" width="50%">
      <img src="https://raw.githubusercontent.com/RadiantForever/supermimic_wheelbipe/main/docs/gifs/spin_leg_wz10.gif" width="380" alt="in-place yaw at 10 rad/s while changing leg height"><br>
      <sub><b>原地偏航 + 变腿</b> · 10 rad/s · 8 cm</sub>
    </td>
    <td align="center" width="50%">
      <img src="https://raw.githubusercontent.com/RadiantForever/supermimic_wheelbipe/main/docs/gifs/fwd_leg_vx15.gif" width="380" alt="forward 1.5 m/s while changing leg height"><br>
      <sub><b>前进 + 变腿</b> · 1.5 m/s</sub>
    </td>
  </tr>
  <tr>
    <td align="center" width="50%">
      <img src="https://raw.githubusercontent.com/RadiantForever/supermimic_wheelbipe/main/docs/gifs/spin_wz10.gif" width="380" alt="in-place yaw at 10 rad/s"><br>
      <sub><b>原地偏航</b> · 10.21 rad/s</sub>
    </td>
    <td align="center" width="50%">
      <img src="https://raw.githubusercontent.com/RadiantForever/supermimic_wheelbipe/main/docs/gifs/leg_static.gif" width="380" alt="leg height sweeping 0.20 to 0.28 m"><br>
      <sub><b>变腿高</b> · 0.20 – 0.28 m</sub>
    </td>
  </tr>
</table>

<p align="center">
  <sub>四段均来自同一检查点 <code>wb_final</code></sub>
</p>

### [supermimic_wheelbipe](https://github.com/RadiantForever/supermimic_wheelbipe)

**一个 6 维动作的单策略，同时控住前进速度、原地偏航和腿高。**

训练不用 PPO，而是三段循环：在 Isaac Lab 里采样短指令序列 → 在 buffer 上拟合多步**可微世界模型**
→ 在想象 rollout 中用 **BPTT** 同时优化 actor 与 critic，并周期性刷新 buffer。

| | |
|---|---|
| **1.40 m/s** | 前进速度（跟踪误差 0.01） |
| **10.21 rad/s** | 原地偏航 ≈ 1.6 圈/秒 |
| **8 cm** | 腿高行程（0.20 – 0.28 m） |
| **0 / 16** | 16 条指令评测摔倒次数，归一化回报 0.983 |
| **4096 envs** | 单卡 RTX 4090，5570 env-step/s，17.8 GB |

指令可组合：前进 + 变腿、偏航 + 变腿、零速下腿高按 2 s 周期往复。

[![Code](https://img.shields.io/badge/Code-%E2%86%97-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/RadiantForever/supermimic_wheelbipe)
[![Video](https://img.shields.io/badge/2s%20demo-Bilibili-00A1D6?style=flat-square&logo=bilibili&logoColor=white)](https://www.bilibili.com/video/BV1haxM6CEGm/)
[![Checkpoint](https://img.shields.io/badge/Checkpoint-27.7%20MB%20policy-2F81F7?style=flat-square&logo=github&logoColor=white)](https://github.com/RadiantForever/supermimic_wheelbipe/releases/tag/ckpt-v1)
![License](https://img.shields.io/badge/MIT-3DA639?style=flat-square)

## 🛠 Tech stack

> **Robotics & learning**
>
> ![ROS 1](https://img.shields.io/badge/ROS%201-22314E?style=flat-square&logo=ros&logoColor=white)
> ![ROS 2](https://img.shields.io/badge/ROS%202-22314E?style=flat-square&logo=ros&logoColor=white)
> ![Isaac Lab](https://img.shields.io/badge/Isaac%20Lab-76B900?style=flat-square&logo=nvidia&logoColor=white)
> ![Isaac Sim](https://img.shields.io/badge/Isaac%20Sim-76B900?style=flat-square&logo=nvidia&logoColor=white)
> ![MuJoCo](https://img.shields.io/badge/MuJoCo-1F6FEB?style=flat-square)
> ![Gazebo](https://img.shields.io/badge/Gazebo-F58113?style=flat-square)
> ![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat-square&logo=pytorch&logoColor=white)

> **Languages**
>
> ![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
> ![C](https://img.shields.io/badge/C-A8B9CC?style=flat-square&logo=c&logoColor=white)
> ![C++](https://img.shields.io/badge/C++-00599C?style=flat-square&logo=cplusplus&logoColor=white)
> ![Bash](https://img.shields.io/badge/Bash-4EAA25?style=flat-square&logo=gnubash&logoColor=white)

> **Tooling**
>
> ![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat-square&logo=linux&logoColor=black)
> ![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
> ![Git](https://img.shields.io/badge/Git-F05032?style=flat-square&logo=git&logoColor=white)
> ![CMake](https://img.shields.io/badge/CMake-064F8C?style=flat-square&logo=cmake&logoColor=white)

## 🌏 Elsewhere

- 📺 B 站：[space.bilibili.com/475529500](https://space.bilibili.com/475529500)
- 📬 邮箱：radiant_heart@163.com

<div align="center">
<sub>Last updated: 2026-11</sub>
</div>
