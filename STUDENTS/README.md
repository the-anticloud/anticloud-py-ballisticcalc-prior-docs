# Students — PY_BALLISTICCALC_PRIOR_DOCS

**Project:** PY_BALLISTICCALC_PRIOR_DOCS  
**Category:** ARTILLERY_MANUFACTURING  
**Upstream:** https://github.com/o-murphy/py-ballisticcalc  
**Pinned commit:** `663db15d7f8fdf8b6494f63b9ba5853e0ffb4e03`  
**Assurance:** 16/16 checks passing  
**Ledger head:** `39af696230bfc6f6dece68892b7763f79c1ca16bada0ee4e49963ecb1feb3eb4`  
**Date:** October 2026

## What this project gives you

A complete worked example of offline-first packaging with a cryptographic audit
chain: source pinned at `663db15d7f8fdf8b6494f63b9ba5853e0ffb4e03`, a 16-check assurance suite, an evidence register
with per-check hashes, and an AIOSS ledger chain ending at `39af696230bfc6f6dece68892b7763f79c1ca16bada0ee4e49963ecb1feb3eb4`.

## Learn by verifying

```
python tools/run_bench.py --out BENCH.json
```

Then take any row from `ISOLATED_LAB_RESULTS/03_Result_Register.md`, recompute
the SHA3-256 of its evidence file, and confirm it matches. If it does not match,
the record has been altered — that is the whole point of the chain.

## Licence

Apache 2.0 terms apply to study and teaching use.
