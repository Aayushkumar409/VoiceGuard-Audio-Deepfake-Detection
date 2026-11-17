# VoiceGuard-Audio-Deepfake-Detection
VoiceGuard is a research project that compares approaches for classifying speech recordings as bonafide or spoofed. The project explores compact acoustic features, classical classifiers, dense neural networks, mel-spectrogram CNNs, and pretrained speech encoders.

## Project team

- Aayush Kumar
- Gautam Sharma (`gautam87004-max`), Project Partner
- 
## Repository contents

- `notebooks/` — all 18 project notebooks, including exploratory analysis, model training, and comparisons.
- `literature/` — the 25-paper literature review workbook.
- `paper/` — the expanded research paper.
- `presentation/` — a 13-slide project explainer with speaker notes.

## Data

The notebooks load the DFADD evaluation package from Hugging Face (`SpeechAntiSpoofingBenchmarks/DFADD`). The audio dataset is not stored in this repository. Review the dataset's terms and citation requirements before using or redistributing audio.

Several notebooks form a balanced subset of 755 bonafide and 755 spoof examples, then use a random train/test split. Because the code uses the package's evaluation/test split to build model training and test partitions, these results are exploratory within-package measurements, not an untouched benchmark evaluation or evidence of performance on unseen generators. See the research paper for the detailed protocol, results, and limitations.

## Environment

The notebooks use Python packages listed in `requirements.txt`. Some models need substantial memory or an available GPU. The transformer notebooks can run on CPU, but training may be slow. Install the PyTorch build that matches your hardware using the official PyTorch installation instructions.

```bash
python -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
jupyter lab
```

Open notebooks from `notebooks/`. Most load DFADD automatically and may download several gigabytes of audio on first run. Check each notebook's cells for its model-specific settings and output paths.

## Collaboration

Use a separate branch for experiments and open a pull request before merging changes to the shared `main` branch. Keep generated model weights, cached datasets, and temporary exports out of Git; `.gitignore` covers common artifacts. Do not commit API tokens, private keys, or personal access credentials.

## Reproducing the reported comparison

Start with `notebooks/VoiceGuard_All_Model_Comparison (1).ipynb` for the saved seven-model spectrogram comparison. The SVM and Random Forest runs are in `notebooks/1st_baseline.ipynb` and `notebooks/2nd_baseline.ipynb`. The paper reports only metrics preserved in the supplied notebook outputs; the Wav2Vec 2.0, HuBERT, WavLM, and AST notebooks contain implementation code without saved final test metrics.

## Citation and reuse

Cite the DFADD dataset and the relevant research papers when using this project. No software license has been selected yet; until one is added, the repository's public visibility does not grant permission to reuse its code or documents.
