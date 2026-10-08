# MicroWakeWord

A lightweight repository for experimenting with and building a small wake-word detection pipeline for edge devices and resource-constrained environments.

This project is intended as a starting point for training, evaluating, and iterating on a micro wake-word model that can run efficiently on embedded or local hardware.

## Project goals

- Build a compact wake-word detection model
- Support small-footprint inference for edge devices
- Track experiments, data, and model iterations
- Keep training and evaluation reproducible
- Make it easy to adapt to different wake words and datasets

## Repository structure

```text
.
├── README.md
├── data/
│   ├── raw/
│   ├── processed/
│   └── labels/
├── notebooks/
│   └── exploratory.ipynb
├── src/
│   ├── data/
│   ├── models/
│   ├── train.py
│   ├── evaluate.py
│   └── inference.py
├── configs/
│   └── default.yaml
├── tests/
│   └── test_pipeline.py
├── requirements.txt
├── .gitignore
└── results/
    ├── checkpoints/
    └── metrics/
```

## Typical workflow

1. Collect or curate audio data for the wake word and negatives.
2. Preprocess audio into features such as MFCCs, Mel spectrograms, or log-mel energy.
3. Train a small neural network or classical model for wake-word detection.
4. Evaluate precision, recall, false accept rate, and false reject rate.
5. Export the optimized model for deployment.

## Data organization

Use a simple, consistent format for your dataset:

- `data/raw/`: original recordings
- `data/processed/`: normalized or feature-extracted data
- `data/labels/`: annotation files or CSV metadata

Recommended metadata fields:

- audio file path
- label (`wake_word`, `background`, `noise`, etc.)
- sample rate
- duration in seconds
- speaker / split information

## Suggested training setup

This project can support several model types, including:

- CNN-based keyword spotting models
- tiny RNN or GRU variants
- feature-engineered classical models
- quantized or pruned models for low-resource deployment

A standard pipeline typically includes:

- audio preprocessing
- train/validation/test splits
- balanced sampling across positive and negative examples
- threshold tuning for inference
- model export and benchmarking

## Quick start

```bash
# create a virtual environment
python -m venv .venv
source .venv/bin/activate

# install dependencies
pip install -r requirements.txt

# run training
python src/train.py --config configs/default.yaml
```

## Environment

This project is designed to be easy to run locally and can later be adapted for:

- CPU development
- GPU training
- embedded inference targets
- mobile or microcontroller deployment

## Notes

This README is intentionally written as a flexible starting template. As the project grows, update it with:

- the exact wake word used
- dataset source and licensing
- training hyperparameters
- evaluation metrics
- deployment target and performance constraints
- links to experiments or notebooks

## TODO

- Define the wake word and target use case
- Add dataset pipeline and preprocessing scripts
- Add training config files
- Add evaluation metrics and threshold tuning
- Add deployment/export instructions
- Add experiment tracking and model registry notes

## License

Add a license if the project will be shared publicly or with collaborators.
