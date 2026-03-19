# Struct-TVReID: LLM-Driven Structural Grounding for Text-to-Video Person Re-identification
[![PWC](https://img.shields.io/endpoint.svg?url=https://paperswithcode.com/badge/struct-vreid-semantics-guided-visual/text-to-video-person-re-identification-on)](https://paperswithcode.com/sota/text-to-video-person-re-identification-on)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Official PyTorch implementation of the paper **"Struct-TVReID: LLM-Driven Structural Grounding for Text-to-Video Person Re-identification"**. 

> **Authors:** Rui Sun, Yi Long, Jicheng Shen, Haohao Wang, Jingjing Wu, Wei Jia


## 💡 Introduction
Struct-TVReID introduces a **Hierarchical Semantic Parsing (LLM-HSP)** module to decompose unstructured text into a semantic tree. Guided by this topology, our **Semantics-Guided Visual Grounding (SGVG)** mechanism actively searches for visible regions across the spatio-temporal domain to filter out occlusion noise. Finally, a **Multi-Granularity Structural Consistency Alignment (MSCA)** objective ensures geometric and semantic correspondence between retrieved video parts and descriptions via an explicit geometric centroid constraint.

![Architecture Diagram](figures/Struct-VReID_Safe_Version.png) 

## 🤖 LLM-HSP
Step1.You can choose to deploy the large model locally or use an online large model
Step2.
```bash
# If you wish to use this module 
python process_local_qwen.py 
```

## 🏆 Main Results

Extensive experiments on TVPReid benchmarks demonstrate the superiority of Struct-TVReID, especially under severe occlusions and cross-domain Zero-Shot generalization scenarios.

### In-Domain Performance

| Dataset | Rank-1 | Rank-5 | Rank-10 | mAP | MdR |
| :--- | :---: | :---: | :---: | :---: | :---: |
| **TVPReid-PRID** | **66.55%** | 89.79% | 97.54% | 76.87% | 1.00 |
| **TVPReid-iLIDs** | **40.67%** | 66.00% | 82.67% | 53.59% | 3.00 |
| **TVPReid-Duke** | **51.58%** | 78.36% | 84.08% | 63.74% | 1.00 |

**Table: Robustness evaluation of Struct-TVReID under varying ratios of dynamic spatial occlusion across three benchmarks.**

| **Dataset** | **Noise Ratio** | **Rank-1** | **Rank-5** | **Rank-10** | **mAP** |
| :--- | :---: | :---: | :---: | :---: | :---: |
| **TVPReid-PRID** | 0% (Clean) | 66.55 | 89.79 | 97.54 | 76.87 |
| | 10% | 63.03 | 87.68 | 95.78 | 74.24 |
| | 20% | 55.28 | 86.62 | 92.25 | 68.27 |
| | 30% | 48.59 | 81.69 | 90.85 | 64.06 |
| | 40% | 44.72 | 81.34 | 89.44 | 60.53 |
| **TVPReid-iLIDs** | 0% (Clean) | 40.67 | 82.67 | 89.33 | 53.59 |
| | 10% | 38.00 | 66.00 | 83.33 | 51.53 |
| | 20% | 35.33 | 64.00 | 80.00 | 49.38 |
| | 30% | 37.33 | 65.33 | 76.67 | 50.24 |
| | 40% | 34.00 | 62.00 | 78.00 | 47.40 |
| **TVPReid-Duke** | 0% (Clean) | 51.58 | 84.08 | 78.36 | 63.74 |
| | 10% | 49.67 | 76.37 | 84.83 | 62.03 |
| | 20% | 48.26 | 76.70 | 83.91 | 61.23 |
| | 30% | 45.27 | 74.71 | 82.50 | 58.14 |
| | 40% | 43.28 | 72.14 | 81.18 | 56.52 |

## 📂 Data Preparation
Please download the TVPReid datasets [PRID, iLIDs, Duke](https://github.com/NjtechCVLab/TVPReid-Dataset). Organize the directory structure as follows:

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

We would like to thank the **NjtechCVLab** team for their pioneering work and for providing the [**TVPReid**](https://github.com/NjtechCVLab/TVPReid-Dataset) dataset. 

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
pip install opencv-python matplotlib
