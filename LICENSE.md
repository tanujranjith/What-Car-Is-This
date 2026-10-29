# Model weight and data-use notice

The released weights are provided for **non-commercial research and educational
evaluation only**. This release does not grant commercial rights to the weights,
training data, vehicle photographs or third-party material.

This repository contains trained model artifacts. No commercial rights are granted by this notice.

## Training sources and conditions

- RIOTU car make/model/generation, Kaggle version 1:
  https://www.kaggle.com/datasets/riotulab/car-make-model-and-generation .
  Publisher metadata declares Creative Commons Attribution-NonCommercial 4.0:
  https://creativecommons.org/licenses/by-nc/4.0/ .
- CUHK CompCars, acquired from the Kaggle mirror version 1:
  https://www.kaggle.com/datasets/renancostaalencar/compcars .
  The mirror's unknown license field does not override the original terms:
  https://mmlab.ie.cuhk.edu.hk/datasets/comp_cars/ . CompCars is for
  non-commercial research only, prohibits commercial exploitation of images and
  derived data, and prohibits redistribution of its database.
- Initial backbone: torchvision EfficientNet-B0 `IMAGENET1K_V1` weights.
  https://docs.pytorch.org/vision/0.22/models/generated/torchvision.models.efficientnet_b0.html .
  Training on a source does not transfer ownership of its images to this project.

No dataset photographs, raw archives, per-image source manifests or training
checkpoints containing optimizer state are included. Model weights are not a
license to redistribute either dataset. Users must review all upstream terms
for their proposed use; this notice does not expand the upstream permissions or
represent clearance of every original image's copyright.

## Required attribution

Adel Ammar, Anis Koubaa, Wadii Boulila, Bilel Benjdira and Yasser Alhabashi.
*A multi-stage deep-learning-based vehicle and license plate recognition system
with real-time edge inference.* Sensors 23(4):2120, 2023.

Linjie Yang, Ping Luo, Chen Change Loy and Xiaoou Tang.
*A Large-Scale Car Dataset for Fine-Grained Categorization and Verification.*
CVPR, 2015.

The weights are supplied without warranty. Confidence is not proof of vehicle
identity; the model is not suitable for safety, enforcement, insurance or other
high-stakes decisions.
