<!--
双语版：英文在前，中文在后，逐行对照，不重复区块结构。
仓库：https://github.com/RadiantForever/RadiantForever
-->

<div align="center">

<img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=600&size=22&duration=2800&pause=900&color=2F81F7&center=true&vCenter=true&width=700&lines=Robotics+%C2%B7+Motion+Control+%C2%B7+ROS2;Legged+%26+wheel-legged+locomotion;Train+in+simulation%2C+run+it+on+hardware" alt="typing" />

# Haihong Qiu · 邱海宏

[![Bilibili](https://img.shields.io/badge/Bilibili-475529500-00A1D6?style=flat-square&logo=bilibili&logoColor=white)](https://space.bilibili.com/475529500)
[![Xiaohongshu](https://img.shields.io/badge/Xiaohongshu-FF2442?style=flat-square&logo=xiaohongshu&logoColor=white)](https://www.xiaohongshu.com/user/profile/62dbd953000000001f015c1c)
[![Email](https://img.shields.io/badge/Email-radiant__heart@163.com-EA4335?style=flat-square&logo=gmail&logoColor=white)](mailto:radiant_heart@163.com)
![Guangzhou](https://img.shields.io/badge/Guangzhou-China-6E7781?style=flat-square&logo=googlemaps&logoColor=white)
![Profile views](https://komarev.com/ghpvc/?username=RadiantForever&style=flat-square&color=6E7781&label=views)

</div>

## 🚀 About · 关于

- 🎓 Junior, Guangdong University of Technology · 广东工业大学 大三本科生
- 🎯 Aiming for motion control engineer / robot systems engineer · 目标：机器人运动控制工程师 / 机器人系统工程师
- 📚 Currently learning robot motion control, reinforcement learning and ROS 2 · 正在学：机器人运动控制、强化学习、ROS 2
- 📫 [radiant_heart@163.com](mailto:radiant_heart@163.com) · [Bilibili](https://space.bilibili.com/475529500)

## 🦿 Featured work · 项目

<table align="center">
  <tr>
    <td align="center" width="50%">
      <img src="https://raw.githubusercontent.com/RadiantForever/supermimic_wheelbipe/main/docs/gifs/spin_leg_wz10.gif" width="380" alt="in-place yaw at 10 rad/s while changing leg height"><br>
      <sub><b>Yaw + leg height</b> · 偏航 + 变腿 · 10 rad/s · 8 cm</sub>
    </td>
    <td align="center" width="50%">
      <img src="https://raw.githubusercontent.com/RadiantForever/supermimic_wheelbipe/main/docs/gifs/fwd_leg_vx15.gif" width="380" alt="forward 1.5 m/s while changing leg height"><br>
      <sub><b>Forward + leg height</b> · 前进 + 变腿 · 1.5 m/s</sub>
    </td>
  </tr>
  <tr>
    <td align="center" width="50%">
      <img src="https://raw.githubusercontent.com/RadiantForever/supermimic_wheelbipe/main/docs/gifs/spin_wz10.gif" width="380" alt="in-place yaw at 10 rad/s"><br>
      <sub><b>In-place yaw</b> · 原地偏航 · 10.21 rad/s</sub>
    </td>
    <td align="center" width="50%">
      <img src="https://raw.githubusercontent.com/RadiantForever/supermimic_wheelbipe/main/docs/gifs/leg_static.gif" width="380" alt="leg height sweeping 0.20 to 0.28 m"><br>
      <sub><b>Leg height</b> · 变腿高 · 0.20 – 0.28 m</sub>
    </td>
  </tr>
</table>

<p align="center">
  <sub>Four clips from one checkpoint <code>wb_final</code> · 四段均来自同一检查点</sub>
</p>

### [supermimic_wheelbipe](https://github.com/RadiantForever/supermimic_wheelbipe)

**One 6-D action policy holding forward velocity, in-place yaw and leg height at the same time.**
**一个 6 维动作的单策略，同时控住前进速度、原地偏航和腿高。**

Trained without PPO, in three repeating stages: sample short command sequences in Isaac Lab → fit a multi-step differentiable world model on the buffer → optimize actor and critic by BPTT through imagined rollouts, refreshing the buffer periodically.

训练不用 PPO，而是三段循环：在 Isaac Lab 里采样短指令序列 → 在 buffer 上拟合多步可微世界模型 → 在想象 rollout 中用 BPTT 同时优化 actor 与 critic，并周期性刷新 buffer。

| | |
|---|---|
| **1.40 m/s** | Forward velocity · 前进速度（跟踪误差 0.01） |
| **10.21 rad/s** | In-place yaw ≈ 1.6 rev/s · 原地偏航 |
| **8 cm** | Leg-height travel, 0.20 – 0.28 m · 腿高行程 |
| **0 / 16** | Falls over 16 commands, normalized return 0.983 · 16 条指令评测摔倒数 |
| **4096 envs** | Single RTX 4090, 5570 env-step/s · 单卡训练吞吐 |

Commands compose: forward + height, yaw + height, and a 2 s leg-height oscillation at zero velocity.

指令可组合：前进 + 变腿、偏航 + 变腿、零速下腿高按 2 s 周期往复。

[![Code](https://img.shields.io/badge/Code-%E2%86%97-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/RadiantForever/supermimic_wheelbipe)
[![Video](https://img.shields.io/badge/2s%20demo-Bilibili-00A1D6?style=flat-square&logo=bilibili&logoColor=white)](https://www.bilibili.com/video/BV1haxM6CEGm/)
[![Checkpoint](https://img.shields.io/badge/Checkpoint-27.7%20MB%20policy-2F81F7?style=flat-square&logo=github&logoColor=white)](https://github.com/RadiantForever/supermimic_wheelbipe/releases/tag/ckpt-v1)
![License](https://img.shields.io/badge/MIT-3DA639?style=flat-square)

## 🛠 Tech stack · 技术栈

> **Robotics & learning · 机器人与学习**
>
> ![ROS 1](https://img.shields.io/badge/ROS%201-22314E?style=flat-square&logo=ros&logoColor=white)
> ![ROS 2](https://img.shields.io/badge/ROS%202-22314E?style=flat-square&logo=ros&logoColor=white)
> ![Isaac Lab](https://img.shields.io/badge/Isaac%20Lab-76B900?style=flat-square&logo=nvidia&logoColor=white)
> ![Isaac Sim](https://img.shields.io/badge/Isaac%20Sim-76B900?style=flat-square&logo=nvidia&logoColor=white)
> ![MuJoCo](https://img.shields.io/badge/MuJoCo-1F6FEB?style=flat-square)
> ![Gazebo](https://img.shields.io/badge/Gazebo-F58113?style=flat-square)
> ![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat-square&logo=pytorch&logoColor=white)

> **Languages · 语言**
>
> ![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
> ![C](https://img.shields.io/badge/C-A8B9CC?style=flat-square&logo=c&logoColor=white)
> ![C++](https://img.shields.io/badge/C++-00599C?style=flat-square&logo=cplusplus&logoColor=white)
> ![Bash](https://img.shields.io/badge/Bash-4EAA25?style=flat-square&logo=gnubash&logoColor=white)

> **Tooling · 工具**
>
> ![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat-square&logo=linux&logoColor=black)
> ![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
> ![Git](https://img.shields.io/badge/Git-F05032?style=flat-square&logo=git&logoColor=white)
> ![CMake](https://img.shields.io/badge/CMake-064F8C?style=flat-square&logo=cmake&logoColor=white)

## 📊 This GitHub · 数据

<div align="center">

<img src="https://github-readme-stats.vercel.app/api?username=RadiantForever&show_icons=true&hide_title=true&hide_rank=true&hide_border=true&hide=commits,prs,issues,contribs&theme=transparent" alt="stars" />

</div>

## 🌏 Elsewhere · 其他

- 📺 Bilibili · B 站：[space.bilibili.com/475529500](https://space.bilibili.com/475529500)
- 📕 Xiaohongshu · 小红书：[62dbd953000000001f015c1c](https://www.xiaohongshu.com/user/profile/62dbd953000000001f015c1c)
- 📬 Email · 邮箱：[radiant_heart@163.com](mailto:radiant_heart@163.com)

<div align="center">
<sub>Last updated: 2026-11</sub>
</div>
