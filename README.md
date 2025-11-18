## sam_phd_project
## Portrait and Oil Painting Style Fusion Tool: User Guide

This project uses SAM (Segment Anything Model) to segment portraits and combines PHDNet to naturally fuse portraits with oil painting backgrounds, generating artistically styled composite images. Below are the detailed operating steps.


## Project Overview
**Function**：Input a portrait image and an oil painting background to automatically segment the portrait and harmoniously fuse it with the oil painting style.

**Core Technologies:**：
- SAM：Precisely segments the portrait area (generates masks).
- PHDNet：Optimizes the color and texture consistency between the portrait and the oil painting background for natural fusion.
## Weight Download
Download pre-trained VGG19 from [Baidu Cloud](https://pan.baidu.com/s/1HljOE-4Q2yUeeWmteu0nNA) (access code: pc9y) or [Dropbox](https://www.dropbox.com/scl/fi/vmi4vsg7og41xy8y20j8j/vgg_normalised.pth?rlkey=mbf24da9ac4fnyig1qbkgeem8&st=fjt3274i&dl=0).

Our pre-trained model is available on [Baidu Cloud](https://pan.baidu.com/s/1D6iAS6Sli1QggLp-E9EvyQ) (access code: po7q) or [Dropbox](https://www.dropbox.com/scl/fi/frud0136kx3jizjdkpte0/latest_net_G.pth?rlkey=evhxja7g5vi8ageq7gqhatsxs&st=a1ai0zu5&dl=0).

## Project Structure
```plaintextplaintext
segment_harmonize_project/
├── models/                  
│   ├── segment-anything/    # SAM official code
│   └── PHDNet/  # PHDNet
├── checkpoints/     # Weight storage location       
│   ├── sam_vit_h_4b8939.pth  
│   └── vgg_normalised.pth
│   └── latest_net_G.pth
│   └── yolov8n.pt
├── Input_Data/                  
│   ├── portraits        # Original portrait images (input)
│   ├── paintings/    # Oil painting backgrounds (input)
├── Output_Results/    
│
└──  requirements.txt
└──  pipeline.py
└──  main.py      
```
## Prerequisites
- Operating System: Linux/macOS/Windows (Linux recommended for more stable GPU support)
- Python Version: 3.8+
- Dependent Libraries: PyTorch (1.10+), OpenCV, NumPy, etc. (see installation steps below)
- Hardware: Recommended: NVIDIA GPU (VRAM ≥8GB, CUDA-supported for accelerated inference)
## Install Dependent Libraries
```plaintextplaintext
pip install -r requirements.txt
```
## Usage Steps
1. Prepare Test Images
Place the following in the Input_Data/ folder:
Portrait image: Named portrait.jpg (Recommendation: Clear subject, simple background, resolution ≥500x500)
Oil painting background: Named starry_night.jpg (Recommendation: Oil painting style, e.g., works by Van Gogh or Monet, resolution close to the portrait image)
2. Run the Test Script
 ```plaintextplaintext
python main.py
```
After successful execution, the output will be: Harmonized result saved to Output_Results/portrait_in_painting.jpg.
## 测试结果
The generated Output_Results/portrait_in_painting.jpg is the fusion result. After the portrait is segmented, it is harmoniously fused with the oil painting background in terms of color and texture, presenting a unified artistic style.
## Reference Resources
https://github.com/facebookresearch/segment-anything

https://github.com/bcmi/PHDNet-Painterly-Image-Harmonization
