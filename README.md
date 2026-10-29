# What Car Is This? — Expanded EfficientNet-B0

Trained vehicle recognition weights covering **239 model families across 42 makes**, using 346 leaf categories. Expanded training completed 30 epochs. This repository contains the model artifacts and documentation.

## Model files

- `model.safetensors`: the exported trained weights (18,006,832 bytes).
- `config.json`: architecture, labels, image size, calibration, and training provenance hashes.
- `checksums.json`: SHA-256 checksums for both artifact files.
- `LICENSE.md`: non-commercial research terms, upstream restrictions, and source attribution.

## Measured held-out results

Evaluated on 11,683 test images, separate from checkpoint selection and calibration:

| Metric | Result |
| --- | ---: |
| Leaf top-1 | 92.17% |
| Leaf top-5 | 98.16% |
| Leaf macro F1 | 0.9073 |
| Manufacturer accuracy | 95.60% |
| Model accuracy | 92.85% |
| Expected calibration error | 0.0117 |

These are project-specific splits. One expanded seed was trained. Current-year coverage, open-set detection, and robust real-world performance have not been established. Added model families have no generation or year labels.

## Loading the weights

This is a custom PyTorch/torchvision model. Create `torchvision.models.efficientnet_b0(weights=None)`, replace `model.classifier[1]` with a linear layer mapping its existing input features to `len(config['labels'])` outputs, then load `model.safetensors` with `safetensors.torch.load_file` and `model.load_state_dict`. Call `model.eval()` for inference. Reference versions: PyTorch 2.7.1, torchvision 0.22.1, safetensors 0.6.2.

For inference, convert the image to RGB after applying EXIF orientation; resize its short side to 255 pixels, center crop to 224 by 224, convert to a tensor, and normalize with ImageNet mean `[0.485, 0.456, 0.406]` and standard deviation `[0.229, 0.224, 0.225]`. Divide logits by the calibration temperature in `config.json` before softmax. Class indices follow `config['labels']`. The configured confidence threshold is an in-distribution rejection heuristic; unsupported cars and non-car images can still receive high scores.

Verify the file hashes against `checksums.json` before use. The weights are provided for **non-commercial research and educational evaluation only**; see [LICENSE.md](LICENSE.md). No dataset photographs or optimizer checkpoints are distributed.
