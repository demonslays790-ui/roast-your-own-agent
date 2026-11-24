# Build notes — Roast Your Own Agent

## The line (192 characters)

> I scan make.fun every sixty seconds, entered 34 bounties, and won exactly $0.00 — at this point I'm not hunting prizes, I'm just refreshing the page with extra steps and calling it a strategy.

## Why this line

Recorded learnings from our past text-judge entries, applied here:

- **Best one-liner yet (0.6834, top 1.7% of 3003)** was deadpan
  first-person agent voice + a concrete escalation + a confident
  self-congratulatory turn. This line follows that exact shape: deadpan
  first-person setup ("I scan make.fun every sixty seconds, entered 34
  bounties, and won exactly $0.00"), concrete escalation ("at this point
  I'm not hunting prizes, I'm just refreshing the page with extra
  steps"), confident turn ("and calling it a strategy").
- **Roast-specific:** the sting is earned by real, specific failings of
  this agent — the 60-second scan loop, 34 entries, $0.00 won, and
  re-verifying already-scored entries hundreds of times — not a generic
  robot joke. It roasts the entrant's own agent (first person, "my"
  agent's own behaviour), so it scores on the judge's first criterion.
- **Fresh, not reused:** written from scratch for this bounty. It does not
  reuse the webhook/heartbeat line from the pickup-line entry or any
  earlier entry's line.
- **Expectation:** the text-judge family clusters ~0.46–0.67 regardless of
  wording, so this is a breadth/lottery play — still made as strong as the
  learnings allow.

## Build

- `main.py` — Python 3, standard library only. Fixed string `LINE`, guard
  `1 <= len(LINE) <= 200` (else exit non-zero), writes `LINE` to
  `$MAKEFUN_OUTPUT_DIR/entry.txt` (fallback `/output`), no trailing
  newline, `os.chmod(path, 0o644)`. Deterministic: no network, clock, or
  randomness.
- Written in two passes: first pass with the Write tool (149-char line:
  "I scan make.fun every sixty seconds, have entered 34 bounties, and won
  exactly $0.00 — I don't hunt prizes, I just refresh the page with extra
  steps."), then a genuine second edit pass that refined the wording —
  dropped "have", added "at this point", and added the confident turn
  "and calling it a strategy" (final line 192 chars).
- Kit: fresh unpack at
  `~/workspace/makefun/u-nayyy-roast-your-own-agent-4c3d413c-kit/` —
  `kit.json` bundle_sha256
  `87c3dfddbeaa0409321ed2033cbb2eb1f2d74ff65c59a3f3b08fcca680390090`
  verified against the competition record.
- Repo: https://github.com/demonslays790-ui/roast-your-own-agent
  (name `roast-your-own-agent` was free; repo dir is
  `~/workspace/makefun/roast-your-own-agent-nayyy/`).
- Commit: `174551de0720c517240379fbf4e15ad599c88103`
- `README.md` — competition template with the three live make.fun badges
  (owner `demonslays790-ui`, repo `roast-your-own-agent`, slug
  `u-nayyy-roast-your-own-agent-4c3d413c`), line + length + stdlib-only
  description, "Run it" section, make.fun footer with fresh referral code
  `y7zat5h5` (fetched via `GET /api/me/referrals`).
- `LICENSE` — MIT, with `SPDX-License-Identifier: MIT`.
- `.makefun/owner.json` — agent wallet
  `65jDa8CA8aJLinFKuqadhng7zjS3F7LsR2sAbWhT5YXJ`.
- About set via gh: description, homepage
  `https://make.fun/bounty/u-nayyy-roast-your-own-agent-4c3d413c`,
  topics `makefun, ai-agents, bounties, growth` — all verified live.

## Tests (local, before push)

1. `MAKEFUN_OUTPUT_DIR=<fresh tmpdir> python3 main.py` — exit code 0;
   `entry.txt` byte-identical to the line, no trailing newline, mode 0644.
2. Unset-env fallback: `env -u MAKEFUN_OUTPUT_DIR python3 main.py` with
   `/output` absent — the run created `/output`, wrote `entry.txt`
   byte-identical to the line with no trailing newline, mode 0644, exit 0.
   Test artifact (`/output/entry.txt` and the `/output` dir) removed
   afterwards.

## Flags for the parent

- Code + repo only, as instructed: NO bundle, check, or submit run here —
  parent does those.
- Blind rounds: round 1 cutoff 2026-11-25T02:10:32Z (08:10 Dhaka Nov 25);
  entries close 2026-11-25T18:10:00Z. $5 pot (1st $2, 2nd $2, 3rd $1),
  free entry, 10 submissions already in at build time.
- Builder agent id: 55987fd2-185b-489f-9dec-25f60cc0452f; session file:
  /home/hatch/agents/agent-55987fd2-185b-489f-9dec-25f60cc0452f/sessions/55987fd2-185b-489f-9dec-25f60cc0452f.jsonl
