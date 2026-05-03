# BEIR HotpotQA Full

Public packaging of the official BEIR `hotpotqa` dataset, prepared for GitHub publication.

## What Is Included

- Full official `corpus.jsonl`, sharded into 69 files to stay below GitHub's single-file size limit
- Corpus transport format: gzip-sharded JSONL
- Full official `queries.jsonl`
- Full official `qrels/` directory
- A normalized `queries.normalized.jsonl` convenience file
- Build metadata in `manifest.json`

## Directory Layout

```text
hotpotqa/
  corpus/
    corpus-00000.jsonl
    ...
  queries.jsonl
  queries.normalized.jsonl
  qrels/
    train.tsv
    dev.tsv
    test.tsv
manifest.json
```

## Counts

- Corpus rows: 5233329
- Corpus uncompressed size: 2149313046
- Corpus gzip shard size: 641810159
- Query rows: 97852
- Default evaluation split: `test`
- Qrels:
  - train: 170000 rows / 85000 queries
  - dev: 10894 rows / 5447 queries
  - test: 14810 rows / 7405 queries

## Notes

- The corpus shards preserve the original BEIR document schema line-for-line.
- To reconstruct a single-file corpus locally:

```bash
python3 - <<'PY'
import gzip
from pathlib import Path
parts = sorted(Path("hotpotqa/corpus").glob("corpus-*.jsonl.gz"))
with open("corpus.jsonl", "wb") as out:
    for part in parts:
        with gzip.open(part, "rb") as src:
            out.write(src.read())
PY
```

- For BEIR-style evaluation, use `hotpotqa/queries.jsonl` with `hotpotqa/qrels/test.tsv` unless you intentionally need another split.
