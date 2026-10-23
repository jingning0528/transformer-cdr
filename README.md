Choose Transformer DP seeds and epsilon values at run time:

```bash
python -u run_recbole_cdr.py --transformer_dp --dataset movielens \
  --seed 2025, 2026 --epsilon 10, 1
```

This runs four experiments (each seed × each epsilon), pairing training,
projection, and noise seeds. Space-separated values also work:
`--seed 2025 2026 --epsilon 10 1`. Use `--seed`, without a colon.
The existing `--transformer_dp_5seeds` flag remains an alias and accepts these
options too. Without overrides, defaults are seeds 2022–2026 and epsilon
100, 10, 1. Detailed output stays in `log/dp_grid`; per-user Top-K export
is disabled.

Run TransformerDTCDR with DP epsilon values **100, 10, 1** and **five seeds**:

```bash
python -u run_recbole_cdr.py --transformer_dp_5seeds --dataset movielens
```

Choose `--dataset movielens`, `amazon`, `book_crossing`, or `douban`.
This runs 15 experiments using seeds 2022–2026, pairing the training,
projection, and Gaussian noise seed in each run. Logs are saved in
`log/dp_grid`, with the dataset, projection seed, noise seed, and epsilon
in each filename. This preset prints final results only; detailed configuration
and training output go to `.log` files, and prints, warnings, and failure
tracebacks go to matching `.log.console.txt` files. Use
`--dataset_root /absolute/path/to/dataset_example` to select a data location.
Override these defaults with `--seed` and `--epsilon`.

conda activate "RecBole-CDR-main 2"
python -u run_recbole_cdr.py \
  --model TransformerDTCDR \
  --dataset_preset movielens

- CMF
Evaluate   : 100%|██████████████████████████████████████████████| 315/315 [00:00<00:00, 3554.29it/s]
28 Aug 16:32    INFO  best valid : OrderedDict([('recall@10', 0.2434), ('mrr@10', 0.3643), ('ndcg@10', 0.2299), ('hit@10', 0.7158), ('precision@10', 0.1419)])
28 Aug 16:32    INFO  test result: OrderedDict([('recall@10', 0.254), ('mrr@10', 0.4305), ('ndcg@10', 0.2656), ('hit@10', 0.7253), ('precision@10', 0.1721)])