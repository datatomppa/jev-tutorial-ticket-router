# Jev ticket router

Companion code for the DataCamp tutorial [Jev API: A Practical Guide](LINK).

A support ticket router built on [Jev](https://typesafe.ai), TypeSafe AI's System One
model. One API call asks six typed questions about a ticket; an ordinary Python
function turns those answers into a routing decision. Jev decides *what*, the code
decides *what happens*.

## Setup

Requires Python 3.10+ and a TypeSafe early-access key.

```bash
pip install typesafe-sdk
export TYPESAFE_API_KEY="your-key"
```

## Run

```bash
python router.py
```

## What's here

| File | Description |
| --- | --- |
| `router.py` | The question set, the Jev call, and the routing policy |

## Notes

The thresholds in `route()` are illustrative, not calibrated. Set your own against
labelled tickets before routing anything automatically.

The script uses `jev-latest`. Pin a version (`TypeSafeClient(model="jev-1.13.0")`)
once your thresholds depend on specific model behaviour.

If your first call raises a `TypeError` about `output_buffer_limit`, upgrade the
SDK's compression backend: `pip install -U typesafe-sdk httpx2 zstandard brotli`.
