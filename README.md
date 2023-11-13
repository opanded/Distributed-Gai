[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
# Distributed-MADDPG
基于批处理数据优先级的MADDPG分布式多智能体协作算法

## Distributed Multi-Agent Architecture
<p align="center">
  <img src="https://github.com/namidairo777/Distributed-MADDPG/blob/master/imgs/architecture.PNG">
</p>

## Introduction
本文主要研究多智能体协作问题。我们提出了一种由三部分组成的方法：
1. 相关研究基础 - MADDPG
算法来自 [Multi-Agent Actor-Critic for Mixed Cooperative-Competitive Environments](https://arxiv.org/pdf/1706.02275.pdf)
2. 批处理数据的优先级
为了在不失去多样性的情况下优化一步更新，我们将批处理数据分为几个部分，并对这些批处理进行优先级排序。使用损失最大的批处理数据进行一步更新。
3. Distributed 多智能体 Architecture
与A3C算法类似，我们在工作中采用了Master和Multi-Worker架构。

## Experiment
### Implementation
- Keras 2.1.2 （tensorflow 1.4 as backend）
- mpi4py
- Python 3.6
- CUDA 8.0 + cuDNN 6.0

### Environment
- 修改后的原始环境 from [OpenAI](https://github.com/openai/multiagent-particle-envs)
	- Fixed landmark
	- Border
<p align="center">
  <img width="300" src="https://github.com/namidairo777/Distributed-MADDPG/blob/master/imgs/env.png">
</p>

### Neural Network
<p align="center">
  <img width="800" src="https://github.com/namidairo777/Distributed-MADDPG/blob/master/imgs/network.PNG">
</p>

### Result 
<p align="center">
  <img width="600" src="https://github.com/namidairo777/Distributed-MADDPG/blob/master/imgs/result_curve.png">
</p>
<p align="center">
  <img width="400" src="https://github.com/namidairo777/Distributed-MADDPG/blob/master/imgs/result_table.PNG">
</p>

### Learning Progress
- DDPG & MADDPG & PROPOSED
<p align="center">
  <span width="280" style="float:left">
    <img width="280" src="https://github.com/namidairo777/Distributed-MADDPG/blob/master/imgs/ddpg_slow_gif.gif">
  </span>
  <span width="280" style="float:left">
    <img width="280" src="https://github.com/namidairo777/Distributed-MADDPG/blob/master/imgs/maddpg_slow_gif.gif">
  </span>
  <span width="280" style="float:left">
    <img width="280" src="https://github.com/namidairo777/Distributed-MADDPG/blob/master/imgs/proposed_slow_gif.gif">
  </span>
</p>

## How to run this program
使用 MPI 的程序:
- mpiexec -np [worker_number] python mpi-xxx.py
```python
mpiexec -np 4 python mpirun_main.py
```
其他程序:
```python
python xxx.py
```

## Future Work (4 vs 2)
<p align="center">
  <img width="300" src="https://github.com/namidairo777/Distributed-MADDPG/blob/master/imgs/4vs2_slow_gif.gif">
</p>

## Thanks to
- [agakshat's MADDPG implementation repo](https://github.com/agakshat/maddpg)
- [OpenAI baselines](https://github.com/openai/baselines)
- [OpenAI envs](https://github.com/openai/multiagent-particle-envs)
