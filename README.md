# [CVPR 2026 Findings] SAT
[CVPR 2026 Findings] Official repository for "SAT: Selective Aggregation Transformer for Image Super-Resolution"

### SAT: Selective Aggregation Transformer for Image Super-Resolution [[Paper Link]](https://github.com/PhuTran1005/SAT)
[Dinh Phu Tran](https://scholar.google.com/citations?user=peeXHDYAAAAJ&hl=en), [Thao Do](https://scholar.google.com/citations?user=_KJqjjYAAAAJ&hl=en), [Saad Wazir](https://scholar.google.com/citations?user=hMSbyCoAAAAJ&hl=en), [Seongah Kim](https://github.com/PhuTran1005/SAT), [Seon Kwon Kim](https://github.com/PhuTran1005/SAT) and [Daeyoung Kim](https://github.com/PhuTran1005/SAT)

## Updates
- ✅ 2026-04-01: Release repository

## Overview

## Citations
#### BibTeX

TBD

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

## Contact
If you have any question, please email `phutx2000@kaist.ac.kr`