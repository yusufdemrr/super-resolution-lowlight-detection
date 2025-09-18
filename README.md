# Enhancing Low-Light Image Quality for Object Detection Using Super Resolution

This project explores the effectiveness of various deep learning-based super-resolution (SR) models in improving both the visual quality and object detection performance of low-light images. It evaluates how perceptual quality (e.g., SSIM, PSNR) correlates with detection accuracy when used as preprocessing for YOLOv8.

## Models Implemented

- **SRCNN** – Classic 3-layer model for baseline performance.
- **Enhanced SRCNN** – Adds residual blocks for deeper feature extraction.
- **Enhanced SRCNN v2** – Introduces Squeeze-and-Excitation (SE) channel attention.
- **YASRNet** – Combines spatial and channel attention via CBAM with PixelShuffle upsampling.
- **SRCNN Edge** – Uses a hybrid MSE + Laplacian loss to preserve edge details.

## Evaluation Strategy

The super-resolved images were passed into a frozen YOLOv8 detector and compared against:

- Original low-light inputs
- High-light (ground truth) versions
- Super-resolved outputs

Metrics used:
- **SSIM / PSNR** for visual fidelity
- **YOLOv8 Precision, Recall, and Exact Match Accuracy** for detection performance

## Dataset

- **LOLv1 Dataset** for low-light image enhancement.
- Images are used at full resolution for preserving edge structures critical to detection.

## Environment

- Framework: PyTorch
- GPUs: 2× NVIDIA T4 (16 GB VRAM)
- Mixed precision: Disabled
- Training Epochs: 30

## Key Findings

- SR models improve perceptual quality, but not always detection performance.
- High SSIM does not imply high YOLO detection accuracy.
- Models that prioritize **edge preservation** (like SRCNN Edge) are more useful for downstream tasks.

<img width="716" height="489" alt="image" src="https://github.com/user-attachments/assets/40f0f331-4654-4a01-8103-4db2094795ed" />
<img width="706" height="353" alt="image" src="https://github.com/user-attachments/assets/88ddabda-e9cc-4295-8e33-a950f275b756" />


