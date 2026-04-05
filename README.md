# [CVPR 2026 Findings] SAT
[CVPR 2026 Findings] Official repository for "SAT: Selective Aggregation Transformer for Image Super-Resolution"

### SAT: Selective Aggregation Transformer for Image Super-Resolution [[Paper Link]](https://github.com/PhuTran1005/SAT)
[Dinh Phu Tran](https://scholar.google.com/citations?user=peeXHDYAAAAJ&hl=en), [Thao Do](https://scholar.google.com/citations?user=_KJqjjYAAAAJ&hl=en), [Saad Wazir](https://scholar.google.com/citations?user=hMSbyCoAAAAJ&hl=en), [Seongah Kim](https://github.com/PhuTran1005/SAT), [Seon Kwon Kim](https://github.com/PhuTran1005/SAT) and [Daeyoung Kim](https://github.com/PhuTran1005/SAT)

[![arXiv](https://img.shields.io/badge/arXiv-Paper-<COLOR>.svg)](https://github.com/PhuTran1005/SAT)
![visitors](https://visitor-badge.laobi.icu/badge?page_id=PhuTran1005.SAT)
[![GitHub Stars](https://img.shields.io/github/stars/PhuTran1005/SAT?style=social)](https://github.com/PhuTran1005/SAT)

## Updates
- ✅ 2026-04-01: Release repository

## Overview

**Abstract:**

> Transformer-based approaches have revolutionized image super-resolution by modeling long-range dependencies. However, the quadratic computational complexity of vanilla self-attention mechanisms poses significant challenges, often leading to compromises between efficiency and global context exploitation. Recent window-based attention methods mitigate this by localizing computations, but they often yield restricted receptive fields. To mitigate these limitations, we propose **S**elective **A**ggregation **T**ransformer (SAT). This novel transformer efficiently captures long-range dependencies, leading to an enlarged model receptive field by selectively aggregating key-value matrices (reducing the number of tokens by **97**%) via our Density-driven Token Aggregation algorithm while maintaining the full resolution of the query matrix. This design significantly reduces computational costs, resulting in lower complexity and enabling scalable global interactions without compromising reconstruction fidelity. SAT identifies and represents each cluster with a single aggregation token, utilizing density and isolation metrics to ensure that critical high-frequency details are preserved. Experimental results demonstrate that SAT outperforms the state-of-the-art method PFT by **up to 0.22dB**, while the total number of FLOPs can be reduced by **up to 27**%.

**Overall Architecture of SAT:**

<img src="https://raw.githubusercontent.com/PhuTran1005/SAT/master/figures/sat.png" width="600"/>

#### Selective Aggregation Attention:

<img src="https://raw.githubusercontent.com/PhuTran1005/SAT/master/figures/saa.png" width="600"/>

**Quantitative Results:**

<img src="https://raw.githubusercontent.com/PhuTran1005/SAT/master/figures/performance.png" width="600"/>

**Qualitative Results:**

<img src="https://raw.githubusercontent.com/PhuTran1005/SAT/master/figures/vis.png" width="600"/>

## Environment
- [PyTorch >= 1.7](https://pytorch.org/) **(Recommend **NOT** using torch 1.8!!! It would cause abnormal performance.)**
- [BasicSR == 1.3.4.9](https://github.com/XPixelGroup/BasicSR/blob/master/INSTALL.md) 
### Installation
Install Pytorch first.
Then,
```
pip install -r requirements.txt
python setup.py develop
```

## How To Test

- Run the following codes:
```
python basicsr/test.py -opt options/test/SAT_SRx4.yml
```
The testing results will be saved in the `./results` folder.  

## How To Train

- Refer to `./options/train` for the configuration file of the model to train.
- Preparation of training data can refer to [this page](https://github.com/XPixelGroup/BasicSR/blob/master/docs/DatasetPreparation.md).

- The training command is like
```
CUDA_VISIBLE_DEVICES=0,1 python -m torch.distributed.launch --nproc_per_node=2 --master_port=4321 basicsr/train.py -opt options/train/train_SAT_SRx4.yml --launcher pytorch
```

The training logs and weights will be saved in the `./experiments` folder.

## Citations
#### BibTeX

TBD

## Acknowledgement

Our codes was built on [BasicSR](https://github.com/xpixelgroup/basicsr) and [RGT](https://github.com/zhengchen1999/RGT). Thank you authors for sharing their great works.