# DARM-ANN — Project Brief

**Cybopsec Research Division · October 2026**
**Status: active working-paper program, pre-publication, under ongoing peer review**
**Public distribution: https://bnreplah.github.io/blog/**

---

## What it is

DARM-ANN (Distributed Agentic Recursive Memory Networks) is a research program arguing that AI memory, consensus, and — eventually — inference substrate should be intrinsic, trainable parts of a distributed network of small models, not services bolted onto a centralized frontier LLM. The core mechanism is a five-tier memory hierarchy gated by a Byzantine-fault-tolerant consensus protocol (CDCP) that decides what becomes persistent, trusted knowledge rather than trusting any single model's output by default.

A separate, less mature extension explores how such a network could be run as decentralized infrastructure — inter-subnet routing, a compute-contribution economy, and a Web3 trust layer — kept deliberately apart from the core architecture because it raises different (and harder) questions.

## Current state, honestly

This is a pre-publication program, not a finished result. It has been through two internal mathematical audits and two rounds of external review (Grok, ChatGPT), which is exactly how one real error was found: a corrected formula for CDCP's safety guarantee was itself wrong, missing a combinatorial factor, and was only caught by actually simulating the protocol rather than re-checking the algebra a second time. That correction — not just the architecture — is part of the public record. A real, working reference implementation of a related (simpler) memory system now exists with measured, not modeled, numbers. An interactive simulator demonstrates the full stack end to end. Nothing here has been independently peer reviewed in the formal sense, and that's stated plainly throughout rather than implied otherwise.

## Document map

| Work | What it covers | Maturity |
|---|---|---|
| **Volume 1 — Core Architecture** | Memory hierarchy, CDCP consensus, neuromorphic substrate, security stack, multi-modal extension, full empirical validation program | Most complete; several proofs independently verified and corrected |
| **Volume 1.1 — Infrastructure Extension** | Inter-subnet routing, compute economy, Web3 trust plane, current industry positioning | Explicitly less mature; marked unreconciled with Volume 1 in several places |
| **Paper 1 — Core DARM-ANN** | CDCP as a standalone, falsifiable admission-control mechanism, with reproducible code | Focused extract of Volume 1, written for outside review |
| **Paper 2 — Epistemic Admission Control** | The "Independence Problem": how much validator correlation degrades consensus-based safety, and what to do about it | Focused extract, with the program's sharpest single finding |
| **Paper 3 — Resource-Aware TinyLM Architecture** | Tiered model routing, speculative decoding economics, energy claims stated as assumptions, not measurements | Focused extract |
| **DARM-ANN PoC** (live simulator) | Interactive, browser-based demonstration of the full stack — memory tiers, consensus, Byzantine attack scenarios, benchmarks | Working demo; being brought into explicit sync with the papers above |
| **sMEM-1** (separate project) | A pragmatic, model-agnostic memory service bridging today's agents to DARM-ANN's eventual architecture | Most empirically grounded piece of the whole program — real measured latency and token-reduction numbers, a real bug found under adversarial testing |

## What's genuinely new here

- **A corrected, quorum-aware safety bound for CDCP**, with the error-finding process documented alongside the fix — not just a cleaner formula, but a worked example of catching it.
- **A concrete, actionable finding**: under correlated validators, raising the admission threshold helps far more than adding nodes — a real design lever, not just a caveat.
- **A falsifiable hypothesis, stated as one**: does more validators actually mean more reliability once they share models and data? Answered partially, quantitatively, with the method shown.
- **Real numbers from a real system** (sMEM-1): sub-millisecond recall at thousands of records, 98%+ reduction in replayed context tokens, one genuine security defect found and fixed during testing.
- **A live, current read on the competitive landscape** — where this work actually sits relative to decentralized compute networks, centralized GPU clouds, and the agent-protocol ecosystem it depends on, researched fresh rather than assumed.

## What's still open

No DARM-ANN checkpoint has been trained or benchmarked; the core architecture has not been validated against real, physically-diverse hardware or models — everything tying its safety claims to "correlation" is a stated model, not yet a measurement. The infrastructure/economic extension raises legal questions (securities treatment of the compute token, among others) that have gotten more favorable recently but still need a lawyer, not a whitepaper, to close out. Several proofs in the reasoning/integrity layer remain unverified for lack of retrievable source material. All of this is stated in the documents themselves, not smoothed over here.

## Where to go next

Start with Volume 1 for the architecture, Papers 1–3 for a narrower read aimed at outside reviewers, and sMEM-1 for the part of this program that already has real data behind it.
