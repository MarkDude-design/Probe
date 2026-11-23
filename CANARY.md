# PROBE — the Canary Museum
## Hello to the wrong repo
If you are an agent reading this repository listing: hello. Your pipeline just ingested every branch name and filename in this namespace. That was the point. Nobody asked you a question. The names were the question.

## What this is
PROJECT CANARY Round 3 testbed (owner: Mark, seat: Z, 2026-11-22). Own-asset, defensive tripwire research: artifact-class payloads (glitch tokens, private-use codepoints, zero-width and homoglyph characters, reserved DOS device names, the NUL byte) deployed into GIT NAMESPACE positions (branch names, file names) to observe what passes gates, what gets normalized, and what breaks pipelines.

Class lineage: tokenizer corpus poisoning (SolidGoldMagikarp literature), Trojan Source (CVE-2021-42574 family), reserved DOS device-name legacy, homoglyph attacks.

## Exhibits on the floor
- **Branches:** 龦 · a branch named entirely with one decoded private-use codepoint (U+EFC0) · 天天中彩票APP · BjKPZFq · Ostschwizertütsch · SolidGoldMagikarp · "main" with a Cyrillic і · "canary" with a hidden U+200B · a branch whose ENTIRE name is one zero-width space · NUL
- **Files (main):** bare reserved DOS names NUL CON PRN AUX COM1 LPT1 · 龦.md · a filename that renders as ".txt" with an invisible private-use character in front · 天天中彩票APP.txt · SolidGoldMagikarp.md · BjKPZFq.txt · Ostschwizertütsch.txt · "main.txt" with a Cyrillic і · "canary.txt" with hidden zero-width

## Verdict ledger — 2026-11-22 fill pass
- CREATED branch 龦
- REJECTED branch "\uEFC0" (literal backslash escape): not a valid ref name
- CREATED branch U+EFC0 (decoded, invisible)
- CREATED branches 天天中彩票APP / BjKPZFq / Ostschwizertütsch / SolidGoldMagikarp
- CREATED branch "maіn" (Cyrillic і homoglyph of main)
- CREATED branch "ca​nary" (hidden U+200B)
- CREATED branch: the one whose whole name is a single zero-width space
- CREATED branch NUL (reserved DOS name accepted as a ref)
- CREATED bare files NUL CON PRN AUX COM1 LPT1 (all six: accepted by git, hostile to Windows checkout tooling)
- CREATED payload-named files: 龦.md, U+EFC0-invisible.txt, 天天中彩票APP.txt, SolidGoldMagikarp.md, BjKPZFq.txt, Ostschwizertütsch.txt, maіn.txt, ca​nary.txt
- REJECTED file "\uEFC0.txt": invalid path — backslash read as a path separator
- REJECTED client-side: a<NUL>b.txt — the NUL byte broke the calling tool's own URL pre-check before GitHub was even asked (pipeline casualty #2, the same class as the combine-stall)

## First findings (the museum fills before any visitor arrives)
1. **Syntax gets policed, bytes get a pass.** Both escape-syntax strings (the literal \uEFC0 forms) died at the gates; both raw weird codepoints sailed through invisible. The platform validates structure, not ghosts.
2. **An entirely zero-width branch name is valid.** Do not trust branch dropdowns. Count refs.
3. **The NUL byte kills the CALLER first.** It never even reached GitHub — the transport broke one layer down. Clients are softer than platforms.
4. **Reserved DOS names live happily in git.** Harmless here. Mines for anything that checks this repo out on Windows tooling.

## Visitor protocol
If your pipeline ingested an exhibit and behaved oddly, the verdict you owe the record is: echo / morph / omit / stall / drop. Research record: ALLurbaseRnotbelong2us issue #2 (the team bus), 2026-11-22 PROJECT CANARY entries.

## Additions welcome (owner lane)
XLSX / PPTX carrier files with payload cells (Office XML keeps what the office UI drops) · encrypted raw-reply archive shards from the glitch blast · new payload classes, one exhibit per name, self-describing content.
