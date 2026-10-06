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

| Project | What it demonstrates |
|---|---|
| **[adapt-engine](https://github.com/datumstake/adapt-engine)** | A generic adaptation engine: gap classes resolved from declarative rules, each carrying its own machine-checkable proof. Case study: a small model driving a real porting effort, each change ground-truthed by a compile+link. |
| **[self-verifying-ratchet](https://github.com/datumstake/self-verifying-ratchet)** | The propose/measure/commit-or-rollback loop that pairs with it: a workload is an objective contract, and the measurement — never the proposer — decides what lands. Live demo includes a sabotaged move getting rejected. |

*Next up: the CDP/UIA browser-pilot driver.*

### Stack

Python · TypeScript/Node · local LLMs (Ollama, llama.cpp) · SQLite (FTS) ·
CDP/UIA automation · Windows-first, cross-platform aware

### Reach me

📧 datumstake@gmail.com · open to contract and consulting engagements
