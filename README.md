# sam_phd_project
## 人像与油画风格融合工具：运行指南 人像与油画风格融合工具：运行指南

本项目通过 SAM（Segment Anything Model）分割人像，结合 PHDNet 将人像与油画背景自然融合，生成具有艺术风格的合成图像。以下是详细的运行步骤。本项目通过 SAM（Segment Anything Model）分割人像，结合 PHDNet 将人像与油画背景自然融合，生成具有艺术风格的合成图像。以下是详细的运行步骤。


## 项目简介
**功能**：输入一张人像图和一幅油画背景，自动分割人像并将其与油画风格协调融合。：输入一张人像图和一幅油画背景，自动分割人像并将其与油画风格协调融合。

**核心技术**：：
- SAM：精确分割人像区域（生成掩码）。 SAM：精确分割人像区域（生成掩码）。
- PHDNet：优化人像与油画背景的颜色、纹理一致性，实现自然融合。 PHDNet：优化人像与油画背景的颜色、纹理一致性，实现自然融合。


## 项目结构
```plaintextplaintext
segment_harmonize_project/
├── models/                  # 模型代码库（需克隆）
│   ├── segment-anything/    # SAM官方代码
│   └── PHDNet-Painterly-Image-Harmonization/  # PHDNet官方代码
├── checkpoints/             # 模型权重文件（需下载）
│   ├── sam_vit_h_4b8939.pth  # SAM的ViT-H权重
│   └── phdnet_checkpoint.pth  # PHDNet预训练权重（重命名自latest_net_G.pth）
├── src/                     # 接口封装代码（已提供）
│   ├── sam_interface.py     # SAM人像分割接口
│   ├── phdnet_interface.py  # PHDNet风格协调接口
│   └── combined_interface.py  # 端到端组合接口
├── images/                  # 测试图像（需自行准备）
│   ├── portrait.jpg         # 人像原图（输入）
│   ├── starry_night.jpg     # 油画背景（输入）
│   └── portrait_in_painting.jpg  # 输出结果（自动生成）
└── test.py                  # 测试脚本（运行入口）
``````
