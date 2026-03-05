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

## Installation (安装)
1. 进入 ComfyUI 的 `custom_nodes` 目录。
2. `git clone https://github.com/您的用户名/ComfyUI-PerfectPixel.git`
3. 进入文件夹，运行 `pip install -r requirements.txt` 安装 OpenCV 依赖。
4. 重启 ComfyUI。

## Credits
Core algorithm is created by [theamusing/perfectPixel](https://github.com/theamusing/perfectPixel).