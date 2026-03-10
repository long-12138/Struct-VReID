# Struct-VReID: Semantics-Guided Visual Grounding for Occluded Text-to-Video Person Re-identification

[![PWC](https://img.shields.io/endpoint.svg?url=https://paperswithcode.com/badge/struct-vreid-semantics-guided-visual/text-to-video-person-re-identification-on)](https://paperswithcode.com/sota/text-to-video-person-re-identification-on)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Official PyTorch implementation of the paper **"Struct-VReID: Semantics-Guided Visual Grounding for Occluded Text-to-Video Person Re-identification"**. 

> **Authors:** Rui Sun, Yi Long, Jicheng Shen, Jingjing Wu, Wei Jia

## 💡 Introduction

Existing Text-to-Video Person Re-identification (T2V ReID) methods are often constrained by coarse global matching paradigms, making them highly susceptible to severe visual noise and occlusions. To bridge this gap, we propose **Struct-VReID**, a novel framework that advances the paradigm from global matching to structure-aware fine-grained grounding. 

Struct-VReID introduces a **Hierarchical Semantic Parsing (LLM-HSP)** module to decompose unstructured text into a semantic tree. Guided by this topology, our **Semantics-Guided Visual Grounding (SGVG)** mechanism actively searches for visible regions across the spatio-temporal domain to filter out occlusion noise. Finally, a **Multi-Granularity Structural Consistency Alignment (MSCA)** objective ensures geometric and semantic correspondence between retrieved video parts and descriptions via an explicit geometric centroid constraint.

![Architecture Diagram](figures/architecture.png) 

## 🏆 Main Results

Extensive experiments on TVPReid benchmarks demonstrate the superiority of Struct-VReID, especially under severe occlusions and cross-domain Zero-Shot generalization scenarios.

### In-Domain Performance

| Dataset | Rank-1 | Rank-5 | Rank-10 | mAP | MdR |
| :--- | :---: | :---: | :---: | :---: | :---: |
| **TVPReid-PRID** | **66.55%** | 89.79% | 97.54% | 76.87% | 1.00 |
| **TVPReid-iLIDs** | **40.67%** | 66.00% | 82.67% | 53.59% | 3.00 |
| **TVPReid-Duke** | **51.58%** | 78.36% | 84.08% | 63.74% | 1.00 |

### Zero-Shot Cross-Dataset Generalization (Rank-1)

| Source \ Target | TVPReid-PRID | TVPReid-iLIDs | TVPReid-Duke |
| :--- | :---: | :---: | :---: |
| **TVPReid-PRID** | - | 20.67% | 12.52% |
| **TVPReid-iLIDs** | 13.38% | - | 4.31% |
| **TVPReid-Duke** | **30.63%** | **21.33%** | - |

## 📂 Data Preparation
Please download the TVPReid datasets (PRID, iLIDs, Duke) from the official sources. Organize the directory structure as follows:

```bash
data/
├── TVPReid-PRID/
├── TVPReid-iLIDs/
└── TVPReid-Duke/
```

## 🔍 Evaluation & Zero-Shot Generalization
To evaluate the trained model, we provide a robust testing script cross_test.py that automatically filters out mismatched classifier heads for safe Cross-Domain Evaluation.

```bash
# Example: Evaluate Duke-trained model on PRID dataset
python cross_test.py 
```

## 🙏 Acknowledgements
We sincerely thank the open-source communities and the authors of [CLIP](https://github.com/openai/CLIP) and [IRRA](https://github.com/anosorae/IRRA) for their brilliant foundational works.

## ⚙️ Installation

```bash
# Clone the repository
git clone [https://github.com/long-12138/Struct-VReID.git](https://github.com/long-12138/Struct-VReID.git)
cd Struct-VReID

# Create a conda environment
conda create -n tvpreid python=3.10
conda activate tvpreid

# Install PyTorch (Tested on PyTorch 2.0+ and CUDA 11.8)
pip install torch torchvision torchaudio --index-url [https://download.pytorch.org/whl/cu118](https://download.pytorch.org/whl/cu118)

# Install dependencies
pip install -r requirements.txt
pip install opencv-python matplotlib# Struct-VReID: Semantics-Guided Visual Grounding for Occluded Text-to-Video Person Re-identification
