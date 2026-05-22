# zk-doctor badges

## Generic "Audited by zk-doctor"
Embed in any ZK repo:
```markdown
[![Audited by zk-doctor](https://battam1111.github.io/bounty-radar-data/badges/audited.svg)](https://github.com/Battam1111/zk-pipeline-doctor)
```

## Per-repo dynamic score (shields.io endpoint)
After running `zk-doctor --format json` and submitting via the badge-update API:
```markdown
[![zk-doctor score](https://img.shields.io/endpoint?url=https://battam1111.github.io/bounty-radar-data/badges/<owner>/<repo>.json)](https://github.com/Battam1111/zk-pipeline-doctor)
```

## Static grade bands
For repos that don't want the dynamic endpoint:
- score-excellent.svg (≥0.85)
- score-good.svg (0.70-0.85)
- score-fair.svg (0.50-0.70)
- score-needs-work.svg (<0.50)

All assets are CC0 — copy, embed, modify freely.
