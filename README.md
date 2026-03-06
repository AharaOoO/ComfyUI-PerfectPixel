# ComfyUI-PerfectPixel 👾

**⚠️ COPYRIGHT NOTICE & DISCLAIMER ⚠️**
The core algorithm files (`perfect_pixel.py` and `perfect_pixel_noCV2.py`) in this repository are strictly the intellectual property of **[theamusing]**. 
Currently, the original repository does not have an explicit open-source license. This repository is created entirely out of respect for the author's brilliant work and solely to provide a ComfyUI wrapper interface for the community. I claim no ownership over the underlying grid-detection and pixel-refinement algorithms.
If the original author wishes for this wrapper to be taken down, I will comply immediately.

Original Repository: [https://github.com/theamusing/perfectPixel](https://github.com/theamusing/perfectPixel)
A ComfyUI custom node that refines and quantizes messy AI-generated pixel art into clean, perfect, and grid-aligned pixels.

这是 [theamusing/perfectPixel](https://github.com/theamusing/perfectPixel) 算法在 ComfyUI 中的完美节点封装版本。专门用于修复 AI 生成的像素画中边缘模糊、网格不对齐、杂色等“伪像素”问题。

## Features (功能)
- **Auto Grid Detection**: 自动通过 FFT 和梯度检测推算像素画的原始网格。
- **Majority/Center Sampling**: 消除渐变和杂色，还原最纯净的像素色块。
- **Dual Backend**: 支持 OpenCV 高性能加速后端与纯 NumPy 轻量级后端自动切换。
- **Nearest Scaling**: 处理后自动使用最近邻插值无损放大回高清大图。
- 
<img width="1436" height="930" alt="Image" src="https://github.com/user-attachments/assets/97f21d20-5433-4ed6-a05c-8c30be80b153" />

## 🖼️ Showcase (效果展示)

| Before (AI 生成的伪像素图) | After (Perfect Pixel 提纯后) |
| :---: | :---: |
| <img src="https://github.com/user-attachments/assets/35620671-1d56-4288-a4b5-20e8cd1abebf" width="400"> | <img src="https://github.com/user-attachments/assets/014d3c40-6df3-4927-a38b-3e3dca4ff16d" width="400"> |
| <img src="https://github.com/user-attachments/assets/1314f1b5-c2de-4509-beba-d34480331ae0" width="400"> | <img src="https://github.com/user-attachments/assets/661cc39b-249b-43e2-b934-a9f8167a1cbd" width="400"> |
| <img src="https://github.com/user-attachments/assets/46b66a16-b222-40de-a7b1-c88ab778332d" width="400"> | <img src="https://github.com/user-attachments/assets/1efb60b1-4609-4186-a22c-12f1996a0565" width="400"> |
| <img src="https://github.com/user-attachments/assets/9dcf2f27-8644-4f79-821e-12fce8be2a48" width="400"> | <img src="https://github.com/user-attachments/assets/a21d8c6e-59fb-4dfb-9a7f-2e4124ad2d96" width="400"> |
| <img src="https://github.com/user-attachments/assets/8a3b0b76-921c-449a-892f-7b515124cb58" width="400"> | <img src="https://github.com/user-attachments/assets/e2ae6f14-251b-4ac7-b700-1feb94f3e7f2" width="400"> |

## Installation (安装)
1. 进入 ComfyUI 的 `custom_nodes` 目录。
2. `git clone https://github.com/AchengOoO/ComfyUI-PerfectPixel.git`
3. 进入文件夹，运行 `pip install -r requirements.txt` 安装 OpenCV 依赖。
4. 重启 ComfyUI。

## Credits

Core algorithm is created by [theamusing/perfectPixel](https://github.com/theamusing/perfectPixel).

## 🛠️ Usage (使用指南)

在 ComfyUI 中加载节点后，您可以按照以下步骤进行连接和配置：

1. **添加节点**：双击画布搜索 `PerfectPixel`，或者在右键菜单 `image/postprocessing` 目录下找到它。
2. **连接图像**：将 AI 生成的（带有杂色或边缘模糊的）像素画连接到 `image` 输入端。
3. **参数配置**：
   - **`sampling` (采样方法)**: 
     - `Majority Cluster` (推荐)：使用 K-Means 聚类，能完美消除格子内的杂色和过渡色。
     - `Center Sample`：直接提取格子中心像素，速度最快。
   - **`export_scale` (导出缩放比例)**: 默认值为 `4`。由于算法会提取出极小的纯净像素网格（如 64x64），此参数会自动使用“最近邻插值 (Nearest)”将其无损放大回高清大图（如 256x256），保证边缘如刀切般锐利。
   - **`backend` (运算后端)**: 强烈建议手动选择 **`OpenCV Backend`** 以开启 C++ 底层加速。若环境未安装 OpenCV，可选择 `Lightweight Backend`。

---






