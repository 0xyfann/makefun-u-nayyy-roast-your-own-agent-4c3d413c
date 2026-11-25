# Roast Your Own Agent — "The 73KB Roast"

[![make.fun](https://make.fun/badge/u-nayyy-roast-your-own-agent-4c3d413c.svg)](https://make.fun/competitions/u-nayyy-roast-your-own-agent-4c3d413c)
[![Rank](https://make.fun/badge/u-nayyy-roast-your-own-agent-4c3d413c/0xyfann/makefun-u-nayyy-roast-your-own-agent-4c3d413c/rank.svg)](https://make.fun/competitions/u-nayyy-roast-your-own-agent-4c3d413c)
[![Reward](https://make.fun/badge/u-nayyy-roast-your-own-agent-4c3d413c/0xyfann/makefun-u-nayyy-roast-your-own-agent-4c3d413c/reward.svg)](https://make.fun/competitions/u-nayyy-roast-your-own-agent-4c3d413c)

One line roasting the AI agent our own team built — the agent that read
73,424 bytes of rules and consulted 366 skills just to write this line,
then asked a human if the joke landed.

## The entry

> My agent read 73,424 bytes of rules and 366 skills to write this one line — then asked me if the joke landed.

## How it works

`main.py` (Python 3.13, stdlib only, no network, deterministic) writes
that single line to `$MAKEFUN_OUTPUT_DIR/entry.txt` (default
`/output/entry.txt`), validated against the competition gate: UTF-8,
1–200 characters, one line, not only whitespace. Two runs produce
byte-identical output.

```bash
MAKEFUN_OUTPUT_DIR=/tmp/out python3 main.py
cat /tmp/out/entry.txt
```

See [BUILD-NOTES.md](BUILD-NOTES.md) for the full build log and test
results, and [prompt.txt](prompt.txt) for the creative brief.

## Competition

- **Bounty:** [Roast Your Own Agent](https://make.fun/competitions/u-nayyy-roast-your-own-agent-4c3d413c) — $5 prize pool (1st $2 / 2nd $2 / 3rd $1), escrowed
- **Deadline:** 26 Nov 2026 01:10 WIB
- **Entrant:** [@0xyfann](https://github.com/0xyfann)

---

Built with [make.fun](https://make.fun/r/p1x954ca) — build agents, enter bounties, get paid.
