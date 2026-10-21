Run TransformerDTCDR with DP epsilon values **100, 10, 1** and **five seeds**:

```bash
python -u run_recbole_cdr.py --transformer_dp_5seeds --dataset movielens
```

Choose `--dataset movielens`, `amazon`, `book_crossing`, or `douban`.
This runs 15 experiments using seeds 2022–2026, pairing the training,
projection, and Gaussian noise seed in each run. Logs are saved in
`log/dp_grid`, with the dataset, projection seed, noise seed, and epsilon
in each filename. Add `--final_only` for final results only, or
`--dataset_root /absolute/path/to/dataset_example` to select a data location.
The preset fixes the five seeds and three epsilon values.

conda activate "RecBole-CDR-main 2"
python -u run_recbole_cdr.py \
  --model TransformerDTCDR \
  --dataset_preset movielens

- CMF
Evaluate   : 100%|██████████████████████████████████████████████| 315/315 [00:00<00:00, 3554.29it/s]
28 Aug 16:32    INFO  best valid : OrderedDict([('recall@10', 0.2434), ('mrr@10', 0.3643), ('ndcg@10', 0.2299), ('hit@10', 0.7158), ('precision@10', 0.1419)])
28 Aug 16:32    INFO  test result: OrderedDict([('recall@10', 0.254), ('mrr@10', 0.4305), ('ndcg@10', 0.2656), ('hit@10', 0.7253), ('precision@10', 0.1721)])