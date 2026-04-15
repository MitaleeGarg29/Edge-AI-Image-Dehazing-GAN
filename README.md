# Edge-AI-Image-Dehazing-GAN
Parameter-efficient GAN (Tiramisu architecture) for real-time dehazing. Optimized for NVIDIA Jetson Nano deployment via TensorRT. Based on our IEEE TENSYMP research.

# 🌫️ Real-Time Image Dehazing for Autonomous Systems
### Optimized GAN for Edge Deployment (NVIDIA Jetson Nano)

[![IEEE Publication](https://img.shields.io/badge/IEEE-Publication-blue)](https://ieeexplore.ieee.org/document/9230685)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## 💡 The Problem
Autonomous vehicles rely heavily on clear visual input. However, haze and fog scatter light, leading to a loss of contrast and dangerous sensor failure. While state-of-the-art models solve this, they are often too heavy (200MB+) to run in real-time on the embedded hardware actually found in cars.

## 🛠️ What I Built
[cite_start]As part of my research published in **IEEE TENSYMP 2020**, I engineered a parameter-efficient **Generative Adversarial Network (GAN)** designed specifically for the "Edge." 

### Key Innovation: The "Shrinkage"
* [cite_start]**Architecture:** Utilized a **Tiramisu (Densely Connected)** backbone to maximize feature reuse while keeping parameters low.
* [cite_start]**Loss Function:** Implemented **Wasserstein Loss** to stabilize GAN training and ensure high-quality reconstruction.
* [cite_start]**Hardware Optimization:** Reduced model size from **212MB to 4.2MB** (a 50x reduction!) without sacrificing significant PSNR/SSIM scores.
* [cite_start]**Deployment:** Integrated with **NVIDIA TensorRT** for sub-30ms inference on the **NVIDIA Jetson Nano**[cite: 45, 36].

---

## 📊 Performance Comparison

| Model | Size | Platform | Real-Time? |
| :--- | :--- | :--- | :--- |
| Standard GAN | 212 MB | High-end GPU | No (on edge) |
| **Our Optimized Model** | **4.2 MB** | **NVIDIA Jetson** | **Yes (30+ FPS)** |

---

## 📂 Project Structure
* `/src`: Training scripts and Tiramisu-GAN architecture implementation.
* `/deployment`: TensorRT conversion scripts and Jetson Nano inference code.
* `/samples`: Before-and-after results showing dehazing performance in low-visibility environments.

## 🚀 How to Run
1. **Clone the repo:** `git clone https://github.com/MitaleeGarg29/Edge-AI-Image-Dehazing-GAN`
2. **Install dependencies:** `pip install -r requirements.txt`
3. **Run Inference:** `python src/inference.py --image test_hazy.jpg`

---

## 🎓 Citation & Research
This work was presented at the **IEEE Region 10 Symposium (TENSYMP)**. 
> [cite_start]*Mitalee Garg et al., "Deep Generative Model for Single Dehazing on Embedded Platform," 2020.*
