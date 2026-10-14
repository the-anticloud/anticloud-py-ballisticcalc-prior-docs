# Educators — PY_BALLISTICCALC_PRIOR_DOCS

**Project:** PY_BALLISTICCALC_PRIOR_DOCS  
**Category:** ARTILLERY_MANUFACTURING  
**Upstream:** https://github.com/o-murphy/py-ballisticcalc  
**Pinned commit:** `663db15d7f8fdf8b6494f63b9ba5853e0ffb4e03`  
**Assurance:** 16/16 checks passing  
**Ledger head:** `39af696230bfc6f6dece68892b7763f79c1ca16bada0ee4e49963ecb1feb3eb4`  
**Date:** October 2026

## Teaching with PY_BALLISTICCALC_PRIOR_DOCS

The project is usable as a worked example of offline-first packaging with a
cryptographic audit chain. It ships with the assurance suite, the evidence
register and the ledger, so students can verify claims rather than take them on
faith.

## Suggested exercises

1. Run `python tools/run_bench.py --out BENCH.json` and read the 16 results.
2. Recompute the SHA3-256 of a row's evidence file and compare to the register.
3. Walk the AIOSS chain from genesis to head `39af696230bfc6f6dece68892b7763f79c1ca16bada0ee4e49963ecb1feb3eb4` and confirm every link.
4. Break one artifact and observe the chain fail to verify.

## Licence for teaching

Apache 2.0 terms apply to academic and teaching use. See `24_ANTICOMMONS_LICENSE`.
