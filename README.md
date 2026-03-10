# Struct-VReID: Semantics-Guided Visual Grounding for Occluded Text-to-Video Person Re-identification

[![PWC](https://img.shields.io/endpoint.svg?url=https://paperswithcode.com/badge/struct-vreid-semantics-guided-visual/text-to-video-person-re-identification-on)](https://paperswithcode.com/sota/text-to-video-person-re-identification-on)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

[cite_start]Official PyTorch implementation of the paper **"Struct-VReID: Semantics-Guided Visual Grounding for Occluded Text-to-Video Person Re-identification"**[cite: 20]. 

> [cite_start]**Authors:** Rui Sun, Xiaolu Yu, Fei Wang, Zikai Da, Yifan Zhang, Jun Gao [cite: 21]

## 💡 Introduction

[cite_start]Existing Text-to-Video Person Re-identification (T2V ReID) methods are often constrained by coarse global matching paradigms, making them highly susceptible to severe visual noise and occlusions[cite: 24, 25, 26]. [cite_start]To bridge this gap, we propose **Struct-VReID**, a novel framework that advances the paradigm from global matching to structure-aware fine-grained grounding[cite: 26]. 

[cite_start]Struct-VReID introduces a **Hierarchical Semantic Parsing (LLM-HSP)** module to decompose unstructured text into a semantic tree[cite: 27]. [cite_start]Guided by this topology, our **Semantics-Guided Visual Grounding (SGVG)** mechanism actively searches for visible regions across the spatio-temporal domain to filter out occlusion noise[cite: 28]. [cite_start]Finally, a **Multi-Granularity Structural Consistency Alignment (MSCA)** objective ensures geometric and semantic correspondence between retrieved video parts and descriptions via an explicit geometric centroid constraint ($\mathcal{L}_{geo}$)[cite: 29, 215].

![Architecture Diagram](https://github.com/long-12138/Struct-VReID/blob/main/figures/architecture.png) ## 🏆 Main Results

Extensive experiments on TVPReid benchmarks demonstrate the superiority of Struct-VReID, especially under severe occlusions and cross-domain Zero-Shot generalization scenarios.

### In-Domain Performance

| Dataset | Rank-1 | Rank-5 | Rank-10 | mAP | MdR |
| :--- | :---: | :---: | :---: | :---: | :---: |
| [cite_start]**TVPReid-PRID** [cite: 382] | [cite_start]**66.55%** [cite: 30] | [cite_start]89.79% [cite: 382] | [cite_start]97.54% [cite: 382] | [cite_start]76.87% [cite: 382] | [cite_start]1.00 [cite: 382] |
| [cite_start]**TVPReid-iLIDs** [cite: 382] | [cite_start]**40.67%** [cite: 30] | [cite_start]66.00% [cite: 382] | [cite_start]82.67% [cite: 382] | [cite_start]53.59% [cite: 382] | [cite_start]3.00 [cite: 382] |
| [cite_start]**TVPReid-Duke** [cite: 386] | [cite_start]**51.58%** [cite: 30] | [cite_start]78.36% [cite: 386] | [cite_start]84.08% [cite: 386] | [cite_start]63.74% [cite: 386] | [cite_start]1.00 [cite: 386] |

### Zero-Shot Cross-Dataset Generalization (Rank-1)

| Source \ Target | TVPReid-PRID | TVPReid-iLIDs | TVPReid-Duke |
| :--- | :---: | :---: | :---: |
| [cite_start]**TVPReid-PRID** [cite: 395] | [cite_start]- [cite: 395] | [cite_start]20.67% [cite: 395] | [cite_start]12.52% [cite: 395] |
| [cite_start]**TVPReid-iLIDs** [cite: 395] | [cite_start]13.38% [cite: 395] | [cite_start]- [cite: 395] | [cite_start]4.31% [cite: 395] |
| [cite_start]**TVPReid-Duke** [cite: 395] | [cite_start]**30.63%** [cite: 395] | [cite_start]**21.33%** [cite: 395] | [cite_start]- [cite: 395] |

## ⚙️ Installation

```bash
# Clone the repository
git clone [https://github.com/long-12138/Struct-VReID.git](https://github.com/long-12138/Struct-VReID.git) [cite: 31]
cd Struct-VReID

# Create a conda environment
conda create -n tvpreid python=3.10
conda activate tvpreid

# Install PyTorch (Tested on PyTorch 2.0+ and CUDA 11.8)
pip install torch torchvision torchaudio --index-url [https://download.pytorch.org/whl/cu118](https://download.pytorch.org/whl/cu118)

# Install dependencies
pip install -r requirements.txt
pip install opencv-python matplotlib
