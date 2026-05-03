# BEIR HotpotQA Full

This repository publishes a GitHub-safe public package of the official BEIR `hotpotqa` full dataset.

## Public Asset

- Release asset: `beir-hotpotqa-full.tar.gz`
- SHA-256: `1d6bc5e4bcd5cbad41e033b28f5056499535928ec0a0fb1e6bf17ffcbdf60a6c`

## Package Summary

- Official dataset: `hotpotqa`
- Corpus rows: `5,233,329`
- Query rows: `97,852`
- Qrels:
  - `train.tsv`: `170,000`
  - `dev.tsv`: `10,894`
  - `test.tsv`: `14,810`
- Default BEIR evaluation split: `test`

## Why The Dataset Is Attached As A Release Asset

The unpacked corpus is over `2GB`, so the public package is distributed as a compressed release asset instead of storing the full corpus directly in the Git tree. The asset itself contains:

- gzip-sharded full corpus
- official queries
- official qrels
- normalized queries convenience file
- manifest and packaging scripts

Use `manifest.json` in this repository for the detailed package metadata.
