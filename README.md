# 强化学习
以强化学习的发展过程为主线，通过理论和算法的结合回顾了强化学习的主要内容。首先，是强化学习的理论基础马尔科夫过程。在强化学习的早期，以状态空间，动作空间，状态转移矩阵，折损因子为已知量（model-base），使用动态规划的思想求解最佳策略。基于马尔科夫奖励过程，求解状态价值函数的贝尔曼方程；基于马尔科夫决策过程，求解行为状态价值函数的贝尔曼方程。其中的经典算法是Qlearning（off-policy）和SARSA（on-policy）方法。
[传统的强化学习方法](https://github.com/liuyandong1988/RL_MarvoProcess)无法求解状态空间、行为空间较大，状态转移概率未知的问题（model-less）。基于神经网络的deep-RL，使用利用探索的思想求解。以优化价值函数和策略函数为不同出发点，形成了两大类求解方法：

1. [优化价值函数](https://github.com/liuyandong1988/ReinforcementLearning_ValueOpimization)
以DQN为核心，及其改进技巧 Experience Replay、 Fixed target、double DQN、Dueling DQN等。以TD-error方法更新网络，优化最大行为价值函数，得到最优策略。优点，经验回放大大提高了样本使用率；网络结构特别，擅长处理基于像素--动作类的游戏控制。缺点，无法处理连续动作；训练过程不稳定，容易出现振荡。
2. [策略梯度](https://github.com/liuyandong1988/Policy_gradient)
直接优化策略。SPG，用蒙特卡洛方法评价策略的好坏，需要完整的episode。改进的Actor-Critic每训练一步用Qvalue评价策略的好坏，样本使用率低。OPP进一步改进，N-step思想结合importance sample评价策略。以上三种方法都是把critic的值作为策略梯度的权重，更新Actor网络的。DDPG也是A-C架构，但思路完全不同。DDPG以DQN为核心作为Critic，但网络的输入不仅是环境状态，还有Actor得到的行为。大大提升了样本的利用率。分布式的方法是提升样本利用率的另一思路，A3C和DOPP分别是对Actor-critc和OPP算法的分布式处理。

[![JfdHOI.png](https://s1.ax1x.com/2020/04/27/JfdHOI.png)](https://imgchr.com/i/JfdHOI)


## 环境
tensorflow 2.1.0
tensorflow-probability 0.9.0
tensorlayer 2.2.1
gym 0.17.1