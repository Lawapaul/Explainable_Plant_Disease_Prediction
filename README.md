# Apple Disease Classification with Explainable AI

A notebook-based project exploring transfer-learning classifiers for four apple leaf classes and an explainability pipeline with Grad-CAM, uncertainty and trust estimates, retrieval-augmented knowledge, generated explanations, and human feedback.

## Repository contents

```text
notebooks/       Ordered Colab/Jupyter workflow (01–09)
results/         Aggregate metrics, selected plots, and demonstration outputs
saved_models/    Local model checkpoints; intentionally excluded from Git
test_images/    Small sample images used by the demo notebooks
```

The notebooks were created around Google Colab and Google Drive paths. They are committed without saved cell outputs; run cells in order in a suitable runtime to reproduce them. The full training dataset and trained model checkpoints are not included because of their size and licensing/storage considerations.

## Notebook workflow

1. `01_Data_Preparation.ipynb` — prepare and split the image dataset.
2. `02_Transfer_Learning_Model_Comparison.ipynb` — train and compare ResNet50, EfficientNet-B0, and MobileNetV3-Large.
3. `03_GradCAM_Explainability_All_Test_Images.ipynb` — generate class activation maps and prediction reports.
4. `04_Trust_Uncertainty_Estimation.ipynb` — estimate calibration, uncertainty, and trust.
5. `05_RAG_Knowledge_Retrieval.ipynb` — build and evaluate the disease knowledge retrieval index.
6. `06_Final_LLM_30_Samples_Qwen_RAG.ipynb` — generate grounded explanations for a 30-sample subset.
7. `07_Human_in_the_Loop_Feedback_Memory_FULLY_UPDATED.ipynb` — route cases for review and record feedback.
8. `08_Final_Integration_XAI_Dashboard_WITH_LLM_HITL.ipynb` — assemble the integrated demonstration.
9. `09_Demo_Without_LLM.ipynb` — run a four-sample demonstration without loading the LLM.

## GitHub + Hugging Face storage

The model checkpoints are kept out of Git and are intended for a separate Hugging Face model repository. See [the storage setup guide](docs/storage.md) for upload/download commands and [the draft model card](docs/huggingface-model-card.md). Add the Hugging Face repo link here after creating it.

## Data and model setup

The notebooks expect the project data and checkpoints in a Google Drive folder named `XAI_Project` (some cells use `/content/drive/MyDrive/XAI_Project`). Update the path/configuration cells for your own storage. Put trained `.pt` checkpoints in `saved_models/` and the prepared dataset in the location configured by Notebook 1. These files are ignored by Git; use an external dataset/model host or Git LFS if you need to share them.

The small examples in `test_images/` are included for the demo. Check dataset and image licenses before redistribution.

## Results

Aggregate experiment outputs and representative plots live under `results/`. Per-image Grad-CAM heatmaps/overlays and raw human feedback records are excluded from Git because they add substantial size or may contain user-provided content. The corresponding notebooks can regenerate derived artifacts.

The saved `results/test_metrics.json` reports 1.000 accuracy for ResNet50 and EfficientNet-B0 and 0.999 accuracy for MobileNetV3-Large on the recorded test run. Treat these as the notebook's recorded results; validate the split and rerun the evaluation when reproducing the experiment.

## Requirements

Use a Python environment with Jupyter or Google Colab and the packages imported by the notebook you plan to run. The workflow uses PyTorch/torchvision, scikit-learn, pandas, NumPy, Matplotlib, Pillow, Grad-CAM utilities, FAISS, sentence-transformers, and Hugging Face Transformers. GPU availability is recommended for training and LLM inference. Package versions and accelerator support may need adjustment for your runtime.

## License

No license has been selected for this repository. Add a license file before inviting reuse or redistribution.
