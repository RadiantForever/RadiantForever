<!--
"A Little Bit of Everything" 版：自我介绍 + 项目 + 技术栈 + GitHub 统计 + 社交入口。
仓库已建：https://github.com/RadiantForever/RadiantForever

唯一待补：博客/知乎/个人站，有的话加到「🌏 Elsewhere」一节。
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

- 🎓 广东工业大学 大三本科生
- 🦿 我做的事：**机器人运动控制** —— 让腿足 / 轮腿机器人在给定指令下稳稳地跑、转、变高度
- 🧠 用的方法：**强化学习**。在仿真里把策略训出来，重点是训得动、控得住、指标可复现
- 🔧 工程侧：**ROS 2**。关心仿真里的策略怎么接到真实机器人上，以及控制栈本身写得好不好维护
- 🧪 喜欢把一条链路从仿真一路跑到实机，中间每一步都能被验证
- 📫 联系方式：radiant_heart@163.com · [B 站](https://space.bilibili.com/475529500)

## 🦿 Featured work

<p align="center">
  <img src="https://raw.githubusercontent.com/RadiantForever/supermimic_wheelbipe/main/docs/gifs/fwd_leg_vx15.gif" alt="wheel-legged robot driving forward at 1.5 m/s while changing leg height" width="760">
</p>
<p align="center">
  <sub><b>Forward 1.5 m/s + leg-height change, one policy.</b> 2.0 s of real-time simulation, no cuts, no speed-up.</sub>
</p>

<table align="center">
  <tr>
    <td align="center" width="50%">
      <img src="https://raw.githubusercontent.com/RadiantForever/supermimic_wheelbipe/main/docs/gifs/spin_wz10.gif" width="360" alt="in-place yaw at 10 rad/s"><br>
      <sub><b>In-place yaw</b> · 10.21 rad/s · 1.6 rev/s</sub>
    </td>
    <td align="center" width="50%">
      <img src="https://raw.githubusercontent.com/RadiantForever/supermimic_wheelbipe/main/docs/gifs/leg_static.gif" width="360" alt="leg height sweeping 0.20 to 0.28 m"><br>
      <sub><b>Leg height</b> · 0.20 – 0.28 m · 8 cm travel</sub>
    </td>
  </tr>
</table>

<p align="center">
  <sub>All clips: same checkpoint <code>wb_final</code> · <a href="https://github.com/RadiantForever/supermimic_wheelbipe/blob/main/docs/gifs/spin_leg_wz10.gif">one more: yaw + height at the same time</a></sub>
</p>

### [supermimic_wheelbipe](https://github.com/RadiantForever/supermimic_wheelbipe)

**一个 6 维动作的单策略，同时控住前进速度、原地偏航和腿高 —— 轮腿机器人最难的地方是这三件事互相打架。**

控制目标是复合的：加速时腿高要被压住，原地高速偏航时不能摔，变高度时速度不能崩。
训练上没用 PPO，而是三段循环：在 Isaac Lab 里采样短指令序列 → 在 buffer 上拟合多步**可微世界模型**
（成功与失败样本都保留）→ 在想象 rollout 中用 **BPTT** 同时优化 actor 与 critic，并周期性刷新 buffer。
选这条路的原因很实际：**同样的算力预算下，想让策略更快见到更多样的指令组合**。

| | |
|---|---|
| **1.40 m/s** | 前进速度（跟踪误差 0.01） |
| **10.21 rad/s** | 原地偏航 ≈ 1.6 圈/秒 |
| **8 cm** | 腿高行程（0.20 – 0.28 m） |
| **0 / 16** | 16 条指令评测摔倒次数，归一化回报 0.983 |
| **4096 envs** | 单卡 RTX 4090，5570 env-step/s，17.8 GB |

指令可组合：前进 + 变腿、偏航 + 变腿、零速下腿高按 2 s 周期往复。

> **已知限制也写在仓库里**：顶速未达 2–3 m/s 目标；PhysX `replicate_physics=True` 下无法逐 env 随机化摩擦；
> 无 URDF 故无 IK；teacher 信号只混入前 800 轮且缺少「完全不给 teacher」的对照，
> 所以**不声称**「不用老师也能到这个水平」。

[![Code](https://img.shields.io/badge/Code-%E2%86%97-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/RadiantForever/supermimic_wheelbipe)
[![Video](https://img.shields.io/badge/2s%20demo-Bilibili-00A1D6?style=flat-square&logo=bilibili&logoColor=white)](https://www.bilibili.com/video/BV1haxM6CEGm/)
[![Checkpoint](https://img.shields.io/badge/Checkpoint-27.7%20MB%20policy-2F81F7?style=flat-square&logo=github&logoColor=white)](https://github.com/RadiantForever/supermimic_wheelbipe/releases/tag/ckpt-v1)
![License](https://img.shields.io/badge/MIT-3DA639?style=flat-square)

## 🛠 Tech stack

> **Motion control & robotics**
>
> ![ROS 2](https://img.shields.io/badge/ROS%202-22314E?style=flat-square&logo=ros&logoColor=white)
> ![Isaac Lab](https://img.shields.io/badge/Isaac%20Lab-76B900?style=flat-square&logo=nvidia&logoColor=white)
> ![Isaac Sim](https://img.shields.io/badge/Isaac%20Sim-76B900?style=flat-square&logo=nvidia&logoColor=white)
> ![MuJoCo](https://img.shields.io/badge/MuJoCo-1F6FEB?style=flat-square)
> ![Gazebo](https://img.shields.io/badge/Gazebo-F58113?style=flat-square)

> **Learning**
>
> ![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat-square&logo=pytorch&logoColor=white)
> ![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat-square&logo=numpy&logoColor=white)
> ![BPTT](https://img.shields.io/badge/backprop%20through%20time-8A2BE2?style=flat-square)

> **Languages**
>
> ![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
> ![C++](https://img.shields.io/badge/C++-00599C?style=flat-square&logo=cplusplus&logoColor=white)
> ![Bash](https://img.shields.io/badge/Bash-4EAA25?style=flat-square&logo=gnubash&logoColor=white)

> **Tooling**
>
> ![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat-square&logo=linux&logoColor=black)
> ![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
> ![Git](https://img.shields.io/badge/Git-F05032?style=flat-square&logo=git&logoColor=white)
> ![CMake](https://img.shields.io/badge/CMake-064F8C?style=flat-square&logo=cmake&logoColor=white)

## 📊 This GitHub

<div align="center">

<img height="150" src="https://github-readme-stats.vercel.app/api?username=RadiantForever&show_icons=true&hide_title=true&hide_rank=true&hide_border=true&include_all_commits=true&theme=transparent" alt="stats" />
<img height="150" src="https://github-readme-stats.vercel.app/api/top-langs/?username=RadiantForever&layout=compact&langs_count=5&hide_border=true&theme=transparent" alt="langs" />

</div>

## 🌏 Elsewhere

- 📺 **B 站** — [space.bilibili.com/475529500](https://space.bilibili.com/475529500) —— 机器人跑起来的原始录像，不做剪辑调速
- ✍️ 把调参、踩坑和失败的实验整理成文（TODO：放博客/知乎链接）
- 📬 开放交流：腿足 / 轮腿运动控制、RL 训策略、ROS 2 工程，欢迎邮件

<div align="center">
<sub>Last updated: 2026-11 · 数据均来自仓库内可复现的实验记录</sub>
</div>
