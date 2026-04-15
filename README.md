# Edge-AI-Image-Dehazing-GAN
Parameter-efficient GAN (Tiramisu architecture) for real-time dehazing. Optimized for NVIDIA Jetson Nano deployment via TensorRT. Based on our IEEE TENSYMP research.

# 🌫️ Real-Time Image Dehazing for Autonomous Systems
### Optimized GAN for Edge Deployment (NVIDIA Jetson Nano)

[![IEEE Publication](https://img.shields.io/badge/IEEE-Publication-blue)](https://ieeexplore.ieee.org/document/9230685)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## 💡 The Problem
Autonomous vehicles rely heavily on clear visual input. However, haze and fog scatter light, leading to a loss of contrast and dangerous sensor failure. While state-of-the-art models solve this, they are often too heavy (200MB+) to run in real-time on the embedded hardware actually found in cars.

## 🛠️ What I Built
As part of my research published in **IEEE TENSYMP 2020**, I engineered a parameter-efficient **Generative Adversarial Network (GAN)** designed specifically for the "Edge." 

### Key Innovation: The "Shrinkage"
* **Architecture:** Utilized a **Tiramisu (Densely Connected)** backbone to maximize feature reuse while keeping parameters low.
* **Loss Function:** Implemented **Wasserstein Loss** to stabilize GAN training and ensure high-quality reconstruction.
* **Hardware Optimization:** Reduced model size from **212MB to 4.2MB** (a 50x reduction!) without sacrificing significant PSNR/SSIM scores.
* **Deployment:** Integrated with **NVIDIA TensorRT** for sub-30ms inference on the **NVIDIA Jetson Nano**[cite: 45, 36].

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

---

## 📂 Content
This repository contains code for training, testing and evaluation. Pre trained model will be added soon.
> 1. train.py - You can train the model using this file. Set the different paratemeters like epoch, batch size, learning rate as per your preference.
> 2. test.py - Code for testing the trained model. You can enter the location of testing folder and all the images would be inferenced and saved in different directory.
> 3. utils/PSNR_SSIM.m - MATPLAB code for calculating average PSNR and SSIM values. Displays average values of PSNR and SSIM.
> 4. utils/augmentation.py - Code for data augmentation. Can generate 9 images for one image. Can be useful if dataset is small.
> 5. utils.resizeConcat.py - Code for resizing images to 256*256 and concatenating for training.
> 6. densenet56.py - Code  containing densenet implementation used in the paper.
> 7. TensorRT.ipynb - Notebook for converting keras' .h5 model to TensorRT optimized graph
> 8. JetsonNano.ipynb - Notebook for testing model on Jetson Nano.

---

## 🚀 How to Run
1. **Clone the repo:** `git clone https://github.com/MitaleeGarg29/Edge-AI-Image-Dehazing-GAN`
2. **Install dependencies:** `pip install -r requirements.txt`
3. **Run Inference:** `python src/inference.py --image test_hazy.jpg`

---

## 🎓 Citation & Research
This work was presented at the **IEEE Region 10 Symposium (TENSYMP)**. 
> *Mitalee Garg et al., "Deep Generative Model for Single Dehazing on Embedded Platform," 2020.*

---

## 💡 Acknowledgement
This code is based on [pix2pix Tensorflow](https://www.tensorflow.org/tutorials/generative/pix2pix) for training code and [DLology](https://www.dlology.com/blog/how-to-run-keras-model-on-jetson-nano/) for TensorRT and for Inference part.

