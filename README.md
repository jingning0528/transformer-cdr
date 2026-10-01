# Transformer-Based Cross-Domain Recommendation

A research implementation of Transformer-based cross-domain recommendation built on [RecBole-CDR](https://github.com/RUCAIBox/RecBole-CDR).

This repository explores knowledge transfer between source and target domains using Transformer-enhanced recommendation models, with reproducible dataset presets and optional privacy-aware source-data preprocessing.

## Highlights

- Transformer-enhanced dual-target cross-domain recommendation
- Source and target domain training through the RecBole-CDR pipeline
- Dataset presets for MovieLens, Amazon, Book-Crossing, and Douban
- CPU, CUDA, single-run, multi-model, and multi-seed experiment modes
- Optional differential privacy preprocessing for source-domain interactions

## Included Models

The main experimental models are:

- `TransformerDTCDR`
- `TransformerDTCDRNoSource`
- `AttentionDTCDR`
- `DTCDR`
- `EMCDR`
- `CoNet`
- `NeuMF`
- `CMF`

Additional cross-domain recommendation baselines inherited from RecBole-CDR are also included.

## Requirements

- Python 3.7 or later
- PyTorch
- RecBole 1.0.1

Install the listed Python dependency with:

```bash
pip install -r requirements.txt
```

## Quick Start

Run `TransformerDTCDR` with the MovieLens preset:

```bash
python -u run_recbole_cdr.py \
  --model TransformerDTCDR \
  --dataset_preset movielens \
  --dataset_root /absolute/path/to/dataset_example
```

Available dataset presets are:

```text
movielens
amazon
book_crossing
douban
```

The dataset root must be an absolute path containing the corresponding source and target dataset directories.

## Common Experiment Options

Force CPU execution:

```bash
python run_recbole_cdr.py \
  --model TransformerDTCDR \
  --dataset_preset amazon \
  --dataset_root /absolute/path/to/dataset_example \
  --compute_device cpu
```

Run the configured models across multiple seeds:

```bash
python run_recbole_cdr.py \
  --multimodel \
  --multiseed \
  --dataset_preset book_crossing \
  --dataset_root /absolute/path/to/dataset_example
```

Run the differential privacy parameter grid:

```bash
python run_recbole_cdr.py \
  --model TransformerDTCDR \
  --dp_grid \
  --dataset_preset douban \
  --dataset_root /absolute/path/to/dataset_example
```

Use `python run_recbole_cdr.py --help` to view all available options.

## Project Structure

```text
recbole_cdr/
├── data/                         # Dataset loading and source-DP preprocessing
├── model/cross_domain_recommender/
│   ├── transformerdtcdr.py       # Transformer-based CDR model
│   └── transformerdtcdrnosource.py
├── properties/dataset/           # Dataset presets
├── properties/model/             # Model configurations
└── quick_start/                   # Training and evaluation entry points
```

## Acknowledgements

This project is based on [RecBole-CDR](https://github.com/RUCAIBox/RecBole-CDR) and [RecBole](https://github.com/RUCAIBox/RecBole). Please refer to the upstream projects for their original implementations and citations.

## License

This repository is available under the [MIT License](LICENSE).
