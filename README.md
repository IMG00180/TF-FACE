# TF-FACE

Official implementation of **TF-FACE: Time-Frequency Fusion Learning with Frequency-Domain Adaptive and Controllable Enhancement for Trajectory Prediction**.

TF-FACE is a trajectory prediction framework for autonomous driving. It integrates time-domain and frequency-domain modeling to capture both global motion trends and local dynamic details for multi-modal trajectory forecasting.

## Overview

Trajectory prediction requires both reliable long-term trend modeling and accurate short-term detail recovery. TF-FACE addresses this problem by introducing a time-frequency fusion framework with frequency-domain adaptive enhancement.

The main components include:

- **Frequency-domain adaptive attention** for trajectory feature enhancement.
- **Low-frequency feature extraction** for future motion trend guidance.
- **High-frequency feature extraction** for local motion detail modeling.
- **Dual-branch decoder** for trend prediction and detail refinement.

## Repository Structure

```text
TF-FACE/
├── configs/              # Configuration files
├── datasets/             # Dataset preprocessing and loading
├── models/               # Model definitions
├── losses/               # Training losses
├── utils/                # Utility functions
├── tools/                # Training and evaluation scripts
├── checkpoints/          # Saved checkpoints
├── README.md
└── requirements.txt
```

## Installation

Create a conda environment:

```bash
conda create -n tfface python=3.8
conda activate tfface
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Please install the PyTorch version that matches your CUDA version. For example:

```bash
pip install torch torchvision torchaudio
```

## Dataset Preparation

Please download the required trajectory prediction datasets from their official websites.

The recommended directory structure is:

```text
data/
├── argoverse1/
│   ├── train/
│   ├── val/
│   └── test/
└── argoverse2/
    ├── train/
    ├── val/
    └── test/
```

Preprocess the dataset:

```bash
python tools/preprocess.py --dataset argoverse1 --data_root data/argoverse1
```

For Argoverse 2:

```bash
python tools/preprocess.py --dataset argoverse2 --data_root data/argoverse2
```

## Training

Train TF-FACE on Argoverse 1:

```bash
python tools/train.py --config configs/tfface_argoverse1.yaml
```

Train TF-FACE on Argoverse 2:

```bash
python tools/train.py --config configs/tfface_argoverse2.yaml
```

The checkpoints will be saved in:

```text
checkpoints/
```

## Evaluation

Evaluate a trained model on Argoverse 1:

```bash
python tools/eval.py \
  --config configs/tfface_argoverse1.yaml \
  --checkpoint checkpoints/tfface_argoverse1.pth
```

Evaluate a trained model on Argoverse 2:

```bash
python tools/eval.py \
  --config configs/tfface_argoverse2.yaml \
  --checkpoint checkpoints/tfface_argoverse2.pth
```

## Metrics

The evaluation script reports common multi-modal trajectory prediction metrics:

- minADE
- minFDE
- MR
- Brier-minFDE

## Pretrained Models

Pretrained models will be released after the paper is accepted.

```text
checkpoints/
└── tfface_argoverse1.pth
```

## Citation

If you find this repository useful, please cite our paper:

```bibtex
@inproceedings{song2026tfface,
  title={{TF-FACE}: Time-Frequency Fusion Learning with Frequency-Domain Adaptive and Controllable Enhancement for Trajectory Prediction},
   author={Anonymous},
  booktitle={International Conference on Machine Learning},
  year={2026}
}
```

For anonymous review, please use:

```bibtex
@inproceedings{anonymous2026tfface,
  title={{TF-FACE}: Time-Frequency Fusion Learning with Frequency-Domain Adaptive and Controllable Enhancement for Trajectory Prediction},
  author={Anonymous},
  booktitle={Under Review},
  year={2026}
}
```

## License

This project is released under the MIT License.

## Acknowledgements

This codebase is built for research on autonomous driving trajectory prediction. We thank the authors of public trajectory prediction datasets and open-source motion forecasting frameworks.
