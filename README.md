## sam_phd_project
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
```
## 前置要求
- 操作系统：Linux/macOS/Windows（推荐 Linux，GPU 支持更稳定）
- Python 版本：3.8+
- 依赖库：PyTorch（1.10+）、OpenCV、NumPy 等（见下文安装步骤）
- 硬件：推荐：NVIDIA GPU（显存≥8GB，支持 CUDA，加速推理)
## 安装依赖库
```plaintextplaintext
# 安装基础依赖# 安装基础依赖
pip install opencv-python numpy torch torchvision matplotlib

# 安装SAM额外依赖
pip install pycocotools onnxruntime

# 安装PHDNet依赖（使用其官方requirements）
pip install -r models/PHDNet-Painterly-Image-Harmonization/requirements.txt
```
## 使用步骤
1. 准备测试图像 准备测试图像
在 images/ 文件夹中放入：
人像图：命名为 portrait.jpg（建议：人物清晰，背景简单，尺寸≥500x500）
油画背景：命名为 starry_night.jpg（建议：油画风格，如梵高、莫奈作品，尺寸与人像图接近）
2. 运行测试脚本
 ```plaintextplaintext
python test.py
```
成功运行后，会输出：协调结果已保存到 images/portrait_in_painting.jpg。
## 测试结果
生成的 images/portrait_in_painting.jpg 为融合结果：人像被分割后，与油画背景在颜色、纹理上协调融合，呈现统一的艺术风格。
## 参考资源
https://github.com/facebookresearch/segment-anything
https://github.com/bcmi/PHDNet-Painterly-Image-Harmonization
