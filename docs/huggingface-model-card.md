---
tags:
  - image-classification
  - plant-disease
  - pytorch
---

# Apple Leaf Disease Classification Checkpoints

This repository stores trained PyTorch checkpoints for the Apple Disease Classification with Explainable AI notebook project. The checkpoints support the four apple leaf classes used by the project: apple scab, black rot, cedar apple rust, and healthy.

## Files

Upload the contents of the project's `saved_models/` folder. Current local checkpoint files:

- `best_overall_model.pt` — the best checkpoint selected by the model-comparison notebook; the notebook's downstream demo and integration notebooks prefer this filename.
- `resnet50_best.pt` — ResNet50 checkpoint.
- `efficientnet_b0_best.pt` and `efficientnet_b0_best(1).pt` — two separately saved EfficientNet-B0 checkpoints; they have different contents. Verify their provenance before choosing one as canonical.
- `mobilenetv3_large_best.pt` — MobileNetV3-Large checkpoint.

These are state-dict style training artifacts, not standalone Transformers models. Load them with the architecture and preprocessing code in the project's notebooks. Checkpoint keys and exact class-index ordering should be verified against the matching notebook before using them in another application.

## Reported evaluation

The project records its evaluation in `results/test_metrics.json`. That file reports accuracy of 1.000 for ResNet50 and EfficientNet-B0 and approximately 0.999 for MobileNetV3-Large. These are notebook-reported values; rerun the evaluation with the documented test split before relying on them.

## Intended use and limitations

For research and demonstration of image classification and explainability workflows. Predictions can be affected by image quality, lighting, cultivar, geography, disease stage, and distribution shift. This is not a substitute for expert diagnosis or agricultural advice.

## Training data and preprocessing

See the project notebooks, especially Notebooks 1 and 2, for data preparation, class names, preprocessing, and training configuration. The source dataset is not bundled with these weights.

## Usage

Download the files and use the model-building and preprocessing code from the project notebooks. The `.pt` files are PyTorch serialization artifacts and should only be loaded from a trusted source.

## License

No model or dataset redistribution license has been specified yet. Set the appropriate license metadata only after confirming the rights for the training data and derived weights.
