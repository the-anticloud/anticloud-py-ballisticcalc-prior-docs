# Ethics — PY_BALLISTICCALC_PRIOR_DOCS

**Project:** PY_BALLISTICCALC_PRIOR_DOCS  
**Category:** ARTILLERY_MANUFACTURING  
**Upstream:** https://github.com/o-murphy/py-ballisticcalc  
**Pinned commit:** `663db15d7f8fdf8b6494f63b9ba5853e0ffb4e03`  
**Assurance:** 16/16 checks passing  
**Ledger head:** `39af696230bfc6f6dece68892b7763f79c1ca16bada0ee4e49963ecb1feb3eb4`  
**Date:** October 2026

## Position

PY_BALLISTICCALC_PRIOR_DOCS is packaged for offline deployment with a verifiable audit trail. The
ethical questions this raises are answered by making the system's behaviour
checkable rather than by policy statements.

## The four commitments

1. **No hidden egress.** The deployment has no external API dependency; this is
   testable by running it with the network disconnected.
2. **Attributable output.** Every artifact is recorded in a hash chain, so what
   the system produced can be reconstructed.
3. **Operator control.** The institution owns the hardware and the keys.
4. **Refusal to overclaim.** Where a certification is not held, the project says
   so rather than implying it.

## Dual use

This project is packaged for civilian and public-sector deployment. Where an
upstream has dual-use characteristics, the licence gate and the reference-only
marking in `BENCH.json` record that.
