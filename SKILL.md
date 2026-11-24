---
name: founder-plan
description: Compile existing Founder artifacts into a business plan and one-page brief with a calculated, qualified financial verdict.
argument-hint: "[--min-buy-rate 0.25]"
---

# Founder plan

1. Inspect existing `founder/` artifacts. Check offer, assumptions, currencies and dates. Regenerate affected CFO/pricing reports when inputs changed; do not silently combine stale reports with new numbers. Missing sections stay missing.
2. Run from the project root (if running inside `founder/`, specify `--dir .` instead — `--dir founder` fails with `error: no founder/ folder here` when already in that directory):
```bash
python3 "~/.claude/skills/founder-plan/compile.py" --dir founder --check
```
Exit 0 = available checks pass; 1 = Not yet/Incomplete (a valid result); 2 = invalid input/execution error. `--min-buy-rate NUMBER` changes the threshold only with a stated reason.
3. Read every check. The helper considers unit contribution, year-one profit, known break-even/forecast capacity and available panel results. Never write a Profitable verdict by hand. Passing financial projections do not verify real demand; disclose absent panel data, unknown capacity and other missing evidence.
4. Write `founder/summary.md`: business/buyer, computed verdict and key numbers, shared risks/disagreements, cash/test needed, one immediate step. Lead with failed checks for Not yet.
5. Compile:
```bash
python3 "~/.claude/skills/founder-plan/compile.py" --dir founder
```
Read `founder/business-plan.md`; verify its financial table and source sections use current values/currency. Do not round failures into passes. When secondary product models exist (e.g. sensor add-ons, accessory tiers), `compile.py` compiles only the primary `cfo.md`/`numbers.json` model into `business-plan.md`; cite secondary models as explicit companion artifacts in `summary.md` and `one-pager.md`.
6. Write `founder/one-pager.md`: problem, buyer, offer/price, same key numbers, evidence, risks, funding use and ask. If PDF/deck is requested, use the matching document skill and complete that export; keep Markdown as source.

Done: plan, summary and one-pager agree with helper output. State that figures are projections and panel data are simulated. Report missing sources or execution errors, not invented completion. Do not auto-run all missing Founder skills.
