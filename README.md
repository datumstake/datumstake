# Ken Deibel · datumstake

**Systems engineer building local-first AI agents — with a field-services /
geospatial background.** I design harnesses that make small, swappable models do
large, verifiable work: the intelligence lives in the system around the model, not
in any one model's weights. Before software, a heavy background running Trimble
line-of-sight positioning systems in the field — where a wrong answer costs a dug-up
site, so *verification* isn't a nice-to-have.

Available for contract work in AI/agent systems, developer tooling, backend
infrastructure, and software that touches surveying / field-services / geospatial.

---

### What I work on

**Agent harnesses over model fine-tuning.** My main system runs local models through
a persistent, content-addressed memory and a retrieval layer (living RAG) instead of
training — so the same harness keeps working when the model underneath is swapped. The
capability accumulates in tools and records, which means it is inspectable and portable
rather than frozen in a checkpoint.

**Verification-first execution.** A generic self-verifying "ratchet": a workload is
reduced to an objective contract (a metric command, a propose command, a rollback
command), and the engine only keeps a change when the metric *verifiably* improved,
rolling back otherwise. A small model drives real multi-step work — the ground truth,
not the model's self-assessment, decides what lands.

**Browser and desktop automation.** A pilot stack that drives a real browser over CDP
and the Windows desktop over UIA, with the model seeing the page as numbered elements —
used for authenticated workflows a headless scraper can't reach.

### Selected work

**Start here:** [focus-three](https://datumstake.github.io/focus-three/) runs in your
browser right now (one file, nothing to install); if you want the systems work
instead, read [self-verifying-ratchet](https://github.com/datumstake/self-verifying-ratchet)
— it is the shortest statement of how I build.

| Project | What it demonstrates | Proof you can run |
|---|---|---|
| **[adapt-engine](https://github.com/datumstake/adapt-engine)** | A generic adaptation engine: gap classes resolved from declarative rules, each carrying its own machine-checkable proof. Case study: a small model driving a real porting effort, each change ground-truthed by a compile+link. | `python examples/demo.py` shows a proof holding, then **refusing** when you corrupt the asset it checks. 13 tests, CI green, zero runtime deps. |
| **[self-verifying-ratchet](https://github.com/datumstake/self-verifying-ratchet)** | The propose/measure/commit-or-rollback loop that pairs with it: a workload is an objective contract, and the measurement — never the proposer — decides what lands. | The demo plants a **sabotaged move** and you watch it get rolled back. 8 tests, CI green, zero runtime deps. |
| **[browser-pilot](https://github.com/datumstake/browser-pilot)** | A CDP driver that steers a real, logged-in Chrome through a handful of one-word verbs — elements addressed by number, not CSS selector — so a small model can run authenticated workflows a headless scraper can't reach. Documents the Chrome 136 dedicated-profile constraint. | 6 tests that run **without a browser** (stub CDP), so CI stays hermetic; `examples/demo.py` drives a real one. |
| **[focus-three](https://github.com/datumstake/focus-three)** | A complete, dependency-free focus tool in a single offline HTML file: three capped task slots and a Pomodoro timer, state persisted in the browser. The product-polish counterpoint to the systems work. | **[Live demo](https://datumstake.github.io/focus-three/)** — one file, zero dependencies, zero network calls. |

*Next up: a write-up of the living-RAG retrieval pattern — one authority, drawer-scoped, model-agnostic.*

### Stack

Python · TypeScript/Node · local LLMs (Ollama, llama.cpp) · SQLite (FTS) ·
CDP/UIA automation · Windows-first, cross-platform aware

### How I work

Every claim in these repos ships with the command that would fail if it were
wrong — a test, a demo that refuses when you break its premise, a measured
number rather than an assertion. That is the habit the field-services work
taught: *a result with no check beside it is an anecdote.*

### Reach me

📧 **datumstake@gmail.com** · open to contract and consulting engagements
· repos: [adapt-engine](https://github.com/datumstake/adapt-engine)
· [self-verifying-ratchet](https://github.com/datumstake/self-verifying-ratchet)
· [browser-pilot](https://github.com/datumstake/browser-pilot)
· [focus-three](https://github.com/datumstake/focus-three)
