# Developer Cookbook — K_AWESOMENESY
**Stack:** Python 3.11, PAX 27B, Z3 (symbolic), problog, AIOSS_FORMAT
**Domain:** Neurosymbolic AI toolkit: combining PAX 27B neural inference with symbolic reasoning

## Neuro-symbolic query
```python
from k_awesomenesy import NeurosymbolicReasoner

reasoner = NeurosymbolicReasoner(
    pax_model="./pax-27b-q4.gguf",
    symbolic_engine="z3",
    aioss_chain="./neurosy.aioss"
)

result = reasoner.reason(
    query="Is it safe to administer drug X given patient has condition Y?",
    constraints=["NOT (drug_X AND condition_Y)",  # formal safety constraint
                 "dosage_X < max_safe_dosage"],
    facts={"condition_Y": True, "max_safe_dosage": 500}
)
print(f"Answer: {result.answer}")
print(f"Formally verified: {result.verified}")
print(f"Constraint violations: {result.violations}")
```

## AIOSS Chain Append
```python
import hashlib, time

def aioss_append(chain_path, payload: bytes, module_id: str):
    entry_hash = hashlib.sha3_256(payload).digest()
    ts = int(time.time_ns()).to_bytes(8, 'big')
    with open(chain_path, 'rb') as f:
        f.seek(-32, 2); prev_hash = f.read(32)
    new_hash = hashlib.sha3_256(prev_hash + entry_hash + ts).digest()
    with open(chain_path, 'ab') as f:
        f.write(ts + entry_hash + new_hash)
    return new_hash.hex()
```
