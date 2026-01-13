<div align="center">
  <img src="logo.png" alt="Dexbotic Logo" width="280"/>

  # 一站式具身智能 VLA 开发工具箱

  [![Paper](https://img.shields.io/badge/Paper-arXiv-b31b1b.svg)](https://arxiv.org/pdf/2510.23511)
  [![Python](https://img.shields.io/badge/Python-3.8%2B-blue)](https://www.python.org/)
  [![Documentation](https://img.shields.io/badge/Docs-Online-success)](https://dexbotic.com/docs/)
  [![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

  <p align="center">
    <strong>预训练 · 微调 · 推理 · 评测</strong><br>
    支持 Pi0、CogACT、OFT、RL 等主流策略
  </p>
</div>

## 简介

**Dexbotic** 旨在为具身智能研究提供一个统一、高效的 VLA（视觉-语言-动作）开发工具箱。它内置了多种主流 VLA 模型的环境配置，用户只需简单的设置即可复现、微调和推理各种前沿算法。

- **开箱即用的 VLA 框架**：以 VLA 模型为核心，集成了具身操作和导航功能，原生支持多种业内领先的策略。
- **强大的预训练基座**：针对 Pi0 和 CogACT 等主流策略，提供了多个基于 Dexbotic 优化的预训练模型。
- **模块化开发架构**：采用“分层配置 + 工厂注册 + 入口分发”的设计模式。用户只需修改配置脚本，即可轻松完成参数修改、模型更换或任务扩展。
- **混合训练支持**：无缝衔接云端与本地环境，支持阿里云、火山引擎等大规模云端集群，同时适配消费级 GPU 进行本地训练。
- **广泛的机器人适配**：针对 UR5、Franka 和 ALOHA 等主流机器人平台，提供了**统一的训练数据格式**，大幅降低数据处理成本。

![](intro.jpeg)

## 🔥 最新动态

- **[2026-01-08]** 🆕 新增 **联合训练 (Co-training)** 能力，支持对 CogACT 模型的动作专家和 LLM 进行联合优化。同时发布适配 **Blackwell GPU** 的专用镜像。
- **[2025-12-29]** 全面支持 **OFT** 和 **Pi0.5** 模型。
- **[2025-10-20]** Dexbotic 正式发布！详情请查阅 [技术报告](https://arxiv.org/pdf/2510.23511) 和 [官方文档](https://dexbotic.com/docs/)。


## 快速开始

我们强烈推荐使用 Docker 进行开发或部署，以获得最佳的使用体验。

### 1. 安装与环境配置

```bash
# 1. 克隆代码仓库
git clone https://github.com/dexmal/dexbotic.git

# 2. 启动 Docker 容器
docker run -it --rm --gpus all --network host \
  -v $(pwd)/dexbotic:/dexbotic \
  dexmal/dexbotic \
  bash

# 3. 激活环境并安装依赖
cd /dexbotic
conda activate dexbotic
pip install -e .
```

<details>
<summary>在 Blackwell GPU 上使用</summary>

对于使用 Blackwell 架构 GPU（例如 B100, RTX 5090）的用户，请使用专用的 Docker 镜像 `dexmal/dexbotic:c130t28`。

**步骤 1：使用 Blackwell 镜像启动 Docker**

```bash
# 1. 使用 Blackwell 镜像启动 Docker
docker run -it --rm --gpus all --network host \
  -v /path/to/dexbotic:/dexbotic \
  dexmal/dexbotic:c130t28 \
  bash

# 2. 激活环境**
cd /dexbotic
pip install -e .
```

</details>

> **系统要求**：Ubuntu 20.04/22.04，推荐使用 RTX 4090、A100 或 H100（训练建议 8 GPU，部署需 1 GPU）。

### 2. 使用指南

- [运行预训练模型](https://dexbotic.com/docs/2.%20Get%20Start.html#_2-run-a-pretrained-model)
- [基于仿真数据训练](https://dexbotic.com/docs/2.%20Get%20Start.html#_3-train-on-provided-simulator-data)
- [测试与评估](https://dexbotic.com/docs/2.%20Get%20Start.html#_4-test-your-trained-model)
- [完整的官方文档](https://dexbotic.com/docs/)


## 基准测试

以下展示了基于 Dexbotic 训练的模型与原始模型在主流仿真环境下的评测结果对比。

![](demo.png)

📊 **查看更多详细评测结果**: [Simulation Results](https://dexbotic.com/docs/7.%20Simulation%20Results.html)

## 未来计划

我们正在积极开发以下新功能，敬请期待：

- 预训练模型：Dexbotic-OFT
- 导航策略：NaVid、NaVILA、StreamVLN

## 支持我们

我们正在不断改进，更多功能即将推出。如果你喜欢这个项目，请在 GitHub 上给我们点一颗星 [![GitHub](https://img.shields.io/github/stars/dexmal/dexbotic?color=5B5BD6)](https://github.com/dexmal/dexbotic)，你的支持是我们前进的动力！

如果 Dexbotic 对你的研究工作有所帮助，请考虑引用我们的技术报告：

```bibtex
@article{dexbotic,
  title={Dexbotic: Open-Source Vision-Language-Action Toolbox},
  author={Dexbotic Contributors},
  journal={arXiv preprint arXiv:2510.23511},
  year={2025}
}
```

## 许可

本项目采用 [MIT 许可证](LICENSE)。
