# Ledger Status

**Project:** `K_AWESOMENESY`  
**Tier:** TIER_5_WORLD_NEURO_EMBODIED  
**Identity:** Upstream `LAMDA-NeSy/Awesome-LLM-Reasoning-with-NeSy` @ `22e740dca84b` (unknown)

## Chain state

| Fact | Value |
| --- | --- |
| Upstream | `LAMDA-NeSy/Awesome-LLM-Reasoning-with-NeSy` |
| Commit | `22e740dca84b6eca0f359562ff062cb5d540df5f` |
| Upstream licence | unknown |
| Licence class | unknown |
| Clone size | 0.93 MB |
| Ledger | 0 blocks, chain verified |
| Current TRL | NOT YET MEASURED |
| Post-optimisation TRL | NOT YET MEASURED |
| II budget cap | 1000.0 IIU |
| Verified upstream edits | 0 |

- Blocks: **0**
- Head digest: `None`
- Chain verification: **verified**

## Independent verification

The chain is verifiable without trusting this project's tooling:

```
anticloud ledger verify
anticloud ledger export > ledger.jsonl
```

Each block carries the previous block's digest, so removing or reordering an
entry invalidates every block after it. That property is the reason the
ledger can stand in for a claim of what happened.
