# GitHub + Hugging Face storage setup

Use GitHub for notebooks, documentation, selected small result summaries, and demo images. Use a Hugging Face **model** repository for the five local `.pt` checkpoints in `saved_models/`. The notebooks expect these files locally under `saved_models/`; download them there before running notebooks 2–9.

The full training dataset is not present in this project folder. Keep it in its permitted source/storage location and configure Notebook 1 accordingly. If you later need to distribute it, use a separate Hugging Face **dataset** repository and confirm redistribution rights first.

## Create and upload the model repo

1. Create a Hugging Face account (or use your existing account) and create a **private model repository** such as `YOUR_USERNAME/apple-disease-xai-models`.
2. Install and authenticate the official Hub CLI:

   ```bash
   python -m pip install -U huggingface_hub
   hf auth login
   ```

3. From the project root, upload the checkpoints. Replace the repository ID with your account and repository name:

   ```bash
   hf upload YOUR_USERNAME/apple-disease-xai-models ./saved_models saved_models
   ```

4. Copy [huggingface-model-card.md](huggingface-model-card.md) to the model repository as `README.md`. Keep the model private until you have confirmed that the dataset terms allow sharing the derived weights; change visibility when ready.

Hugging Face's CLI streams uploads and supports retrying an interrupted folder upload. The Hub documentation recommends a Model Card to explain model files, evaluation, and intended use.

## Download checkpoints for the notebooks

After authenticating (or once the repo is public), download from the project root:

```bash
hf download YOUR_USERNAME/apple-disease-xai-models --repo-type model --local-dir saved_models
```

The repository includes notebook-readable results and selected visuals but ignores checkpoints, per-image heatmaps, and raw human feedback. Keep the GitHub README's Hugging Face link updated after the model repo has been created.

## GitHub repository setup

The selected GitHub payload is approximately 7.2 MiB. Keep the existing `.gitignore` rules in place so model checkpoints and bulk generated artifacts cannot accidentally enter Git history. GitHub enforces a 100 MB individual object limit and recommends Git LFS or external storage for large binaries.

Official references: [Hugging Face model uploads](https://huggingface.co/docs/hub/models-uploading), [Hugging Face CLI uploads](https://huggingface.co/docs/huggingface_hub/guides/upload), [GitHub repository limits](https://docs.github.com/en/repositories/creating-and-managing-repositories/repository-limits).
