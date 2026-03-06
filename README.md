# ComfyUI-PerfectPixel 👾

**⚠️ COPYRIGHT NOTICE & DISCLAIMER ⚠️**
The core algorithm files (`perfect_pixel.py` and `perfect_pixel_noCV2.py`) in this repository are strictly the intellectual property of **[theamusing]**. 
Currently, the original repository does not have an explicit open-source license. This repository is created entirely out of respect for the author's brilliant work and solely to provide a ComfyUI wrapper interface for the community. I claim no ownership over the underlying grid-detection and pixel-refinement algorithms.
If the original author wishes for this wrapper to be taken down, I will comply immediately.

Original Repository: [https://github.com/theamusing/perfectPixel](https://github.com/theamusing/perfectPixel)

A ComfyUI custom node that refines and quantizes messy AI-generated pixel art into clean, perfect, and grid-aligned pixels.

This is a perfect node wrapper for the [theamusing/perfectPixel](https://github.com/theamusing/perfectPixel) algorithm in ComfyUI. It is specifically designed to fix "pseudo-pixel" issues in AI-generated pixel art, such as blurry edges, misaligned grids, and color noise.

## ✨ Features
- **Auto Grid Detection**: Automatically calculates the original grid of the pixel art using FFT and gradient detection.
- **Majority/Center Sampling**: Eliminates gradients and color noise, restoring the purest pixel blocks.
- **Dual Backend**: Supports automatic switching between a high-performance OpenCV backend and a lightweight pure NumPy backend.
- **Nearest Scaling**: Automatically uses nearest-neighbor interpolation to losslessly upscale the processed result back to high-definition.

<img width="1436" height="930" alt="Node Interface" src="https://github.com/user-attachments/assets/97f21d20-5433-4ed6-a05c-8c30be80b153" />

## 🖼️ Showcase

| Before (AI-Generated Pseudo-Pixels) | After (Refined by Perfect Pixel) |
| :---: | :---: |
| <img src="https://github.com/user-attachments/assets/e2ae6f14-251b-4ac7-b700-1feb94f3e7f2" width="400"> | <img src="https://github.com/user-attachments/assets/35620671-1d56-4288-a4b5-20e8cd1abebf" width="400"> |
| <img src="https://github.com/user-attachments/assets/1314f1b5-c2de-4509-beba-d34480331ae0" width="400"> | <img src="https://github.com/user-attachments/assets/014d3c40-6df3-4927-a38b-3e3dca4ff16d" width="400"> |
| <img src="https://github.com/user-attachments/assets/46b66a16-b222-40de-a7b1-c88ab778332d" width="400"> | <img src="https://github.com/user-attachments/assets/661cc39b-249b-43e2-b934-a9f8167a1cbd" width="400"> |
| <img src="https://github.com/user-attachments/assets/9dcf2f27-8644-4f79-821e-12fce8be2a48" width="400"> | <img src="https://github.com/user-attachments/assets/1efb60b1-4609-4186-a22c-12fce8be2a48" width="400"> |
| <img src="https://github.com/user-attachments/assets/8a3b0b76-921c-449a-892f-7b515124cb58" width="400"> | <img src="https://github.com/user-attachments/assets/a21d8c6e-59fb-4dfb-9a7f-2e4124ad2d96" width="400"> |

## ⚙️ Installation
1. Navigate to your ComfyUI `custom_nodes` directory.
2. Run the command: `git clone https://github.com/AchengOoO/ComfyUI-PerfectPixel.git`
3. Enter the cloned folder and run `pip install -r requirements.txt` to install the OpenCV dependencies.
4. Restart ComfyUI.

## 🤝 Credits

Core algorithm is created by [theamusing/perfectPixel](https://github.com/theamusing/perfectPixel).

## 🛠️ Usage

After loading the node in ComfyUI, follow these steps to connect and configure it:

1. **Add the Node**: Double-click the canvas and search for `PerfectPixel`, or find it in the right-click menu under `image/postprocessing`.
2. **Connect the Image**: Connect your AI-generated pixel art (with noise or blurry edges) to the `image` input.
3. **Configure Parameters**:
   - **`sampling`**: 
     - `Majority Cluster` (Recommended): Uses K-Means clustering to perfectly eliminate noise and transitional colors within the grid.
     - `Center Sample`: Directly extracts the center pixel of the grid. This is the fastest method.
   - **`export_scale`**: The default value is `4`. Since the algorithm extracts a very small, pure pixel grid (e.g., 64x64), this parameter automatically uses "Nearest-Neighbor" interpolation to losslessly scale it back to a high-definition image (e.g., 256x256), ensuring razor-sharp edges.
   - **`backend`**: It is highly recommended to manually select the **`OpenCV Backend`** to enable C++ underlying acceleration. If OpenCV is not installed in your environment, you can choose the `Lightweight Backend`.
