# Ken Deibel · datumstake

**Systems engineer building local-first AI agents — with a field-services /
geospatial background.** I design harnesses that make small, swappable models do
large, verifiable work: the intelligence lives in the system around the model, not
in any one model's weights. Before software, a heavy background running Trimble
line-of-sight positioning systems in the field — where a wrong answer costs a dug-up
site, so *verification* isn't a nice-to-have.

Available for contract work in document extraction pipelines, AI/agent systems,
developer tooling, backend infrastructure, and software that touches surveying /
field-services / geospatial.

---

### What I work on

**Agent harnesses over model fine-tuning.** My main system runs local models through
a persistent, content-addressed memory and a retrieval layer (living RAG) instead of
training — so the same harness keeps working when the model underneath is swapped. The
capability accumulates in tools and records, which means it is inspectable and portable
rather than frozen in a checkpoint.

**Verification-first execution.** [**ratchet**](https://github.com/datumstake/ratchet)
is the shape: a workload is reduced to an objective contract — a metric command, a
propose command, a rollback command — and a change is kept only when the metric
*verifiably* improved. A small model drives real multi-step work and never gets a vote
on whether it worked; the measurement decides what lands.

**Documents that resist being read.** PDFs, drawings and scanned forms, extracted into
structured rows that can be audited. The parsing is the easy half; the hard half is
refusing to emit a row that cannot be traced back to a spot on the page -- a wrong value
that looks right is the failure mode that costs a customer money, and it is invisible
until someone acts on it.

**Browser and desktop automation.** [**handle**](https://github.com/datumstake/handle)
drives a real, logged-in Chrome over CDP with nine one-word verbs; a sibling driver does
the Windows desktop over UIA. The model sees the page as *numbered elements* rather than
composing selectors, which is what makes a 7B-class model able to run an authenticated
workflow a headless scraper cannot reach.

### Selected work

**Start here:** [pdftext](https://github.com/datumstake/pdftext) is one header file with
no dependencies that pulls text out of a PDF — the shortest read, and the one with a
from-scratch DEFLATE decoder in it. [focus-three](https://datumstake.github.io/focus-three/)
runs in your browser right now, nothing to install. For how I think about verification,
[**ratchet**](https://github.com/datumstake/ratchet) is the shortest statement of it.

| Project | What it is | Proof you can run |
|---|---|---|
| **[pdftext](https://github.com/datumstake/pdftext)** | PDF text extraction in a single C++ header, zero dependencies: a from-scratch DEFLATE decoder, chained `/ASCII85Decode` filters, subset fonts decoded through `/ToUnicode` CMaps, per-page attribution, and CTM tracking so rotated callouts land on the sheet. Written because the deployment was an offline machine where "copy one file" had to mean one file. | `make test` — 132 checks over 8 fixtures, each named for the PDF construct it proves. The corpus generator writes its own expected output, so the parser never grades itself; CI regenerates it and fails on a diff. `-Werror` on g++/clang/MSVC, ASan+UBSan, and 312 mutated files that must not crash. |
| **[gapsmith](https://github.com/datumstake/gapsmith)** | *Resolve a whole class of porting gaps from rules that carry their own proof.* A missing symbol doesn't get a bespoke script here — its **shape** is described as a rule, and the rule ships with a machine-checkable proof that applying it is safe. Case study: a small model driving a real porting effort ~1100 undefined symbols deep, every change ground-truthed by a compile+link. | `python examples/demo.py` resolves a constant proved by tileset byte-identity — then corrupt that asset, re-run, and watch the engine **refuse**. 13 tests, CI green, zero runtime deps. |
| **[ratchet](https://github.com/datumstake/ratchet)** | *Automation that cannot grade its own work.* The propose → measure → commit-or-rollback loop that pairs with gapsmith: a workload becomes four commands in a JSON contract, and the measurement — never the proposer — decides what is kept. Works the same on a script, an agent, or a local model. | The demo plants a **deliberately sabotaged move** and you watch the loop roll it back. 8 tests, CI green, zero runtime deps. |
| **[handle](https://github.com/datumstake/handle)** | *A logged-in Chrome, nine verbs.* A CDP driver for sites you did **not** write, driven by a model that can't be trusted to compose a CSS selector: elements are addressed by the number a prior `links()` printed. Sees into shadow roots and types with trusted events — both lessons paid for on a live signup form that defeated the textbook approach. | 10 tests that run **without a browser** (stub CDP), so CI stays hermetic; `examples/demo.py` drives a real one. |
| **[focus-three](https://github.com/datumstake/focus-three)** | *Three tasks, one timer, nothing else.* A native Windows app in **153 KB** — one translation unit, no framework, no installer, no runtime, zero network calls, every control custom-painted so it follows the system light/dark theme including the title bar. The product-polish counterpoint to the systems work. | **[Download](https://github.com/datumstake/focus-three/releases/latest)** and run it — nothing to install. Or **[try the browser demo](https://datumstake.github.io/focus-three/)** first. |

*Next up: what PDFs actually do to you — the defect log from building the extractor above,
every one of which produced a clean build and a plausible wrong answer.*

### Stack

Python · C++17 · TypeScript/Node · local LLMs (Ollama, llama.cpp) · SQLite (FTS) ·
CDP/UIA automation · Windows-first, cross-platform aware

### How I work

Every claim in these repos ships with the command that would fail if it were
wrong — a test, a demo that refuses when you break its premise, a measured
number rather than an assertion. That is the habit the field-services work
taught: *a result with no check beside it is an anecdote.*

### Reach me

📧 **datumstake@gmail.com** · open to contract and consulting engagements
· repos: [pdftext](https://github.com/datumstake/pdftext)
· [gapsmith](https://github.com/datumstake/gapsmith)
· [ratchet](https://github.com/datumstake/ratchet)
· [handle](https://github.com/datumstake/handle)
· [focus-three](https://github.com/datumstake/focus-three)
