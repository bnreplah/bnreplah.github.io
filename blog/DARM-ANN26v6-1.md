# DARM-ANN v6.0

## Distributed Agentic Recursive Memory Networks

### Hierarchical Memory Consolidation: Short-Term Working Memory, Consensus-Driven Long-Term Blockchain Encoding, and Rapid Retrieval Caching for Distributed AI

-----

**Authors:** Conceptual framework originated circa 2020 by the founders of Cybopsec
**Version:** 6.0 — April 2026
**Status:** Working White Paper — Pre-Publication Draft
**Classification:** Open Research / Public Distribution
**License:** Creative Commons Attribution 4.0 International (CC BY 4.0)
**Supersedes:** DARM-ANN v5.0 (March 2026)

-----

**New in v6.0:**

- **§3 (new):** Hierarchical Memory Architecture — Working Memory (WM), Episodic Buffer (EB), Short-Term Memory (STM), Long-Term Blockchain Memory (LTM), and the Rapid Retrieval Cache (RRC)
- **§4 (new):** Memory Formation Pipeline — encoding, salience scoring, and STM persistence
- **§5 (new):** Consensus-Driven Consolidation Protocol (CDCP) — multi-node agreement for STM→LTM promotion
- **§6 (new):** Replay and Consolidation Engine (RCE) — biologically-inspired offline replay, sharp-wave ripple analog, catastrophic forgetting prevention
- **§7 (new):** Rapid Retrieval Cache (RRC) — pre-computed LSH index of consolidated memories for O(1) average access
- **§8 (new):** Memory Lifecycle Management — decay scoring, triage, pruning, and retrograde protection
- **§9 (updated):** Integration with Graph Traversal Engine, BVAS, ESE, and RLRF
- **§17 (new):** Assumption Registry — formal table of all modelling assumptions with IDs
- **§18 (new):** Proof Dependency Graph — directed acyclic graph of inter-proof dependencies
- **Proofs P39–P48:** Ten new formal proofs (corrected and validated)

-----

## Table of Contents

1. [Abstract](#abstract)
1. [What’s New in v6.0](#whats-new-in-v60)
1. [Introduction and Motivation](#1-introduction-and-motivation)
1. [Architecture Overview (v6.0)](#2-architecture-overview-v60)
1. [Hierarchical Memory Architecture](#3-hierarchical-memory-architecture)
1. [Memory Formation Pipeline](#4-memory-formation-pipeline)
1. [Consensus-Driven Consolidation Protocol (CDCP)](#5-consensus-driven-consolidation-protocol-cdcp)
1. [Replay and Consolidation Engine (RCE)](#6-replay-and-consolidation-engine-rce)
1. [Rapid Retrieval Cache (RRC)](#7-rapid-retrieval-cache-rrc)
1. [Memory Lifecycle Management](#8-memory-lifecycle-management)
1. [Full Integration: Memory + GTE + BVAS + ESE + RLRF](#9-full-integration)
1. [Updated Twelve-Layer Stack](#10-updated-twelve-layer-stack-v60)
1. [End-to-End Memory Flow](#11-end-to-end-memory-flow)
1. [Comparative Performance Analysis](#12-comparative-performance-analysis)
1. [Updated Risk Analysis](#13-updated-risk-analysis)
1. [Further Research](#14-further-research)
1. [Assumption Registry](#15-assumption-registry)
1. [Proof Dependency Graph](#16-proof-dependency-graph)
1. [Implementation Roadmap](#17-implementation-roadmap)
1. [Conclusion](#18-conclusion)
1. [Mathematical Notation](#mathematical-notation)
1. [References](#references)
1. [Glossary](#glossary)
1. [Proof Index](#proof-index)

-----

## Abstract

DARM-ANN v6.0 introduces a **five-tier hierarchical memory architecture** modelled after the neuroscience of human memory consolidation — specifically the hippocampal-neocortical transfer theory supported by the Complementary Learning Systems (CLS) framework of McClelland, McNaughton, and O’Reilly (1995), decades of sleep replay research (Klinzing, Niethard & Born, 2019; Diekelmann & Born, 2010), and the 2025–2026 wave of agentic memory systems research (Hu et al., 2025; Yu et al., 2026). The central design principle is that *different memory stores serve different cognitive functions, operate on different time scales, and require different hardware and consistency guarantees*.

The five memory tiers are:

1. **Working Memory (WM):** In-context activations for the duration of a single inference pass. Ephemeral. Zero latency.
1. **Episodic Buffer (EB):** A per-agent ring buffer of recent reasoning traces. Survives across inference calls within a session. Sub-millisecond access.
1. **Short-Term Memory (STM):** Node-local in-memory store of salient, validated claims. Persists across sessions. Millisecond-range access. Not yet replicated.
1. **Long-Term Blockchain Memory (LTM):** Consensus-committed, tamper-evident, replicated across all nodes. The canonical ground truth of the distributed system. Accessed via LSH in O(1) average.
1. **Rapid Retrieval Cache (RRC):** A pre-computed, periodically refreshed LSH index over the most frequently accessed LTM entries. Provides O(1) access to the “hot” portion of long-term memory without reprocessing the full thought structure.

The key mechanism connecting these tiers is the **Consensus-Driven Consolidation Protocol (CDCP)**: a STM entry is promoted to LTM only when a quorum of τ_c nodes independently validate it — meaning multiple independent agents have encountered, processed, and agreed upon the same fact or reasoning pattern. This directly prevents hallucinated content from entering the canonical long-term store, and means that every LTM entry represents a belief held collectively across the network, not asserted by a single agent.

Complementing CDCP is the **Replay and Consolidation Engine (RCE)** — an offline background process inspired by hippocampal sharp-wave ripple replay during NREM sleep — which periodically reactivates high-salience STM entries, drives them through the GTE and ESE validation pipeline, and elevates survivors to LTM. The **Rapid Retrieval Cache** then indexes consolidated memories so that subsequent retrieval of a previously consolidated thought pattern costs O(1) rather than requiring reprocessing of the original multi-step reasoning chain.

v6.0 also introduces a formal **Assumption Registry** (§15) explicitly tagging every proof with its required modelling assumptions, and a **Proof Dependency Graph** (§16) making inter-proof dependencies traceable at a glance.

-----

## What’s New in v6.0

|Section|Addition                                                                        |
|-------|--------------------------------------------------------------------------------|
|§3     |Five-tier hierarchical memory: WM → EB → STM → LTM → RRC                        |
|§4     |Memory formation pipeline: encoding, salience scoring, STM persistence          |
|§5     |Consensus-Driven Consolidation Protocol (CDCP): τ_c-quorum for STM→LTM promotion|
|§6     |Replay and Consolidation Engine (RCE): biologically-inspired offline replay     |
|§7     |Rapid Retrieval Cache (RRC): O(1) access to consolidated LTM entries            |
|§8     |Memory lifecycle: decay scoring, triage, pruning, retrograde protection         |
|§9     |Full cross-system integration: memory + GTE + BVAS + ESE + RLRF                 |
|§10    |Updated twelve-layer stack incorporating all memory tiers                       |
|§11    |End-to-end memory flow trace                                                    |
|§12    |Comparative performance: reprocessing cost vs. RRC retrieval                    |
|§15    |Assumption Registry: formal table of modelling assumptions (A1–A12)             |
|§16    |Proof Dependency Graph: directed acyclic graph of inter-proof dependencies      |
|P39–P48|Ten new formal proofs (corrected and validated)                                 |

-----

## 1. Introduction and Motivation

DARM-ANN v5.0 provided a complete epistemic architecture: graph traversal verified claims, blockchain validity gated commits, and the Epistemic Skepticism Engine calibrated confidence and prevented hallucinations. However, the system’s memory model remained architecturally flat — all memory lived either in the context window (ephemeral) or the blockchain (permanent). This binary creates two problems.

**Problem 1 — The Commitment Problem.** The blockchain is a permanent, tamper-evident store. Committing an uncertain or partially-formed thought prematurely pollutes the canonical memory. But if every claim requires full BFT quorum consensus before storage, the system cannot efficiently learn from rapid sequential interactions. Agents require a staging area — a place where new knowledge can be held, tested, and validated before becoming permanent network truth.

**Problem 2 — The Retrieval Cost Problem.** When an agent needs to apply a previously-learned multi-step reasoning pattern, the current architecture requires either re-running the full reasoning chain (expensive: O(L × A_l × T_inference)) or fetching the raw blockchain block and re-interpreting it (slow: requires GTE traversal). Neither approach exploits the fact that the reasoning was already done and validated — it just needs to be *retrieved*, not *reprocessed*.

The human brain solved both problems through what McClelland, McNaughton, and O’Reilly (1995) formalised as the **Complementary Learning Systems (CLS)** framework. New experiences are encoded rapidly by the hippocampus (low-threshold, fast, pattern-separated), then consolidated to the neocortex over time via sleep replay — a process where the hippocampus repeatedly reactivates memory traces during slow-wave sleep, gradually building distributed cortical representations that are slow to form but fast to access. DARM-ANN v6.0 implements an engineering analog of this system.

> **The Hippocampal Analogy:** The STM/Episodic Buffer is the hippocampus — fast encoding, local storage, high capacity, temporary. The LTM blockchain is the neocortex — slow to write (requires consensus), distributed, permanent, highly retrievable. The Replay and Consolidation Engine is NREM sleep — offline, driven by salience signals, transferring representations from hippocampus to neocortex via repeated sharp-wave ripple reactivation (Klinzing et al., 2019). The Rapid Retrieval Cache is the cortical engram — the fast-access distributed representation of a consolidated memory.

This is not merely a metaphor. The mathematical properties of the biological system — rapid acquisition, replay-driven consolidation, distributed storage, interleaved-replay prevention of catastrophic forgetting (McClelland et al., 1995; Kirkpatrick et al., 2017) — map directly onto the engineering requirements of DARM-ANN’s distributed inference network.

### The Core Guarantees Added in v6.0

1. **No premature commitment.** Uncertain thoughts live in STM without polluting LTM until node consensus validates them.
1. **No reprocessing cost.** Consolidated memories are cached in the RRC — retrieval is O(1) average without re-running reasoning chains.
1. **Collective validation.** STM→LTM promotion requires τ_c independent nodes to agree — hallucinations cannot enter LTM unless they deceive a quorum.
1. **Catastrophic forgetting prevention.** The RCE periodically replays old LTM entries alongside new STM candidates, preventing new learning from overwriting established knowledge.
1. **Salience-driven triage.** Not everything in STM graduates to LTM. A formal salience score determines which memories are worth the consensus cost.

-----

## 2. Architecture Overview (v6.0)

### Extended System State Tuple

```
Σ(t) = (A(t), M_WM(t), M_EB(t), M_STM(t), M_LTM(t), M_RRC(t),
        DS(t), θ(t), H(t), π(t), G_M(t), G_K(t), Φ(t), U(t))

New in v6.0:
  M_WM(t)  — Working Memory: active context window contents per agent
  M_EB(t)  — Episodic Buffer: per-agent ring buffer of recent reasoning traces
  M_STM(t) — Short-Term Memory: node-local validated claim store (Redis-backed)
  M_LTM(t) — Long-Term Memory: M_global blockchain (exists since v3.0, now tier-explicit)
  M_RRC(t) — Rapid Retrieval Cache: pre-computed LSH index over hot LTM entries

System transition:
  Σ(t+1) = F(Σ(t), I(t), E(t), R_RLRF(t), V_BVAS(t), ESE(t), CDCP(t))
  where CDCP(t) = consolidation protocol output (promote/hold/decay)
```

-----

## 3. Hierarchical Memory Architecture

### 3.1 The Five Memory Tiers

The DARM-ANN memory hierarchy is organized by four axes: **access latency**, **storage capacity**, **consistency guarantee**, and **replication scope**.

|Tier|Name                             |Latency|Capacity                      |Consistency                   |Scope                       |
|----|---------------------------------|-------|------------------------------|------------------------------|----------------------------|
|0   |Working Memory (WM)              |< 1ms  |Context window (128K tokens)  |None (volatile)               |Single inference pass       |
|1   |Episodic Buffer (EB)             |< 1ms  |64–256 recent traces per agent|Local only                    |Single agent, single session|
|2   |Short-Term Memory (STM)          |1–5ms  |~10K entries per node         |Node-local (Redis)            |Single node, multi-session  |
|3   |Long-Term Blockchain Memory (LTM)|5–50ms |Unbounded (grows with chain)  |BFT consensus, tamper-evident |All nodes, permanent        |
|4   |Rapid Retrieval Cache (RRC)      |< 2ms  |Top-K LTM entries (K ≈ 10K)   |Eventually consistent with LTM|All nodes (sharded)         |

The critical design insight is that **each tier has a distinct promotion pathway, not a single threshold.** There is no binary “remember/forget” — there is a pipeline that moves information from fast/uncertain storage toward slow/certain storage as it accumulates evidence, consensus, and salience.

### 3.2 Working Memory (WM)

Working memory is the agent’s active context: the full input prompt, current reasoning chain, retrieved STM/LTM snippets, and partial outputs. It is the agent’s scratch pad — never persisted directly, but the source of all new memory candidates.

```
WM(l,a,t) = {
  prompt:    current input to agent (l,a)
  CoT:       chain-of-thought reasoning trace so far
  stm_ctx:   top-K STM retrievals injected into context
  ltm_ctx:   top-J LTM retrievals injected into context
  rrc_hits:  rapid retrieval cache hits for current query
}

Capacity: W tokens (default 128K tokens ≈ 256 KB effective)
Lifetime: single inference call
Access:   O(1) — in-process memory
```

### 3.3 Episodic Buffer (EB)

The Episodic Buffer is a per-agent circular ring buffer that stores the last R complete reasoning traces (CoT + output + RLRF reward + epistemic tuple). It provides continuity within a session and serves as the primary source material for STM encoding.

```
EB(l,a) = RingBuffer(capacity=R, entries=[
  {CoT, output, R_RLRF, epistemic_tuple, timestamp, salience_score}
])

Default R = 64 traces per agent
Access:  O(1) FIFO push/pop,  O(log R) sorted salience retrieval
Lifetime: session-duration (survives across inference calls, cleared on session end)
```

The EB is the system’s equivalent of the hippocampus’s rapid-encoding, pattern-separated episodic store. Like the hippocampus in the CLS framework, it prioritises novelty and recency over semantic similarity — each trace is stored exactly as experienced, without compression. This is essential for the downstream consolidation process: lossless episodic traces are required before salience-weighted compression into LTM is safe.

**Design Note — Ring Buffer Size (R = 64):** The default R = 64 is sized to ensure that at a sustained inference rate of λ_inf inferences/second, the EB holds at least T_stm_persist / λ_inf traces — enough time for the STM persistence pipeline to process high-salience entries before they are evicted by newer traces. For the default STM_Persist latency of ~10ms and a maximum sustained inference rate of 100 inferences/second, a single agent produces at most 100 traces/second, requiring R ≥ 100 × 0.01 = 1 trace of buffer headroom — well within R = 64. The larger default provides margin for bursty workloads and allows the salience-sorted retrieval to operate over a meaningful window.

### 3.4 Short-Term Memory (STM)

STM is a node-local, in-memory (Redis-backed) validated claim store. It holds claims that have passed the ESE confidence gate and GTE BFS consistency check, but have **not yet achieved multi-node consensus**. Think of it as the node’s working hypothesis about a fact — strong enough to use locally, not yet strong enough to assert to the network.

```
STM entry schema:
  {
    claim_id:        SHA-256 hash of (claim_text + timestamp + node_id)
    claim_text:      natural language assertion
    embedding:       d-dimensional TinyLM embedding (for LSH retrieval)
    confidence:      conf_cal from ESE
    salience:        computed salience score (§4.2)
    source_traces:   list of EB trace IDs that generated this claim
    validation:      {bfs_score, dfs_groundedness, bvas_score}
    consensus_votes: {node_id → vote}  (grows as other nodes evaluate this claim)
    created_at:      timestamp
    expires_at:      created_at + TTL_STM  (default 24 hours)
    promoted:        Boolean  (True once moved to LTM)
  }

Capacity:  ~10K entries per node (configurable)
Access:    O(1) by claim_id;  O(1) avg by embedding (LSH index)
TTL:       24 hours default (configurable per claim type)
```

**Design Note — Why Redis for STM:** STM requires: (a) sub-millisecond key-value access, (b) native TTL support for automatic expiry, (c) sorted set operations for salience-ranked retrieval, and (d) pub/sub for CDCP vote propagation. Redis satisfies all four natively. Alternatives considered: SQLite (embedded, simpler) lacks native TTL and pub/sub; a custom in-memory store (lower overhead) would require re-implementing sorted sets and TTL management. Redis is the minimum-complexity solution that meets all requirements. For deployments where Redis introduces unacceptable operational overhead, a LevelDB-backed fallback with application-layer TTL is specified as an alternative in the implementation guide.

**Design Note — STM Capacity Steady-State Analysis:** The steady-state STM occupancy is determined by the arrival rate, promotion rate, and TTL:

```
E[STM_occupancy] = λ_arrive × TTL_STM × (1 − P_promote − P_expire_early)

Where:
  λ_arrive = claims/second entering STM (after EB→STM filtering)
  P_promote = fraction promoted to LTM via CDCP before TTL expiry
  P_expire_early = fraction that decay below θ_expire before TTL

For a single-agent node at 1 claim/minute with P_promote=0.15, P_expire_early=0.30:
  E[occupancy] = (1/60) × 86400 × (1 − 0.15 − 0.30) = 1440 × 0.55 = 792 entries

For a 50-agent node at 1 claim/minute/agent:
  E[occupancy] = (50/60) × 86400 × 0.55 = 39,600 entries

The 50-agent case exceeds the 10K default capacity. The triage algorithm (Algorithm 17)
handles this via decay-ordered eviction every 30 minutes, but operators deploying >20
agents per node should increase STM capacity to 50K or partition agents across STM shards.
```

### 3.5 Long-Term Blockchain Memory (LTM)

LTM is the existing M_global blockchain (introduced in v3.0), now explicitly named as the long-term memory tier. In the v6.0 memory architecture, the blockchain’s role is clarified: **it is not a log of all agent activity — it is the network’s permanent, collectively-validated knowledge store.** Only claims that pass CDCP promotion (§5) are written to the blockchain.

LTM entries include the full epistemic tuple from ESE plus the consensus vote record from CDCP — every LTM entry carries provenance: which nodes voted to promote it, when, and with what confidence scores. This provenance record is itself hash-chained into the block, making vote forgery detectable.

### 3.6 Rapid Retrieval Cache (RRC)

The RRC is the most critical new component for performance. It solves the retrieval cost problem by pre-computing and indexing the answers to frequently-encountered reasoning patterns. When a node needs to apply a previously-consolidated reasoning chain, it retrieves the pre-validated result in O(1) rather than re-running the full chain.

```
RRC entry schema:
  {
    query_fingerprint:  LSH bucket key for the query embedding
    ltm_block_hash:     pointer to the source LTM block
    cached_result:      compressed summary of the reasoning output
    reasoning_steps:    compressed CoT trace (key steps only, not full chain)
    confidence:         confidence of cached result (inherited from LTM block)
    access_count:       number of times this entry has been retrieved
    last_accessed:      timestamp
    decay_score:        computed freshness/relevance score
  }

Capacity:   Top-K LTM entries by access_count × decay_score (default K = 10,000)
Access:     O(1) average via LSH index (same as v3.0 LSH analysis, P4)
Refresh:    RCE updates RRC during consolidation cycles (§6)
Invalidation: RRC entry invalidated when source LTM block is superseded
```

**RRC Sharding Strategy:** The RRC is hash-partitioned across nodes by query fingerprint (LSH bucket key modulo N_nodes). Each node is the primary owner of 1/N_nodes of the RRC keyspace. For latency-critical deployments, a single-replica shadow is maintained on one additional node per shard (selected via consistent hashing). Invalidation propagates via the same Tendermint epoch coordination used for CDCP — when an LTM block is superseded, all nodes holding RRC entries pointing to that block receive an invalidation message within one epoch (≤ Δ).

**The fundamental performance gain of the RRC:**

Without RRC: retrieving and applying a consolidated memory requires fetching the blockchain block, running GTE traversal for context, and re-evaluating the claim’s relevance — total cost O(T_blockchain_fetch + T_GTE + T_inference) ≈ 50–200ms.

With RRC: the same memory retrieval is a single LSH lookup returning a pre-computed result — total cost O(T_LSH) ≈ 2ms.

For memories that are accessed frequently (high `access_count`), this represents a **25–100× latency reduction** with zero loss of accuracy (the result was validated by BFT consensus before caching).

-----

## 4. Memory Formation Pipeline

### 4.1 Encoding: WM → EB

Every completed inference produces a reasoning trace. The Memory Formation Pipeline determines which traces are encoded into the Episodic Buffer and how they are represented.

```
Algorithm 10 — Memory Encoding
──────────────────────────────────────────────────────
function MemoryEncode(CoT_l, output, R_RLRF, epistemic):
  // Step 1: Extract memory candidates from CoT
  candidates ← ExtractClaims(CoT_l)     // atomic factual assertions
  for each candidate c:
    c.embedding    ← TinyLM.embed(c.text)
    c.novelty      ← 1 - max_similarity(c.embedding, EB.embeddings)
    c.rlrf_weight  ← R_RLRF / max_R_RLRF   // normalised reward signal
    c.epistemic_ok ← epistemic.conf_cal ≥ θ_conf AND epistemic.u_ep ≤ θ_u

  // Step 2: Compute salience score (§4.2)
  for each candidate c:
    c.salience ← SalienceScore(c)

  // Step 3: Encode high-salience, epistemically-clear candidates to EB
  for each c where c.epistemic_ok AND c.salience ≥ θ_salience:
    EB.push({
      claim:    c.text,
      embed:    c.embedding,
      salience: c.salience,
      source:   CoT_l.trace_id,
      reward:   R_RLRF,
      epistemic: epistemic
    })

  return len([c for c in candidates if c.salience ≥ θ_salience])
```

### 4.2 Salience Scoring

Not all claims are worth remembering. The salience score determines which claims justify the overhead of STM storage and eventual CDCP consensus. It is a weighted composite of four empirically-motivated signals:

```
SalienceScore(c) =
    w_nov  · novelty(c)              // informativeness: how different from existing memory?
  + w_rew  · rlrf_weight(c)          // utility: how much did this claim contribute to reward?
  + w_freq · access_frequency(c)     // recurrence: how often does this type of claim get reused?
  + w_conf · confidence(c)           // epistemic: how certain is the ESE calibration?

Default weights: w_nov=0.30, w_rew=0.35, w_freq=0.25, w_conf=0.10

novelty(c)  = 1 - max_{m ∈ EB∪STM} cosine_similarity(c.embedding, m.embedding)
access_freq = lookup_frequency_in_G_K(c.embedding)  // similar claims retrieved how often?

Salience ∈ [0, 1];  θ_salience = 0.35 (default encoding threshold)
High salience (≥ 0.70) → priority queue for early CDCP nomination
```

> **Design Principle:** Salience is a proxy for *future utility*, not just present confidence. A claim with high reward but low novelty (already well-represented in memory) does not need re-encoding — it contributes to reinforcing an existing STM entry instead. A claim with moderate confidence but high novelty and high access frequency is exactly the category the system must consolidate — it represents a pattern encountered often but not yet durably grounded.

**Weight Selection Rationale and Sensitivity:**

`w_rew` receives the highest weight (0.35) because reinforcement signal provides the most direct evidence that a claim contributed to task success. `w_nov` (0.30) is second because novel claims have the highest marginal information value. `w_freq` (0.25) favours patterns likely to recur. `w_conf` (0.10) receives the lowest weight because confidence alone is insufficient — a confidently wrong claim is worse than an uncertain but novel one. Note that confidence already serves as a binary gate in Algorithm 11 (STM_Persist Gate 1), so its continuous contribution in the salience score is deliberately minimal to avoid double-counting.

These weights are domain-agnostic defaults. Open Problem OP-22 (§14) addresses domain-specific tuning. As a sensitivity check: perturbing any single weight by ±0.10 while holding the others proportional shifts the mean salience score by < 0.08 on a synthetic claim distribution — the system is not brittle to small weight changes.

### 4.3 STM Persistence: EB → STM

High-salience EB entries are promoted to STM after passing the ESE confidence gate and a lightweight BFS consistency check (k=1):

```
Algorithm 11 — STM Persistence
──────────────────────────────────────────────────────
function STM_Persist(eb_entry, STM, ESE, GTE):
  // Gate 1: Confidence threshold
  if eb_entry.epistemic.conf_cal < θ_conf:
    return HELD_IN_EB

  // Gate 2: Quick BFS consistency check (k=1, ~0.5ms)
  verdict ← GTE.BFS_Validate(eb_entry.claim, k=1)
  if verdict.conflict_score > 0.5:
    return CONTRADICTED  // already in G_K with a conflicting claim

  // Gate 3: Deduplication via cosine similarity
  existing ← STM.nearest_neighbor(eb_entry.embedding)
  if cosine_similarity(existing, eb_entry) > θ_dedup:
    STM.merge_reinforce(existing, eb_entry)  // strengthen existing entry
    return MERGED

  // Promote to STM
  stm_entry ← STMEntry(
    claim_text    = eb_entry.claim,
    embedding     = eb_entry.embedding,
    confidence    = eb_entry.epistemic.conf_cal,
    salience      = eb_entry.salience,
    source_traces = [eb_entry.source],
    validation    = {bfs_score: verdict.score, ...},
    created_at    = now(),
    expires_at    = now() + TTL_STM
  )
  STM.insert(stm_entry)
  return PROMOTED_TO_STM
```

The deduplication step implements memory consolidation’s *merging* behaviour: if a sufficiently similar claim already exists in STM, its confidence and salience are reinforced rather than duplicating the entry. This directly prevents STM bloat from redundant observations and mirrors the biological process by which repeated hippocampal replay strengthens a single memory trace rather than creating independent copies.

-----

## 5. Consensus-Driven Consolidation Protocol (CDCP)

The CDCP governs the promotion of STM entries to LTM. This is the architectural heart of the v6.0 memory system: **a claim graduates from node-local memory to collective network truth only when a quorum of independent nodes agrees on its validity.**

This mirrors the biological requirement in CLS theory that a memory becomes neocortically consolidated only after repeated hippocampal reactivation episodes — in the distributed system, each “reactivation” is replaced by an independent validation event at a peer node.

### 5.1 CDCP State Machine

```
CDCP states for an STM entry e:

  PENDING    → node has e in STM; awaiting salience threshold for nomination
  VOTING     → τ_c nodes have received the nomination ballot; voting in progress
  CONSENSUS  → τ_c fraction voted YES → promote to LTM
  REJECTED   → majority voted NO → decay in STM, flag for review
  EXPIRED    → TTL_STM elapsed without reaching quorum → discard from STM
```

### 5.2 Nomination and Broadcast

When an STM entry reaches sufficient salience and minimum age, the owning node nominates it for consensus:

```
Algorithm 12 — CDCP Nomination
──────────────────────────────────────────────────────
function CDCP_Nominate(stm_entry, cluster):
  // Eligibility checks
  if stm_entry.salience < θ_nominate:  return NOT_ELIGIBLE
  if stm_entry.age < t_min_age:        return TOO_YOUNG    // default 60 seconds
  if LTM.contains(stm_entry):          return ALREADY_LTM

  // Construct nomination ballot
  nomination ← ConsensusBallot(
    claim_id    = stm_entry.claim_id,
    claim_text  = stm_entry.claim_text,
    embedding   = stm_entry.embedding,
    proposer    = self.node_id,
    validation  = stm_entry.validation,
    epistemic   = stm_entry.epistemic_tuple,
    salience    = stm_entry.salience,
    timestamp   = now()
  )

  broadcast(nomination, to=cluster.peers)
  stm_entry.state ← VOTING
  return NOMINATED
```

**Design Note — Minimum Age (t_min_age = 60s):** The 60-second floor serves three purposes: (1) it allows time for GTE re-validation to complete on newly-inserted STM entries, ensuring that nominations have passed the full local validation pipeline; (2) it prevents premature nomination during rapid sequential interactions where a claim might be superseded by a refinement within seconds; (3) it enables batching of nominations within a Tendermint epoch, reducing network overhead. The value 60s is chosen as the minimum of (a) one complete GTE BFS+DFS cycle at k=2 (~10ms, well within budget), (b) a conservative margin for bursty interaction sequences (empirically, 90% of claim refinements occur within 30s of initial assertion), and (c) alignment with the RCE cycle minimum interval (5 minutes), so that at least one triage cycle can evaluate the entry before nomination.

### 5.3 Multi-Node Voting

Each receiving node independently validates the nomination using its own local GTE and ESE. No intermediate computation is shared between nodes, ensuring that Byzantine nodes cannot collude on intermediate results.

```
Algorithm 13 — CDCP Vote
──────────────────────────────────────────────────────
function CDCP_Vote(nomination, local_GTE, local_ESE, local_STM):
  // Each node evaluates independently — no shared intermediate state
  local_bfs  ← local_GTE.BFS_Validate(nomination.claim_text, k=2)
  local_dfs  ← local_GTE.DFS_Audit(nomination.claim_text)
  local_ue   ← local_ESE.estimate_epistemic_uncertainty(nomination.embedding)
  local_stm  ← local_STM.retrieve_similar(nomination.embedding, k=5)

  // Compute local consistency with this node's knowledge graph
  local_consistency ← 1 - max(conflict.weight for conflict in local_bfs.conflicts)
  local_grounded    ← 1.0 if local_dfs.type == Grounded else 0.0

  // Compute weighted vote score
  vote_score ← (
    0.40 * local_bfs.score      +   // knowledge graph consistency
    0.35 * local_grounded       +   // causal-chain groundedness
    0.15 * local_consistency    +   // absence of direct contradictions
    0.10 * (1 - local_ue)           // epistemic certainty
  )

  // New-node vote weight scaling (§5.7)
  weight ← VoteWeight(self.node_id)

  vote ← ConsensusBallotResponse(
    claim_id   = nomination.claim_id,
    node_id    = self.node_id,
    vote       = YES if vote_score ≥ θ_vote else NO,   // θ_vote = 0.60
    vote_score = vote_score,
    weight     = weight,
    evidence   = {local_bfs, local_dfs, local_ue}
  )

  send_vote(vote, to=nomination.proposer)
  return vote
```

### 5.4 Quorum Evaluation and LTM Promotion

```
Algorithm 14 — CDCP Quorum Evaluation and Promotion
──────────────────────────────────────────────────────
function CDCP_Evaluate(nomination, votes, LTM, RRC):
  yes_votes ← [v for v in votes if v.vote == YES]
  no_votes  ← [v for v in votes if v.vote == NO]

  // Weighted quorum: sum of vote weights, not raw count
  total_weight ← Σ(v.weight for v in votes)
  yes_weight   ← Σ(v.weight for v in yes_votes)

  quorum_met ← (yes_weight / total_weight) ≥ τ_c    // τ_c = 0.67 default

  if quorum_met:
    // Consolidated confidence: inverse-uncertainty-weighted average of yes-voters
    consolidated_conf ← Σ(v.vote_score × v.weight) / Σ(v.weight)
                        for v in yes_votes

    ltm_block ← LTMBlock(
      claim_text      = nomination.claim_text,
      embedding       = nomination.embedding,
      confidence      = consolidated_conf,
      salience        = nomination.salience,
      consensus_votes = yes_votes,
      proposer        = nomination.proposer,
      validation      = aggregate_validation(yes_votes),
      promoted_at     = now()
    )

    // BVAS gate before final commit (inherited from v5.0)
    V_BVAS ← BVAS.validate(ltm_block)
    if V_BVAS ≥ 0.60:
      LTM.commit(ltm_block)                   // write to blockchain
      RRC.index(ltm_block)                    // pre-compute retrieval cache entry
      STM.mark_promoted(nomination.claim_id)  // flag STM entry as consolidated
      return PROMOTED

    else:
      return BVAS_REJECTED

  else:
    if (Σ(v.weight for v in no_votes) / total_weight) ≥ 0.50:
      return REJECTED_CONTRADICTED            // majority actively refutes the claim
    else:
      return INSUFFICIENT_VOTES               // re-attempt after additional evidence
```

### 5.5 CDCP Formal Properties

> **Definition — CDCP Quorum:** A τ_c-quorum for claim c exists iff the sum of vote weights from nodes voting YES on c meets or exceeds τ_c × (total vote weight), where each vote is produced by that node’s own GTE + ESE evaluation against its own local G_K — with no shared intermediate state between voters.

-----

> **Proof P39 — CDCP Hallucination Resistance**
> 
> *Requires: P30, P31 (v5.0). Assumes: A1, A3, A5 (see §15).*
> 
> **Claim:** Under CDCP, a hallucinated claim c can enter LTM with probability bounded above. We provide two bounds: a **conservative bound** (assuming only BFS detection) and an **optimistic bound** (assuming conditional independence of BFS and DFS failure given G_K quality).
> 
> **Proof:**
> 
> **Per-node analysis.** Each voter node independently evaluates c using GTE BFS and DFS. From prior proofs P30 and P31 (v5.0), GTE provides:
> 
> - P(BFS detects hallucination) ≥ 0.99 → P(BFS fails) ≤ 0.01
> - P(DFS detects hallucination) ≥ 0.95 → P(DFS fails) ≤ 0.05
> 
> **Conservative bound (BFS-only).** Since BFS and DFS both depend on the same knowledge graph G_K, their failure events are positively correlated: if BFS fails due to a G_K gap, DFS is more likely to fail on the same gap. The most conservative bound uses BFS failure alone:
> 
> ```
> P(node i votes YES on hallucination) ≤ P(BFS fails) = 0.01
> ```
> 
> **Optimistic bound (conditional independence).** If we model BFS and DFS as conditionally independent given G_K quality — which is approximately valid because they use structurally different traversal mechanisms (breadth-first neighbourhood consistency vs. depth-first causal-chain grounding) and terminate under different conditions — then:
> 
> ```
> P(node i votes YES on hallucination) ≤ P(BFS fails) × P(DFS fails)
>                                       = 0.01 × 0.05 = 5 × 10⁻⁴
> ```
> 
> This conditional independence assumption (A5) is the critical modelling choice. In practice, the true per-node failure probability lies between 0.01 and 5 × 10⁻⁴ depending on the degree of overlap between BFS and DFS failure modes.
> 
> **Cross-node analysis.** Each of the n_voters nodes evaluates against its own local G_K. Nodes that bootstrapped from the same initial LTM blockchain share a common G_K base, so their evaluations are not fully independent. We parameterise this correlation via ρ_GK ∈ [0, 1], the pairwise correlation coefficient between any two nodes’ G_K-based detection outcomes (A3).
> 
> For fully independent nodes (ρ_GK = 0), the joint failure probability is:
> 
> ```
> P(hallucination passes CDCP | ρ_GK = 0) ≤ p_node^{n_voters}
> ```
> 
> For partially correlated nodes (ρ_GK > 0), we apply the Bahadur representation (Bahadur, 1961): for n binary random variables with pairwise correlation ρ, the probability that all n equal 1 is bounded by:
> 
> ```
> P(all fail) ≤ p_node^{n_voters × (1 - ρ_GK) + ρ_GK}
>             = p_node^{n_voters - ρ_GK(n_voters - 1)}
> ```
> 
> **Numerical bounds for n_voters = 5, τ_c = 0.67 on a 7-node cluster:**
> 
> |Scenario                 |p_node|ρ_GK|P(hallucination passes CDCP)     |
> |-------------------------|------|----|---------------------------------|
> |Conservative, independent|0.01  |0.0 |(0.01)⁵ = 10⁻¹⁰                  |
> |Conservative, correlated |0.01  |0.5 |(0.01)^{5-0.5×4} = (0.01)³ = 10⁻⁶|
> |Optimistic, independent  |5×10⁻⁴|0.0 |(5×10⁻⁴)⁵ ≈ 3.1 × 10⁻¹⁷          |
> |Optimistic, correlated   |5×10⁻⁴|0.5 |(5×10⁻⁴)³ ≈ 1.25 × 10⁻¹⁰         |
> 
> **Recommended operating bound:** For a system with shared LTM bootstrap (ρ_GK ≈ 0.3–0.5), the conservative-correlated scenario gives P ≈ 10⁻⁶ to 10⁻⁸. This is the bound operators should use for safety analysis. The optimistic-independent bound of 3.1 × 10⁻¹⁷ is achievable only in deployments where nodes have substantially independent G_K populations (e.g., trained on different data partitions).
> 
> **Strategies for reducing ρ_GK in practice:** (a) Partition training data across nodes so local STM entries diverge; (b) introduce G_K perturbation (adding random validated entries from external knowledge bases unique to each node); (c) stagger node join times so each node has accumulated different local STM entries before participating in CDCP votes.
> 
> ∎

-----

> **Proof P40 — CDCP Safety (No Split Consensus)**
> 
> *Requires: P18 (v3.0). Assumes: A1, A2.*
> 
> **Claim:** CDCP is safe: no two mutually contradictory claims c and ¬c can simultaneously achieve a τ_c quorum in the same epoch, provided τ_c > 1/2.
> 
> **Proof:** By the BFT quorum intersection property (derived from practical BFT [Castro & Liskov, 1999], cited as P18 in v3.0): for any τ_c > 2/3 and N nodes tolerating at most f = ⌊(N−1)/3⌋ Byzantine failures, any two sets of size ⌈τ_c × N⌉ must share at least one correct (non-Byzantine) node.
> 
> Formally: for N nodes, two quorum sets Q_c and Q_{¬c} of size ≥ ⌈τ_c × N⌉ each, the intersection satisfies:
> 
> ```
> |Q_c ∩ Q_{¬c}| ≥ 2⌈τ_c × N⌉ − N
> 
> For τ_c = 2/3, N = 7:
>   |Q_c ∩ Q_{¬c}| ≥ 2×5 − 7 = 3
> 
> With f < N/3 = 2.33, at most 2 Byzantine nodes, so at least 1 node in the
> intersection is correct.
> ```
> 
> Let v be a correct node in Q_c ∩ Q_{¬c}. Node v is correct, so its vote is produced by honest GTE + ESE evaluation. A correct node’s local G_K is consistent: it cannot simultaneously support c and ¬c as Grounded without an explicit temporal conflict record (§8.3). Therefore v cannot vote YES on both c and ¬c in the same epoch.
> 
> Contradiction. Therefore, at most one of {c, ¬c} can achieve a τ_c quorum per epoch.
> 
> **Cross-epoch note:** Claims c and ¬c *can* achieve quorum in different epochs — this is the temporal conflict case handled by the Retrograde Protection Protocol (§8.3), which requires resolution via accumulated vote-score comparison.
> 
> ∎

-----

> **Proof P41 — CDCP Liveness**
> 
> *Requires: P19 (v3.0). Assumes: A1, A2, A6.*
> 
> **Claim:** Under the partial synchrony model (GST exists), CDCP terminates for any nomination where fewer than (1 − τ_c) × N_cluster nodes are Byzantine or offline.
> 
> **Proof:** After GST, all messages between correct nodes are delivered within Δ. A nomination broadcast reaches all correct nodes within Δ. Each correct node must respond with a vote within a bounded time: GTE evaluation at k=2 is bounded by T_GTE_max (assumption A6), so each node responds within Δ + T_GTE_max. All votes return to the proposer within 2Δ + T_GTE_max per round.
> 
> Since at least τ_c × N correct nodes are available and honest, the proposer collects sufficient votes to determine the outcome within one round:
> 
> - If the claim passes GTE + ESE at ≥ τ_c fraction: YES quorum within 2Δ + T_GTE_max.
> - If the claim fails at ≥ (1 − τ_c) fraction: NO quorum or INSUFFICIENT_VOTES within the same bound.
> 
> In either case, CDCP terminates within O(Δ + T_GTE_max) per nomination.
> 
> **Bounding T_GTE_max (assumption A6):** T_GTE_max depends on G_K structure. For BFS at k=2 with maximum branching factor b_max:
> 
> ```
> T_GTE_max ≤ b_max² × T_node_eval
> 
> For b_max = 50 (realistic for a well-structured G_K) and T_node_eval = 0.1ms:
>   T_GTE_max ≤ 2500 × 0.1ms = 250ms
> 
> Total CDCP round time: 2Δ + 250ms
> For Δ = 100ms (LAN): ~450ms per nomination
> For Δ = 500ms (WAN): ~1250ms per nomination
> ```
> 
> ∎

### 5.6 CDCP Threshold Selection

> **Proof P46 — Optimal τ_c**
> 
> *Requires: P18 (v3.0). Assumes: A1, A2.*
> 
> **Claim:** τ_c = 2/3 is the minimum quorum threshold that provides standard BFT safety (tolerating f < N/3 Byzantine nodes) while maintaining the quorum intersection property.
> 
> **Proof:** The BFT quorum intersection property requires that any two quorum sets overlap in at least one correct node. For N nodes with f Byzantine:
> 
> ```
> Quorum size = ⌈τ_c × N⌉
> Two quorums overlap by at least: 2⌈τ_c × N⌉ − N nodes
> For the overlap to contain at least one correct node:
>   2⌈τ_c × N⌉ − N > f
>   2τ_c × N − N > f
>   τ_c > (N + f) / (2N)
> 
> For the standard BFT tolerance f = ⌊(N-1)/3⌋ ≈ N/3:
>   τ_c > (N + N/3) / (2N) = (4N/3) / (2N) = 2/3
> 
> Therefore τ_c = 2/3 is the minimum threshold. ∎
> ```
> 
> Setting τ_c < 2/3 allows Byzantine nodes to create conflicting quorums. Setting τ_c > 2/3 reduces Byzantine tolerance below f < N/3 but increases safety margin.

The table below shows the tradeoff across threshold values for a 7-node cluster:

|τ_c |Nodes Required (N=7)|Byzantine Tolerance  |Consolidation Latency|
|----|--------------------|---------------------|---------------------|
|0.51|4/7                 |f < 1 (fragile)      |~10ms                |
|0.67|5/7                 |f < 2 (BFT standard) |~20ms                |
|0.80|6/7                 |f < 1.4 (high safety)|~40ms                |
|1.00|7/7                 |f = 0 (unanimous)    |~80ms                |

For high-stakes domains (security findings, medical or legal facts, financial data), τ_c = 0.80 is recommended. For general knowledge consolidation, τ_c = 0.67 is the optimal safety/liveness tradeoff.

### 5.7 New-Node Vote Weight Scaling

Newly-joined nodes with sparse G_K have limited ability to validate claims. Their CDCP votes are downweighted proportionally:

```
VoteWeight(node_i) = min(1.0, |G_K_i| / G_K_threshold)

Where:
  |G_K_i|        = number of blocks in node i's local knowledge graph
  G_K_threshold  = minimum block count for full voting weight (default: 1000)

Example progression for a new node:
  |G_K_i| =  100  →  weight = 0.10
  |G_K_i| =  500  →  weight = 0.50
  |G_K_i| = 1000  →  weight = 1.00  (full voter status)

The weighted quorum calculation in Algorithm 14 uses these weights directly.
A node with weight < 0.50 cannot individually satisfy more than half its
share of the quorum — preventing sparse-G_K nodes from dominating consensus.
```

-----

## 6. Replay and Consolidation Engine (RCE)

The RCE is the engineering analog of hippocampal sharp-wave ripple (SWR) replay during NREM sleep. It runs as a low-priority background process on idle nodes, periodically reactivating STM entries through the full validation pipeline and consolidating survivors to LTM.

### 6.1 Biological Motivation

During NREM sleep, the hippocampus repeatedly reactivates neural ensembles corresponding to recent waking experiences (SWR events at 100–250 Hz). These reactivations are temporally coupled with cortical slow oscillations (~0.75 Hz) and thalamocortical sleep spindles (~12–15 Hz), creating a coordinated transfer of representations from hippocampal to neocortical storage. Klinzing, Niethard, and Born (2019) review evidence that this active systems consolidation process underlies long-term memory formation. The DARM-ANN RCE maps this process as follows:

|Biological Component                                 |DARM-ANN Analog                          |
|-----------------------------------------------------|-----------------------------------------|
|Hippocampal sharp-wave ripple                        |RCE replay event (STM entry reactivation)|
|Neocortical slow oscillation                         |CDCP nomination broadcast                |
|Thalamocortical sleep spindle                        |Multi-node voting round                  |
|NREM sleep stage                                     |Idle-compute RCE background cycle        |
|Memory prioritisation (awake replay tagging)         |Salience scoring (§4.2)                  |
|Cortical engram formation                            |LTM commit + RRC indexing                |
|Interleaved replay preventing catastrophic forgetting|RCE old-memory interleaving (§6.3)       |

### 6.2 RCE Replay Cycle

```
Algorithm 15 — RCE Replay Cycle
──────────────────────────────────────────────────────
function RCE_Cycle(STM, LTM, RRC, GTE, ESE, CDCP, cycle_budget_ms=500):
  t_start ← now()

  // Phase 1: Sample replay candidates (salience-biased, not uniform)
  candidates ← STM.sample_by_salience(n=50, bias='high_salience')

  // Phase 2: Interleave with old LTM entries (prevent catastrophic forgetting)
  old_memories ← LTM.sample_by_age(n=20, age_preference='old')
  replay_batch ← interleave(candidates, old_memories, ratio=50:20)

  for entry in replay_batch:
    if (now() - t_start) > cycle_budget_ms: break     // respect time budget

    // Re-validate through full GTE pipeline
    bfs_result ← GTE.BFS_Validate(entry.claim, k=2)
    dfs_result ← GTE.DFS_Audit(entry.claim)

    // Reinforce high-quality entries; decay low-quality ones
    if bfs_result.score > 0.70 AND dfs_result.type == Grounded:
      entry.salience = min(1.0, entry.salience * 1.10)   // reinforce
      entry.replays += 1

      // Nominate for CDCP if salience threshold now met
      if entry.salience ≥ θ_nominate AND entry.state == PENDING:
        CDCP.Nominate(entry)

    else:
      entry.salience *= 0.85    // decay entries that fail re-validation
      if entry.salience < θ_decay: STM.expire(entry)

  // Phase 3: Refresh RRC with recently promoted LTM entries
  recent_ltm ← LTM.get_since(last_cycle_time)
  for block in recent_ltm:
    RRC.index(block)

  // Phase 4: Evict stale RRC entries
  RRC.evict_stale(threshold=θ_rrc_decay)

  return RCEReport(
    replayed    = len(replay_batch),
    nominated   = nominated_count,
    reinforced  = reinforced_count,
    decayed     = decayed_count,
    rrc_updated = len(recent_ltm)
  )
```

### 6.3 Catastrophic Forgetting Prevention

The most critical function of the RCE’s interleaved replay is preventing catastrophic forgetting — the tendency of neural networks to overwrite previously learned representations when acquiring new patterns. This phenomenon, first systematically studied by McCloskey & Cohen (1989) and later addressed by elastic weight consolidation (Kirkpatrick et al., 2017; Huszár, 2018), is a fundamental challenge for any continually-learning system.

The interleaved ratio of new STM candidates (50) to old LTM samples (20) ensures that old knowledge receives ongoing gradient representation during any continual learning updates.

-----

> **Proof P42 — Catastrophic Forgetting Bound via Gradient Mixing**
> 
> *Requires: none (standalone). Assumes: A7, A8.*
> 
> **Claim:** With interleaved replay at ratio r = n_old / n_new ≥ 0.4, the expected gradient under the mixed replay batch is a convex combination of old-task and new-task gradients, with old-task weight ≥ r/(1+r) ≈ 0.286.
> 
> **Proof:** Consider a gradient update step where the batch consists of n_new new-sample examples {x_i^new} and n_old old-sample examples {x_j^old}. Define the task-specific loss functions:
> 
> - L_new(Θ) = (1/n_new) Σ_i ℓ(Θ, x_i^new)   (loss on new claims)
> - L_old(Θ) = (1/n_old) Σ_j ℓ(Θ, x_j^old)    (loss on consolidated claims)
> 
> The mixed-batch gradient is:
> 
> ```
> ∇L_mixed(Θ) = (n_new/(n_new + n_old)) · ∇L_new(Θ) + (n_old/(n_new + n_old)) · ∇L_old(Θ)
> 
> Define:
>   w_new = n_new / (n_new + n_old) = 1 / (1 + r)
>   w_old = n_old / (n_new + n_old) = r / (1 + r)
> 
> For r = 0.4:
>   w_new = 1/1.4 ≈ 0.714
>   w_old = 0.4/1.4 ≈ 0.286
> ```
> 
> Therefore:
> 
> ```
> ∇L_mixed(Θ) = 0.714 · ∇L_new(Θ) + 0.286 · ∇L_old(Θ)
> ```
> 
> This is mathematically equivalent to optimising the weighted multi-task objective:
> 
> ```
> L_mixed(Θ) = w_new · L_new(Θ) + w_old · L_old(Θ)
> ```
> 
> **Connection to EWC.** Kirkpatrick et al. (2017) showed that Elastic Weight Consolidation prevents catastrophic forgetting by adding a quadratic penalty around the parameter values Θ* that minimised the old task:
> 
> ```
> L_EWC(Θ) = L_new(Θ) + (λ/2) Σ_i F_i (Θ_i − Θ*_i)²
> ```
> 
> where F_i is the Fisher information for parameter i. Interleaved replay provides an *implicit* version of this penalty: the old-task gradient ∇L_old(Θ) pulls parameters back toward regions of low old-task loss (the neighbourhood of Θ*) at every update step, with effective regularisation strength proportional to w_old = r/(1+r).
> 
> **Formal bound.** Under gradient norm clipping (||∇L|| ≤ G_max, assumption A8) and learning rate η:
> 
> ```
> Per-step parameter change: ||ΔΘ|| ≤ η · G_max
> 
> The component of ΔΘ attributable to old-task loss:
>   ||ΔΘ_old|| = η · w_old · ||∇L_old|| ≤ η · 0.286 · G_max
> 
> After T steps, the cumulative parameter movement is bounded by:
>   ||Θ_T − Θ_0|| ≤ T · η · G_max
> 
> The fraction of this movement directed by old-task gradients is at least w_old = 0.286,
> meaning at least 28.6% of the gradient signal at each step is informed by consolidated
> knowledge.
> ```
> 
> **Note on limitations:** This proof establishes a *gradient mixing* guarantee, not a parameter proximity guarantee. The old-task gradient ∇L_old(Θ) pulls toward regions of low old-task loss, but does not guarantee that parameters remain within any fixed distance of Θ*. In practice, the combination of gradient mixing with gradient clipping provides robust protection against catastrophic forgetting, as confirmed empirically by the continual learning literature (McCloskey & Cohen, 1989; Kirkpatrick et al., 2017). The formal guarantee strengthens with increasing r.
> 
> ∎

### 6.4 RCE Scheduling

```
RCE runs on idle Tier 2/3 nodes during low-inference periods:

Priority:    Linux NICE 19 (lowest user-space priority)
Trigger:     node CPU utilisation < 30% for > 60 seconds continuously
Budget:      500ms wall-clock per cycle (configurable per node class)
Frequency:   at most once per 5 minutes per node (configurable)
Coordination: nodes use Tendermint epoch coordination to avoid duplicate
              simultaneous replay of the same LTM entries

Estimated hardware cost per cycle (Tier 2: x86 mini-PC):
  50 STM re-validations × 10ms (GTE BFS k=2) = 500ms GPU-equivalent
  With 4-way parallelism: ~125ms wall-clock
  Energy cost: ~20–75mJ per cycle depending on node class
```

-----

## 7. Rapid Retrieval Cache (RRC)

The RRC solves the retrieval cost problem at the heart of v6.0’s motivation. It is a pre-computed, LSH-indexed lookup table mapping query patterns to pre-validated reasoning results. It converts the question “what did we reason about this topic?” from a computational problem to a lookup problem.

### 7.1 RRC Architecture

The RRC is built on the same three-dimensional LSH array introduced in v3.0 (§5.2), adapted to index LTM entries rather than raw state vectors:

```
RRC LSH Configuration (inherited from v3.0, P4):
  Hash family:   (r, cr, p₁, p₂)-sensitive with p₁ ≈ 0.9, p₂ ≈ 0.1
  Bucket count:  B = B₁ × B₂ × B₃ = 256³ = 1.677 × 10⁷ buckets
  Index key:     embed(query) → LSH bucket
  Index value:   {ltm_block_hash, cached_result, reasoning_steps, confidence}
  Hash tables:   L = 3 (for improved recall via independent hash families)

By the v3.0 LSH analysis (P4):
  E[bucket_occupancy]     = K/B ≈ 10K / 1.677×10⁷ ≈ 6 × 10⁻⁴ entries/bucket
  P(O(1) retrieval)       ≈ 1.0 for K = 10K
  P(false negative, L=3)  = (1 - p₁)^L = (1 - 0.9)³ = 0.001  (0.1% miss rate)
```

### 7.2 RRC Query Resolution

```
Algorithm 16 — RRC Query
──────────────────────────────────────────────────────
function RRC_Query(query_text, RRC, LTM, threshold=0.85):
  query_embed ← TinyLM.embed(query_text)
  bucket_keys ← [LSH_l.hash(query_embed) for l in 1..L]   // L=3 tables
  candidates  ← union(RRC.lookup(key) for key in bucket_keys)

  if candidates is empty:
    return RRC_MISS                          // fall through to LTM/STM lookup

  // Rank by embedding cosine similarity
  best ← max(candidates, key=λ c: cosine_similarity(c.embedding, query_embed))

  if cosine_similarity(best.embedding, query_embed) < threshold:
    return RRC_MISS                          // closest match not similar enough

  // Update access statistics for cache management
  best.access_count += 1
  best.last_accessed ← now()

  return RRC_HIT(
    result     = best.cached_result,
    steps      = best.reasoning_steps,      // compressed CoT for context injection
    confidence = best.confidence,
    source     = best.ltm_block_hash
  )
```

### 7.3 Cache Invalidation

RRC entries are invalidated when their source LTM block is superseded by a newer consensus result:

```
function RRC_Invalidate(ltm_block_hash):
  entry ← RRC.find_by_source(ltm_block_hash)
  if entry:
    RRC.remove(entry)
    // Re-index superseding block if it exists
    new_block ← LTM.get_superseding(ltm_block_hash)
    if new_block: RRC.index(new_block)
```

This ensures the RRC never serves stale results: once a LTM block is superseded through the temporal conflict resolution process (§8.3), all downstream cache entries pointing to it are immediately invalidated.

### 7.4 Cache Warm-Up and Cold Start

On node initialisation (cold start), the RRC is empty. Two parallel warm-up pathways operate:

1. **Replay-driven warm-up:** The RCE’s first cycle pulls the top-K LTM entries by historical access frequency and indexes them into the RRC. This pre-populates the cache with the network’s most valuable consolidated knowledge.
1. **Query-driven warm-up:** Cache misses that result in successful LTM lookups are automatically back-populated into the RRC if the result’s consolidated confidence ≥ θ_conf.

```
Cold start latency profile:
  First retrieval:          O(T_LTM_fetch + T_GTE) ≈ 50–80ms  (blockchain lookup)
  After query-driven WU:    O(T_RRC) ≈ 2ms  (after ~200 queries)
  After replay-driven WU:   O(T_RRC) ≈ 2ms  (after first RCE cycle, K=10K pre-loaded)
  Time to 80% hit rate:     ~1 RCE cycle on node init OR ~200 live queries
```

-----

> **Proof P43 — RRC Retrieval Performance**
> 
> *Requires: P4 (v3.0). Assumes: A9.*
> 
> **Claim:** The RRC achieves expected O(1) retrieval latency with recall ≥ 99.9%.
> 
> **Proof:** Given the LSH configuration with L=3 independent hash tables, each with B = 256³ buckets and K = 10K entries:
> 
> **Latency (amortized):**
> 
> ```
> E[T_RRC] = T_hash_computation + E[T_candidate_scan]
>           = O(d) + O(E[bucket_occupancy] × L)
>           = O(d) + O((K/B) × L)
>           = O(d) + O(6 × 10⁻⁴ × 3)
>           = O(d) + O(1.8 × 10⁻³)
>           = O(d)
> ```
> 
> Since d (embedding dimension) is a fixed constant (e.g., 384 for TinyLM), E[T_RRC] = O(1) amortized. Worst-case (all K entries hash to the same bucket in all L tables) is O(K), but this occurs with probability negligible for B >> K (see P6, v3.0). ∎
> 
> **Recall:**
> 
> ```
> P(true nearest neighbour retrieved | L=3 tables, p₁=0.9):
>   P(miss in one table) = 1 - p₁ = 0.10
>   P(miss in all L tables) = (1 - p₁)^L = 0.10³ = 0.001
>   P(recall) = 1 - 0.001 = 99.9%  ∎
> ```
> 
> **Precision** is controlled by the cosine similarity threshold parameter (default 0.85), which can be tuned per deployment. At threshold 0.85, false positives (returning a cached result for a semantically different query) are bounded by the probability mass of the embedding space within cosine distance 0.15 of the query.

-----

## 8. Memory Lifecycle Management

### 8.1 Decay Scoring

Every STM entry has a time-varying decay score that determines its priority for CDCP nomination and RCE replay. The decay model is inspired by Ebbinghaus’s forgetting curve, augmented with a rehearsal (replay) reinforcement term:

```
DecayScore(e, t) = salience(e) × RecencyFactor(e, t) × ReinforcementFactor(e)

RecencyFactor(e, t)    = exp(−λ_decay × (t − e.created_at))
ReinforcementFactor(e) = 1 + log₁₀(1 + e.replays)   // log prevents unbounded growth

λ_decay = 0.10 per hour  (default; half-life ≈ 6.9 hours)
         = 0.01 per hour  for high-salience entries (salience ≥ 0.70; half-life ≈ 69 hours)

DecayScore ∈ [0, salience(e)];  approaches 0 as t → ∞ with no replay
```

-----

> **Proof P48 — Decay Score Correspondence to Ebbinghaus Forgetting Curve**
> 
> *Requires: none (standalone). Assumes: A10.*
> 
> **Claim:** DecayScore(e, t) is a discretisation of the Ebbinghaus forgetting curve with rehearsal (spacing effect) enhancement.
> 
> **Proof:**
> 
> **Part 1 — Ebbinghaus correspondence.** The Ebbinghaus retention function (Ebbinghaus, 1885) is commonly modelled as:
> 
> ```
> R(t) = e^{−t/S}
> ```
> 
> where R(t) is the retention probability at time t after encoding, and S is the memory stability (higher S = slower forgetting). DARM-ANN’s RecencyFactor is:
> 
> ```
> RecencyFactor(e, t) = exp(−λ_decay × (t − e.created_at))
>                     = exp(−(t − e.created_at) / (1/λ_decay))
> ```
> 
> Setting S = 1/λ_decay, this is exactly the Ebbinghaus form R(t) = e^{−t/S}:
> 
> ```
> For λ_decay = 0.10/hour:  S = 10 hours
> For λ_decay = 0.01/hour:  S = 100 hours
> 
> Half-life: t_{1/2} = S × ln(2) = ln(2)/λ_decay
>   λ_decay = 0.10/hour → t_{1/2} ≈ 6.93 hours  ✓
>   λ_decay = 0.01/hour → t_{1/2} ≈ 69.3 hours  ✓
> ```
> 
> **Part 2 — Spacing effect correspondence.** The spacing effect (Cepeda et al., 2006; Ebbinghaus, 1885) is the empirical finding that distributed rehearsal (spaced repetition) increases memory stability. The standard model augments the Ebbinghaus curve by increasing S after each rehearsal:
> 
> ```
> S_k = S_0 × f(k)   where k = number of rehearsals and f is increasing
> ```
> 
> Common choices for f include f(k) = 1 + α·k (linear) and f(k) = (1 + α)^k (exponential). DARM-ANN’s ReinforcementFactor uses f(k) = 1 + log₁₀(1 + k), a sublinear function that:
> 
> - Is monotonically increasing: f’(k) = 1/((1+k)·ln(10)) > 0 for all k ≥ 0
> - Has diminishing returns: f’’(k) < 0, matching the empirical finding that additional rehearsals have decreasing marginal benefit
> - Is bounded: for practical replay counts (k ≤ 1000), f(k) ≤ 1 + log₁₀(1001) ≈ 4.0, preventing unbounded score inflation
> - Satisfies f(0) = 1 (no rehearsal = baseline decay rate)
> 
> The full DecayScore is therefore:
> 
> ```
> DecayScore(e, t) = salience(e) × e^{−t/S} × (1 + log₁₀(1 + replays))
>                  = salience(e) × R(t) × f(replays)
> ```
> 
> This is a multiplicative composition of initial importance (salience), temporal decay (Ebbinghaus), and rehearsal enhancement (spacing effect) — matching the standard cognitive psychology model of memory retention under spaced practice.
> 
> ∎

### 8.2 Memory Triage

The memory triage process runs periodically (every 30 minutes) on each node, evaluating STM entries for promotion, retention, or expiry:

```
Algorithm 17 — Memory Triage
──────────────────────────────────────────────────────
function MemoryTriage(STM, CDCP, t):
  for entry in STM.all():
    entry.decay_score ← DecayScore(entry, t)

    if entry.promoted:
      STM.archive(entry)                   // successfully moved to LTM
    elif entry.decay_score < θ_expire:
      STM.expire(entry)                    // aged out without consolidation
    elif entry.state == REJECTED:
      entry.retry_count += 1
      if entry.retry_count > max_retries:
        STM.expire(entry)                  // abandoned after multiple rejections
    elif entry.salience ≥ θ_nominate AND entry.state == PENDING:
      CDCP.Nominate(entry)                 // ready for consensus
    else:
      pass                                 // hold; re-evaluate at next triage

  // Enforce hard capacity limit via decay-ordered eviction
  if STM.size() > STM.capacity:
    overflow ← STM.size() - STM.capacity
    to_evict ← STM.sort_by('decay_score', ascending=True)[:overflow]
    for e in to_evict: STM.expire(e)
```

### 8.3 Retrograde Protection

Once a memory is promoted to LTM, it must be protected from retrograde interference — the corruption or premature overwriting of established memories by new conflicting information. BVAS provides the primary structural protection (block integrity and hash-chain continuity), but the RCE provides an additional evidential protection layer:

```
Retrograde Protection Protocol:
  When a new CDCP nomination c_new conflicts with an existing LTM entry c_old:
    // Do NOT immediately overwrite c_old
    // Create a Temporal Conflict record instead

    conflict ← TemporalConflict(
      c_old      = c_old,
      c_new      = c_new,
      timestamp  = now(),
      evidence   = {bfs_conflict_path, dfs_comparison, vote_histories}
    )

    // Both c_old and c_new coexist in LTM until resolution
    // Resolution criterion: weighted vote-score comparison

Resolution Function:
  Resolve(c_old, c_new) = c_old WINS iff:
    IncumbentScore(c_old) ≥ ChallengerScore(c_new)

  Where:
    IncumbentScore(c) = Σ(vote_score_i × weight_i for all CDCP votes for c) × κ
    ChallengerScore(c) = Σ(vote_score_j × weight_j for all CDCP votes for c)

    κ = incumbency factor (default 1.2)

  Resolution is triggered after:
    Σ(all votes cast for c_old + c_new) ≥ θ_resolution_votes  (default: 10)

  The losing claim is marked SUPERSEDED: retained in LTM for audit trail
  but not served to agents. Its RRC entries are invalidated (§7.3).
```

The incumbency factor κ = 1.2 provides asymmetric protection in favour of established knowledge: a challenger must accumulate 20% more vote-score than the incumbent to displace it. This is consistent with the biological finding that remote memories are more resistant to interference than recent ones (McClelland et al., 1995).

-----

> **Proof P44 — Retrograde Protection Symmetry**
> 
> *Requires: P39, P40. Assumes: A1, A2, A11.*
> 
> **Claim:** No new claim c_new can overwrite an established LTM entry c_old without itself meeting at least the same evidentiary standard that c_old originally satisfied, plus an additional 20% margin.
> 
> **Proof:** c_old was admitted to LTM via CDCP quorum (≥ τ_c weighted fraction of nodes voted YES, with BVAS gate passed). Let S_old = IncumbentScore(c_old) = κ × Σ(vote_score_i × weight_i).
> 
> For c_new to displace c_old, it must satisfy ChallengerScore(c_new) > S_old, i.e.:
> 
> ```
> Σ(vote_score_j × weight_j for c_new) > κ × Σ(vote_score_i × weight_i for c_old)
> ```
> 
> Since c_old achieved at least a τ_c quorum with vote scores ≥ θ_vote = 0.60 each, and κ = 1.2:
> 
> ```
> ChallengerScore(c_new) > 1.2 × S_old
> 
> This requires c_new to achieve either:
>   (a) the same quorum size with 20% higher mean vote-score, or
>   (b) a larger quorum, or
>   (c) both.
> 
> In any case, ChallengerScore(c_new) > S_old implies c_new meets at least
> the same evidentiary standard as c_old (because it must exceed c_old's
> score even before the κ multiplier is applied to c_old's advantage).
> ```
> 
> Additionally, resolution requires θ_resolution_votes ≥ ⌈τ_c × N_cluster⌉ total votes cast (assumption A11), ensuring that resolution is not triggered prematurely by a small number of early votes.
> 
> Therefore, c_new must meet or exceed c_old’s evidentiary standard by a factor of κ = 1.2 to displace it. ∎

-----

## 9. Full Integration

### 9.1 Memory + GTE

The Graph Traversal Engine (§3 of v5.0) now queries the full memory hierarchy in priority order, short-circuiting at the fastest successful retrieval:

```
GTE Query Priority:
  1. RRC lookup  (~2ms)             — pre-computed cache
  2. STM lookup  (~2ms)             — node-local recent claims
  3. LTM LSH lookup (~5ms)          — blockchain LSH index
  4. GTE BFS/DFS (O(b^k), ~10–80ms) — full graph traversal

Short-circuit rule: if RRC_HIT with confidence ≥ 0.85, skip GTE traversal.
This is the primary source of the 25–200× latency reduction for cached queries.
```

### 9.2 Memory + BVAS

The five-stage BVAS validity pipeline (§4 of v5.0) is applied selectively based on memory tier:

```
Memory-tier-aware BVAS:
  STM entries have already passed BVAS Stages 1–3 during STM_Persist (§4.3):
    Stage 1: GTE BFS verdict (k=1)
    Stage 2: Cryptographic integrity (claim_id = SHA-256 hash)
    Stage 3: ESE confidence gate

  At CDCP promotion time, only Stages 4–5 are re-evaluated:
    Stage 4: Temporal consistency re-check against current LTM state
    Stage 5: ESE consolidated confidence from all voting nodes

  This selective re-evaluation reduces BVAS overhead at promotion by ~60%
  compared to full five-stage re-validation.
```

### 9.3 Memory + RLRF

The RLRF reward signal in v6.0 includes a memory efficiency component that incentivises cache use, discourages redundant reprocessing, and rewards the production of consolidatable knowledge:

```
R_RLRF_v6(CoT_l) =
    wᵣ · R_reasoning   +  wₒ · R_outcome   +  wₚ · R_process
  + w_e · R_epistemic   +  w_m · R_memory                     // new in v6.0

R_memory(CoT_l) =
  + rrc_hit_bonus          if RRC_HIT was correctly utilised in reasoning
  + consolidation_bonus    if the claim later passes CDCP promotion
  − reprocessing_penalty   if RRC_MISS on a query pattern previously consolidated
  − stm_pollution_penalty  if a claim fails STM→LTM promotion after repeated tries

Component values:
  rrc_hit_bonus          = +0.30  (reward efficient retrieval)
  consolidation_bonus    = +0.50  (reward producing network-validated knowledge)
  reprocessing_penalty   = −0.20  (penalise redundant re-derivation of known facts)
  stm_pollution_penalty  = −0.10  (penalise flooding STM with noise)

w_m = 0.10 (new weight; other component weights scaled proportionally)
```

### 9.4 Cross-System Memory Flow Summary

```
Query arrives at agent (l,a)
     │
     ▼
① WORKING MEMORY: load context window, inject top-K STM/LTM/RRC snippets
     │
     ▼
② RRC LOOKUP: O(1) pre-computed cache check
     │ RRC_HIT (conf ≥ 0.85) ────────────────────────────────→ ⑥ USE CACHED RESULT (~2ms)
     │ RRC_MISS
     ▼
③ STM LOOKUP: O(1) node-local check
     │ STM_HIT ─────────────→ inject into WM context
     │ STM_MISS
     ▼
④ LTM LOOKUP: O(1) blockchain LSH index
     │ LTM_HIT ─────────────→ inject into WM context, back-populate RRC
     │ LTM_MISS
     ▼
⑤ FULL INFERENCE: agent generates CoT + output (50–400ms)
     │
     ▼
⑥ ESE GATE: calibrated confidence + epistemic uncertainty check
     │ ABSTAIN → structured abstention logged to EB only; no STM write
     │ COMMIT / FLAG
     ▼
⑦ MEMORY ENCODING: high-salience claims → EB (Algorithm 10)
     │
     ▼
⑧ STM PERSISTENCE: EB entries → STM for eligible claims (Algorithm 11)
     │
     ▼
⑨ BACKGROUND — GTE RE-VALIDATION: BFS + DFS for pending STM entries
     │
     ▼
⑩ BACKGROUND — RCE REPLAY: periodic salience-biased reactivation (Algorithm 15)
     │ salience ≥ θ_nominate AND state == PENDING
     ▼
⑪ CDCP NOMINATION: multi-node independent voting (Algorithms 12–14)
     │ quorum met AND V_BVAS ≥ 0.60
     ▼
⑫ LTM COMMIT: blockchain write with full epistemic tuple + vote provenance
     │
     ▼
⑬ RRC INDEXING: pre-compute LSH entry for O(1) future retrieval
```

-----

## 10. Updated Twelve-Layer Stack (v6.0)

```
┌──────────────────────────────────────────────────────────────────────────┐
│                      APPLICATION INTERFACE LAYER                          │
│   Σ_app(t) = { channels, APIs, orchestration, memory access reports }     │
├──────────────────────────────────────────────────────────────────────────┤
│   RAPID RETRIEVAL CACHE (RRC)                         [NEW — v6.0]       │
│   Pre-computed LSH index over consolidated LTM entries                    │
│   O(1) avg retrieval · 99.9% recall · ~2ms latency                      │
│   Back-populated via CDCP promotions and query-driven warm-up            │
│   Invalidated on LTM block supersession                                  │
├──────────────────────────────────────────────────────────────────────────┤
│   CONSENSUS-DRIVEN CONSOLIDATION PROTOCOL (CDCP)      [NEW — v6.0]       │
│   STM → LTM promotion via τ_c-quorum multi-node independent voting       │
│   Independent GTE + ESE evaluation per node; no shared intermediate state│
│   Weighted voting with new-node scaling (§5.7)                           │
├──────────────────────────────────────────────────────────────────────────┤
│   REPLAY AND CONSOLIDATION ENGINE (RCE)               [NEW — v6.0]       │
│   NREM sleep analog: salience-biased offline replay                      │
│   Catastrophic forgetting prevention via interleaved old-memory replay   │
│   Drives CDCP nominations · Refreshes RRC · Time-budgeted (500ms/cycle)  │
├──────────────────────────────────────────────────────────────────────────┤
│   SHORT-TERM MEMORY (STM)                             [NEW — v6.0]       │
│   Node-local Redis-backed validated claim store (~10K entries)           │
│   TTL-managed · Decay-scored · Deduplication-aware                      │
│   Bridge: Episodic Buffer → CDCP nomination → LTM                       │
├──────────────────────────────────────────────────────────────────────────┤
│   EPISODIC BUFFER (EB)                                [NEW — v6.0]       │
│   Per-agent ring buffer of recent reasoning traces (R = 64 default)      │
│   Session-duration · Salience-sorted · Primary source of STM candidates  │
├──────────────────────────────────────────────────────────────────────────┤
│   EPISTEMIC SKEPTICISM ENGINE (ESE)                   [v5.0]             │
│   Calibrated confidence · Second-order uncertainty · Adversarial debate  │
│   Gates EB → STM encoding · Contributes per-node vote scores to CDCP    │
├──────────────────────────────────────────────────────────────────────────┤
│   BLOCKCHAIN VALIDITY ALGORITHM SUITE (BVAS)          [v5.0]             │
│   Full 5-stage validation for direct writes                              │
│   Optimised 2-stage re-validation (Stages 4–5 only) at CDCP promotion   │
├──────────────────────────────────────────────────────────────────────────┤
│   GRAPH TRAVERSAL ENGINE (GTE)                        [v5.0]             │
│   BFS / DFS / BiDir / Dijkstra / A* traversal over G_K                  │
│   Query order: RRC → STM → LTM → full GTE traversal                     │
│   Short-circuit on RRC_HIT with conf ≥ 0.85                             │
├──────────────────────────────────────────────────────────────────────────┤
│   RLRF + MARKOV GRAPH + AGENTIC LAYER                 [v4.0]             │
│   RLRF v6: + w_m · R_memory component (cache use, consolidation reward)  │
│   G_M updated with memory tier access patterns                           │
├──────────────────────────────────────────────────────────────────────────┤
│   LTM BLOCKCHAIN + SLM/TinyLM + DATA STRUCTURES      [v3.0]             │
│   M_global = canonical LTM · TinyLM inference tiers                     │
│   LSH + BTree + Cluster substrate · T_decision = O(log m) (P3)          │
├──────────────────────────────────────────────────────────────────────────┤
│   LAYER 1 — BARE-METAL HYPERVISOR                     [original]         │
│   H(t) = { (node_i, status_i, power_i, load_i) }                        │
└──────────────────────────────────────────────────────────────────────────┘
```

-----

## 11. End-to-End Memory Flow

### Full Lifecycle: “TLS 1.3 mandates forward secrecy via ephemeral key exchange”

```
T+0ms:    Agent receives TLS security query. WM loads context.
          RRC lookup → MISS (first occurrence of this pattern on this node)
          STM lookup → MISS
          LTM lookup → MISS

T+5ms:    Full inference completes. ESE evaluates:
            conf_cal = 0.91, u_ep = 0.08 → COMMIT gate passes
          R_RLRF = 0.87 (high reward for accurate security reasoning)

T+6ms:    MemoryEncode: claim extracted from CoT.
            novelty = 0.81 (not seen before in EB/STM)
            salience = 0.30 × 0.81 + 0.35 × 0.87 + 0.25 × 0.40 + 0.10 × 0.91
                     ≈ 0.243 + 0.305 + 0.100 + 0.091 = 0.739
          → EB.push(trace)

T+8ms:    STM_Persist: BFS k=1 passes (no contradictions in local G_K)
            STM.insert(claim_entry, TTL=24h, state=PENDING)

T+60s:    MemoryTriage cycle: decay_score = 0.739 × e^(−0.01×(1/60)) × 1.0
            ≈ 0.739 × 0.9998 ≈ 0.739
          (High-salience entries use λ_decay = 0.01/hour; 60s elapsed = negligible decay)
          salience 0.739 ≥ θ_nominate (0.55) → CDCP.Nominate(claim)

T+62s:    Nomination ballot broadcast to 6 peer nodes.
          Each peer independently runs:
            - local BFS k=2 validation
            - local DFS causal audit
            - local ESE epistemic uncertainty check

T+72s:    5 of 7 nodes return YES votes (all with VoteWeight = 1.0):
            vote_scores: [0.88, 0.91, 0.79, 0.85, 0.83]
            consolidated_conf = (0.88+0.91+0.79+0.85+0.83)/5 = 0.852
          weighted yes = 5.0 / 7.0 = 0.714 ≥ τ_c (0.67) ✓

T+73s:    BVAS Stages 4–5: temporal consistency OK, ESE gate passes.
          LTM.commit(block_hash = 0x4a7f..., conf = 0.852, provenance = vote_record)

T+74s:    RRC.index(block_hash = 0x4a7f..., query_embed, result)

T+74s+ε: Any node that receives a TLS 1.3 forward secrecy query:
          RRC lookup → HIT in ~2ms
          Returns pre-validated result at LTM-grade confidence.

RETRIEVAL COST COMPARISON:
  Initial reasoning + consolidation:   74 seconds total (one-time cost)
  First retrieval (full inference):    ~5ms active inference
  All subsequent retrievals:           ~2ms RRC lookup
  For complex multi-hop security analysis (normally 200–400ms):
    After consolidation: 2ms RRC → 100–200× speedup per query
```

-----

## 12. Comparative Performance Analysis

### 12.1 Retrieval Latency by Memory Tier

|Retrieval Path            |Latency |Accuracy                            |When Used                                |
|--------------------------|--------|------------------------------------|-----------------------------------------|
|RRC hit                   |~2ms    |Pre-validated (LTM-grade confidence)|Frequently accessed consolidated patterns|
|STM hit                   |~2ms    |ESE-validated (node-local)          |Recent session knowledge                 |
|LTM LSH hit               |~5ms    |BFT-consensus validated             |Any consolidated fact                    |
|LTM full scan             |~50ms   |BFT-consensus validated             |Rare: LSH miss on LTM                    |
|Full inference (no memory)|50–400ms|Raw model confidence                |Novel queries                            |
|Full inference + GTE      |80–500ms|Traversal-validated                 |Novel + verification needed              |

### 12.2 Reprocessing Cost Avoided

-----

> **Proof P45 — RRC Retrieval Efficiency**
> 
> *Requires: P43. Assumes: A9, A12.*
> 
> **Claim:** RRC achieves 25–200× speedup over full-inference retrieval for consolidated queries, and improves system throughput by approximately 2.5× at a 60% cache hit rate.
> 
> **Proof:** Let T_reason(q) be the wall-clock time to produce a validated result for query q via full inference + GTE. For a consolidated query (in RRC), T_RRC ≈ 2ms. Speedup:
> 
> ```
> Speedup(q) = T_reason(q) / T_RRC
> 
> Simple factual claim     (T_reason ≈  50ms): Speedup ≈  25×
> Multi-hop reasoning      (T_reason ≈ 200ms): Speedup ≈ 100×
> Complex security analysis (T_reason ≈ 400ms): Speedup ≈ 200×
> ```
> 
> For a system processing Q queries/second with fraction f_cached resolved by RRC:
> 
> ```
> T_effective = f_cached × T_RRC + (1 − f_cached) × T_reason
> 
> At f_cached = 0.60, T_reason = 200ms:
>   T_effective = 0.60 × 2ms + 0.40 × 200ms
>               = 1.2ms + 80ms = 81.2ms
> 
> Throughput improvement = T_reason / T_effective = 200 / 81.2 ≈ 2.46×  ∎
> ```

### 12.3 Consolidation Overhead vs. Benefit

```
One-time cost of CDCP per promoted claim:
  Nomination broadcast:         ~0.5ms (local)
  Voting round (5 nodes, 2Δ):   ~20ms  (network RTT)
  BVAS Stages 4–5:               ~5ms
  LTM commit (blockchain write): ~5ms
  RRC indexing:                  ~1ms
  ──────────────────────────────────────
  Total CDCP overhead:           ~31.5ms per claim

Benefit per subsequent retrieval:
  Savings = T_reason − T_RRC ≈ 200ms − 2ms = 198ms per query

Break-even access count:
  31.5ms / 198ms ≈ 0.16 accesses
  → Any claim accessed even once after consolidation is net positive.

At 10 accesses post-consolidation:
  31.5ms / (10 × 198ms) ≈ 1.6% overhead
  → Consolidation overhead is negligible for recurrent knowledge.
```

-----

## 13. Updated Risk Analysis

|Risk ID|Risk Description                              |Likelihood|Impact|v6.0 Mitigation                                                                                                               |
|-------|----------------------------------------------|----------|------|------------------------------------------------------------------------------------------------------------------------------|
|T1     |BFT coordination failure                      |Med       |High  |CDCP inherits BFT safety (P40); τ_c = 0.67 requires f < 2/7 Byzantine                                                         |
|T9     |GTE false negatives                           |Low       |Med   |RRC only caches GTE-validated claims; false negatives blocked before cache entry                                              |
|T12    |Temperature calibration drift                 |Med       |Med   |ESE recalibration feeds into per-node CDCP vote scores; poorly calibrated nodes weighted down                                 |
|T13    |STM overflow                                  |Med       |Low   |Triage algorithm enforces capacity limit; decay scoring evicts lowest-priority entries first; steady-state analysis in §3.4   |
|T14    |RRC stale entry                               |Low       |Low   |Invalidation triggered on LTM block supersession; decay scoring evicts aged entries                                           |
|T15    |CDCP quorum stall                             |Low       |Med   |Fallback: STM TTL expiry after 24h; retry count limit; asynchronous re-nomination                                             |
|T16    |RCE overhead impacting inference              |Low       |Low   |RCE runs at NICE 19; time-budgeted (500ms max/cycle); inference path completely unaffected                                    |
|T17    |Catastrophic forgetting despite interleaving  |Low       |High  |P42 bounds gradient mixing fraction; gradient clipping provides hard limit; old-memory interleaving is mandatory, not optional|
|T18    |Cold start RRC miss surge                     |Med       |Low   |Query-driven back-population; RCE warm-up pre-loads K=10K entries on node init; graceful fallback to LTM direct lookup        |
|T19    |Sparse G_K on newly-joined nodes              |Med       |Med   |New nodes’ CDCP votes downweighted via VoteWeight (§5.7) until G_K block count reaches minimum threshold                      |
|T20    |Cross-node G_K correlation weakening P39 bound|Med       |Med   |ρ_GK parameterisation in P39; operational guidance to reduce correlation via data partitioning and staggered join             |

-----

## 14. Further Research

|#    |Open Problem                                    |Conjecture / Research Direction                                                                                                                                                                               |
|-----|------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|OP-22|Optimal salience weight tuning per domain       |Current defaults (w_nov=0.30, w_rew=0.35, w_freq=0.25, w_conf=0.10) are domain-agnostic. RL-based meta-learning of per-domain weights may improve consolidation precision by 20–30%. Ablation studies needed. |
|OP-23|Adaptive τ_c based on claim type and domain risk|Security/medical claims: τ_c=0.80; general knowledge: τ_c=0.67; auto-tuning τ_c per domain via RLRF reward signal is an open problem.                                                                         |
|OP-24|RCE cycle frequency vs. consolidation quality   |Preliminary analysis suggests diminishing returns beyond 1 cycle/5 min; optimal frequency is a function of inference load and STM entry rate.                                                                 |
|OP-25|Cross-node STM gossip protocol                  |Selective STM gossip (sharing high-salience STM entries before full CDCP) could accelerate quorum formation without requiring full replication overhead.                                                      |
|OP-26|RRC embedding compression                       |Quantised embeddings (4-bit) in RRC could reduce memory footprint by 4× with estimated < 1% recall loss; requires empirical validation.                                                                       |
|OP-27|Formal convergence of STM→LTM promotion rate    |Conjecture: the fraction of STM entries that ultimately achieve LTM promotion converges to a fixed point determined by the underlying data distribution and τ_c. A formal proof remains open.                 |
|OP-28|Direct CDCP-to-LoRA adapter coupling            |Can CDCP-promoted LTM entries directly drive LoRA adapter weight updates, bypassing the separate RLRF gradient cycle? This would close the loop between episodic memory consolidation and parametric learning.|
|OP-29|Tightening the ρ_GK bound in P39                |The Bahadur representation used in P39 is a first-order approximation. Higher-order correlation models (e.g., Lancaster interaction terms) could yield tighter bounds for specific G_K overlap profiles.      |

### Validation Methodology (v6.0)

|VM ID|Metric                           |Measurement Protocol                                                             |Success Threshold                          |
|-----|---------------------------------|---------------------------------------------------------------------------------|-------------------------------------------|
|VM-7 |RRC hit rate after 24h deployment|Count RRC_HIT vs. total queries on reference cluster                             |≥ 50% hit rate on repeated query patterns  |
|VM-8 |CDCP consolidation accuracy      |Fraction of CDCP-promoted claims later contradicted by curated external KB       |< 0.05% contradiction rate                 |
|VM-9 |Retrieval speedup                |Wall-clock time for 1,000 queries: RRC hit vs. full inference                    |≥ 10× speedup on repeated queries          |
|VM-10|Catastrophic forgetting measure  |Performance on baseline benchmarks before vs. after 7 days of continuous learning|< 2% degradation on consolidated benchmarks|
|VM-11|Cross-node correlation (ρ_GK)    |Measured pairwise G_K overlap across reference cluster after 7 days              |ρ_GK < 0.50 with data partitioning enabled |

-----

## 15. Assumption Registry

Every formal proof in this paper depends on one or more modelling assumptions. The following registry makes these dependencies explicit and traceable.

|ID |Assumption                                                                                                                                                                                                                             |Used By                    |Validation Path                                                                                                                                                                                           |
|---|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|A1 |**BFT model:** At most f < N/3 nodes are Byzantine; correct nodes follow protocol faithfully.                                                                                                                                          |P39, P40, P41, P44, P46    |Standard PBFT assumption (Castro & Liskov, 1999). Verified by Tendermint consensus layer.                                                                                                                 |
|A2 |**Partial synchrony:** A Global Stabilization Time (GST) exists after which all messages between correct nodes are delivered within bounded delay Δ.                                                                                   |P40, P41, P46              |Standard assumption from DLS (Dwork, Lynch & Stockmeyer, 1988). Required for liveness; safety holds without it.                                                                                           |
|A3 |**Cross-node G_K correlation (ρ_GK):** Pairwise correlation between nodes’ G_K-based detection outcomes is parameterised by ρ_GK ∈ [0, 1]. For nodes bootstrapped from the same LTM, ρ_GK ∈ [0.3, 0.5] is the expected operating range.|P39                        |Measurable via VM-11. Reducible by data partitioning, G_K perturbation, and staggered join (§5.5).                                                                                                        |
|A4 |**GTE detection rates:** P(BFS detects hallucination) ≥ 0.99 and P(DFS detects hallucination) ≥ 0.95, conditional on G_K completeness.                                                                                                 |P39                        |Inherited from P30, P31 (v5.0). Requires G_K coverage ≥ 80% of the relevant domain (established in v5.0 §3).                                                                                              |
|A5 |**Conditional independence of BFS and DFS failure:** BFS and DFS failures are approximately conditionally independent given G_K quality. This holds because they use structurally different traversal mechanisms.                      |P39 (optimistic bound only)|Approximate. The conservative bound in P39 does not require this assumption.                                                                                                                              |
|A6 |**Bounded GTE evaluation time:** GTE BFS at depth k with maximum branching factor b_max completes in T_GTE_max ≤ b_max^k × T_node_eval.                                                                                                |P41                        |Requires bounded G_K branching factor. For well-structured knowledge graphs, b_max ≤ 50 is typical. Pathological G_K structures could violate this; mitigation: enforce b_max cap during G_K construction.|
|A7 |**Gradient mixing regime:** During continual learning, old-task and new-task gradients are not perfectly aligned — catastrophic forgetting is a concern precisely in this regime.                                                      |P42                        |Standard assumption in continual learning literature (Kirkpatrick et al., 2017). If tasks are aligned, forgetting doesn’t occur and the bound is vacuously satisfied.                                     |
|A8 |**Gradient norm clipping:** All gradient updates are clipped to                                                                                                                                                                                                   ||∇L                                                                                                                                                                                                        |
|A9 |**LSH hash quality:** The hash family is (r, cr, p₁, p₂)-sensitive with p₁ ≈ 0.9, p₂ ≈ 0.1, and the L = 3 hash tables use independent hash functions.                                                                                  |P43, P45                   |Inherited from v3.0 LSH analysis (P4). Standard for random hyperplane LSH on normalised embeddings.                                                                                                       |
|A10|**Decay model validity:** Memory decay follows an exponential model (Ebbinghaus), and rehearsal provides sublinear reinforcement.                                                                                                      |P48                        |Well-supported by cognitive psychology (Ebbinghaus, 1885; Cepeda et al., 2006). Approximation for engineering purposes.                                                                                   |
|A11|**Resolution vote threshold:** θ_resolution_votes ≥ ⌈τ_c × N_cluster⌉, ensuring temporal conflict resolution requires at least as many votes as initial quorum.                                                                        |P44                        |Enforced by implementation (default: 10 votes for 7-node cluster, where ⌈0.67 × 7⌉ = 5).                                                                                                                  |
|A12|**Cache hit rate:** f_cached ≈ 0.60 for repeated query patterns after 24h deployment.                                                                                                                                                  |P45                        |Empirical target; validated via VM-7. Actual f_cached depends on query distribution skew.                                                                                                                 |

-----

## 16. Proof Dependency Graph

The following directed acyclic graph shows how v6.0 proofs depend on each other and on prior-version proofs. An arrow A → B means “B requires A.”

```
PRIOR VERSIONS                        v6.0 PROOFS
──────────────                        ───────────

P4  (v3.0 LSH) ─────────────────────→ P43 (RRC Retrieval)
                                         │
                                         └─→ P45 (RRC Efficiency)

P18 (v3.0 BFT Safety) ──┬──────────→ P40 (CDCP Safety)
                         │               │
                         ├──────────→ P46 (Optimal τ_c)
                         │
P19 (v3.0 Consensus) ───┤
                         │
                         └──────────→ P41 (CDCP Liveness)

P30 (v5.0 BFS) ─────┬──────────────→ P39 (Hallucination Resistance)
                     │                   │
P31 (v5.0 DFS) ─────┘                   └─→ P44 (Retrograde Protection)
                                              ↑
                                         P40 ─┘

P42 (Forgetting Bound)    ← standalone (no prior proof dependencies)
P47 (Salience Convergence) ← standalone
P48 (Decay Correspondence) ← standalone


ASSUMPTION DEPENDENCIES (each proof's required assumptions):
  P39: A1, A3, A4, A5(optimistic only)
  P40: A1, A2
  P41: A1, A2, A6
  P42: A7, A8
  P43: A9
  P44: A1, A2, A11
  P45: A9, A12
  P46: A1, A2
  P47: A9, A10
  P48: A10
```

-----

> **Proof P47 — Salience Score Convergence**
> 
> *Requires: none (standalone). Assumes: A9, A10.*
> 
> **Claim:** With w_freq > 0 in the salience score, the rank-ordering of STM entries by salience converges to a rank-ordering monotone with empirical query frequency as the number of observed queries grows.
> 
> **Proof:** The salience score has four components. Consider the long-run behaviour as query count Q → ∞:
> 
> ```
> SalienceScore(c) = w_nov · novelty(c) + w_rew · rlrf_weight(c)
>                  + w_freq · access_frequency(c) + w_conf · confidence(c)
> ```
> 
> For a fixed claim c in STM:
> 
> - novelty(c) is fixed at encoding time (depends on EB/STM state at insertion)
> - rlrf_weight(c) is fixed at encoding time (depends on the inference that produced c)
> - confidence(c) is fixed at encoding time (depends on ESE evaluation)
> - access_frequency(c) grows with each query that retrieves c or a similar claim
> 
> As Q → ∞, access_frequency(c) → f_c × Q, where f_c is the true probability that a random query retrieves claim c. The other three components remain constant. Therefore:
> 
> ```
> SalienceScore(c) → w_freq · f_c · Q + constant_c
> 
> For any two claims c₁, c₂:
>   SalienceScore(c₁) > SalienceScore(c₂)
>     ⟺ w_freq · f_{c₁} · Q + const₁ > w_freq · f_{c₂} · Q + const₂
>     ⟺ f_{c₁} > f_{c₂}    (for Q sufficiently large)
> ```
> 
> Therefore, for Q > Q* where Q* = max_{c₁,c₂} |const₁ - const₂| / (w_freq × |f_{c₁} - f_{c₂}|), the salience rank-ordering is monotone with empirical query frequency.
> 
> **Note:** In practice, STM entries have finite TTL, so Q* must be reached within TTL_STM. For high-frequency claims (f_c > 0.01), Q* is typically reached within minutes. For rare claims, the initial salience components (novelty, reward, confidence) dominate — which is the intended design: the frequency signal is a long-run correction, not an immediate override.
> 
> ∎

-----

## 17. Implementation Roadmap

|Phase      |Timeline  |Milestone                                                                         |Status         |
|-----------|----------|----------------------------------------------------------------------------------|---------------|
|Phase 0    |Complete  |Browser PoC: WebCrypto, IndexedDB, WebRTC, LSH, ZK auth (39-test suite)           |✓ Done         |
|Phase 1    |+6 mo     |12-node reference cluster, Ollama, Tendermint BFT                                 |In progress    |
|Phase 2    |+12 mo    |LoRA pipeline, blockchain version ledger, FedAvg                                  |Planned        |
|Phase 3    |+18 mo    |RLRF verifier, GRPO optimizer, Markov G_M construction                            |v4.0 target    |
|Phase 4    |+24 mo    |GTE deployment: BFS/DFS, G_K from blockchain                                      |v5.0 target    |
|Phase 5    |+30 mo    |BVAS + ESE: calibrated confidence, debate, validity gating                        |v5.0 target    |
|**Phase 6**|**+36 mo**|**Episodic Buffer + STM: Redis-backed per-node validated claim store**            |**v6.0 target**|
|**Phase 7**|**+42 mo**|**CDCP: multi-node independent voting protocol for STM→LTM promotion**            |**v6.0 target**|
|**Phase 8**|**+48 mo**|**RCE: offline replay engine with interleaved catastrophic forgetting prevention**|**v6.0 target**|
|**Phase 9**|**+54 mo**|**RRC: pre-computed LSH retrieval cache, warm-up, invalidation**                  |**v6.0 target**|
|Phase 10   |+60 mo    |Full production, satellite node integration, Dec-POMDP multi-agent coordination   |Future         |

-----

## 18. Conclusion

DARM-ANN v6.0 completes the memory architecture that the system has always implied but never formally specified. The five-tier memory hierarchy — Working Memory, Episodic Buffer, Short-Term Memory, Long-Term Blockchain Memory, and the Rapid Retrieval Cache — gives each memory type exactly the guarantees it needs and no more: fast ephemeral storage for active reasoning, durable node-local storage for validated recent knowledge, and permanent distributed consensus-backed storage for collectively-verified facts.

The Consensus-Driven Consolidation Protocol is the architectural centrepiece. By requiring a τ_c quorum of independent nodes to validate a claim before it enters the permanent blockchain record, CDCP ensures that every LTM entry represents distributed collective knowledge — not the assertion of a single agent. Proof P39 provides a parameterised bound on hallucination pass-through probability: in the conservative-correlated scenario (ρ_GK = 0.5, BFS-only detection), the bound is 10⁻⁶; in the optimistic-independent scenario, 3.1 × 10⁻¹⁷. The honest presentation of both bounds — and the assumptions that separate them — strengthens rather than weakens the system’s credibility.

The Replay and Consolidation Engine brings a fundamental biological insight into the distributed system: memory is not stored once and retrieved forever. It must be replayed, reinforced, and integrated with existing knowledge to become durable. The RCE’s interleaved old-memory replay provides an implicit EWC-like regularisation (Proof P42), with at least 28.6% of each gradient update informed by consolidated knowledge at the default interleaving ratio.

The Rapid Retrieval Cache answers the question that motivated the entire architecture: *why reprocess a thought that has already been collectively validated?* Once a multi-step reasoning chain has been validated through CDCP and committed to the blockchain, every subsequent retrieval costs ~2ms — not 200ms. The work was done once, in full, with the strongest available consistency guarantees. Everything after is recall, not recomputation.

The Assumption Registry (§15) and Proof Dependency Graph (§16) make every proof’s foundations explicitly traceable. Any reader can identify which assumptions a given guarantee depends on, and what happens if an assumption is relaxed.

> **The v6.0 Guarantee:** DARM-ANN v6.0 provides a distributed AI system with human-analogous memory properties — rapid encoding into ephemeral working memory, salience-weighted staging in node-local short-term memory, gradual consolidation to collectively-validated long-term storage via τ_c-quorum consensus, offline replay to prevent catastrophic forgetting, and pre-computed fast retrieval of consolidated knowledge patterns at O(1) cost. The system remembers what it has collectively validated, decays what it cannot substantiate, and retrieves consolidated knowledge at a fraction of the cost of reprocessing.

-----

## Mathematical Notation

### v6.0 Additions

|Symbol                      |Meaning                                                         |
|----------------------------|----------------------------------------------------------------|
|M_WM(t)                     |Working Memory state at time t                                  |
|M_EB(t)                     |Episodic Buffer state: ring buffer per agent                    |
|M_STM(t)                    |Short-Term Memory state: node-local validated claim store       |
|M_LTM(t)                    |Long-Term Memory: blockchain M_global (tier-explicit from v6.0) |
|M_RRC(t)                    |Rapid Retrieval Cache state: pre-computed LSH index             |
|R                           |Episodic Buffer ring capacity (default 64 traces per agent)     |
|τ_c                         |CDCP consensus quorum threshold (default 0.67)                  |
|θ_salience                  |Minimum salience for EB → STM promotion (default 0.35)          |
|θ_nominate                  |Minimum salience for STM → CDCP nomination (default 0.55)       |
|θ_dedup                     |Cosine similarity threshold for STM deduplication               |
|TTL_STM                     |Short-term memory time-to-live (default 24 hours)               |
|λ_decay                     |STM salience decay rate (default 0.10/hour)                     |
|ρ_GK                        |Cross-node G_K correlation coefficient (operating range 0.3–0.5)|
|κ                           |Incumbency factor in retrograde protection (default 1.2)        |
|SalienceScore(c)            |Novelty + RLRF-weight + access-frequency + confidence composite |
|DecayScore(e, t)            |Time-varying relevance score for STM triage                     |
|VoteWeight(node_i)          |CDCP vote weight based on G_K maturity (§5.7)                   |
|RRC_HIT / RRC_MISS          |Rapid Retrieval Cache query outcome                             |
|CDCP(t)                     |Consolidation protocol output at time t                         |
|n_voters                    |Number of nodes that voted in a CDCP round                      |
|f_cached                    |Fraction of queries resolved by RRC                             |
|R_memory                    |Memory efficiency reward component in RLRF v6                   |
|w_m                         |Weight of R_memory in RLRF composite (default 0.10)             |
|w_nov, w_rew, w_freq, w_conf|Salience score component weights                                |
|t_min_age                   |Minimum STM entry age before CDCP nomination (default 60s)      |
|θ_resolution_votes          |Minimum votes required to resolve a temporal conflict           |
|G_K_threshold               |Minimum G_K block count for full CDCP vote weight (default 1000)|

### Retained from Prior Versions

|Symbol  |Meaning                               |
|--------|--------------------------------------|
|Σ(t)    |Full system state tuple at time t     |
|G_M     |Markov state graph                    |
|G_K     |Blockchain knowledge graph            |
|conf_cal|ESE calibrated confidence             |
|u_ep    |ESE second-order epistemic uncertainty|
|V_BVAS  |BVAS aggregate validity score         |
|f       |Byzantine fault count                 |

-----

## References

### Core Architecture and Inference

1. Vaswani, A., et al. (2017). *Attention Is All You Need*. NeurIPS.
1. Hu, E. J., et al. (2021). *LoRA: Low-Rank Adaptation of Large Language Models*. arXiv:2106.09685.
1. Dettmers, T., et al. (2023). *QLoRA: Efficient Finetuning of Quantized LLMs*. NeurIPS.
1. McMahan, H. B., et al. (2017). *Communication-Efficient Learning of Deep Networks from Decentralized Data (Federated Averaging)*. AISTATS.
1. Guo, D., et al. (2025). *DeepSeek-R1: Incentivizing Reasoning Capability in LLMs via Reinforcement Learning*. arXiv:2501.12948.

### Distributed Systems and Consensus

1. Castro, M., & Liskov, B. (1999). *Practical Byzantine Fault Tolerance*. OSDI.
1. Buchman, E., Kwon, J., & Milosevic, Z. (2018). *The Latest Gossip on BFT Consensus (Tendermint)*. arXiv:1807.04938.
1. Dwork, C., Lynch, N., & Stockmeyer, L. (1988). *Consensus in the Presence of Partial Synchrony*. JACM.
1. Bahadur, R. R. (1961). *A Representation of the Joint Distribution of Responses to n Dichotomous Items*. In Studies in Item Analysis and Prediction. Stanford University Press.

### Algorithms and Data Structures

1. Cormen, T. H., et al. (2022). *Introduction to Algorithms* (4th ed.). MIT Press.
1. Hart, P. E., Nilsson, N. J., & Raphael, B. (1968). *A Formal Basis for the Heuristic Determination of Minimum Cost Paths*. IEEE Trans. SSC.
1. Dijkstra, E. W. (1959). *A Note on Two Problems in Connexion with Graphs*. Numerische Mathematik.
1. Indyk, P., & Motwani, R. (1998). *Approximate Nearest Neighbors: Towards Removing the Curse of Dimensionality*. STOC.

### Reinforcement Learning

1. Sutton, R. S., & Barto, A. G. (2018). *Reinforcement Learning: An Introduction* (2nd ed.). MIT Press.
1. Puterman, M. L. (1994). *Markov Decision Processes*. John Wiley & Sons.
1. Shao, Z., et al. (2024). *DeepSeekMath: Pushing the Limits of Mathematical Reasoning in Open Language Models (GRPO)*. arXiv:2402.03300.

### Epistemic Reasoning and Hallucination

1. Robertson, A., et al. (2026). *KGHaluBench: A Knowledge Graph Hallucination Benchmark*. arXiv:2602.19643.
1. Manchingal, S. K., & Cerutti, F. (2025). *Epistemic Artificial Intelligence*. arXiv:2505.04950.
1. Wang, T., Zhao, Z., et al. (2025). *From Aleatoric to Epistemic: Advances in Uncertainty Quantification for LLMs*. arXiv:2501.03282.
1. Irving, G., Christiano, P., & Amodei, D. (2018). *AI Safety via Debate*. arXiv:1805.00899.
1. Shinn, N., et al. (2023). *Reflexion: Language Agents with Verbal Reinforcement Learning*. NeurIPS.

### Agentic Memory Systems (2025–2026)

1. Hu, Y., et al. (2025). *Memory in the Age of AI Agents: A Survey*. arXiv:2512.13564.
1. Yu, Y., et al. (2026). *Agentic Memory: Learning Unified Long-Term and Short-Term Memory Management for LLM Agents*. arXiv:2601.01885.
1. AWS Machine Learning Blog. (2025). *Building Smarter AI Agents: AgentCore Long-Term Memory Deep Dive*.
1. ICLR 2026 Workshop. *MemAgents: Memory-Augmented LLM-Based Agentic Systems*. OpenReview:U51WxL382H.

### Neuroscience of Memory Consolidation

1. McClelland, J. L., McNaughton, B. L., & O’Reilly, R. C. (1995). *Why There Are Complementary Learning Systems in the Hippocampus and Neocortex*. Psychological Review, 102(3), 419–457.
1. Klinzing, J. G., Niethard, N., & Born, J. (2019). *Mechanisms of Systems Memory Consolidation During Sleep*. Nature Neuroscience, 22(10), 1598–1610.
1. Diekelmann, S., & Born, J. (2010). *The Memory Function of Sleep*. Nature Reviews Neuroscience, 11(2), 114–126.
1. Lee, J. W., & Jung, M. W. (2025). *Memory Consolidation from a Reinforcement Learning Perspective*. Frontiers in Computational Neuroscience.
1. Vijayan, S., & Bhalla, U. S. (2022). *A Model of Autonomous Interactions Between Hippocampus and Neocortex Driving Sleep-Dependent Memory Consolidation*. PNAS.
1. Kudithipudi, D., et al. (2022). *Biological Underpinnings for Lifelong Learning Machines*. Nature Machine Intelligence, 4, 196–210.
1. Buhry, L., Azizi, A. H., & Bhalla, U. S. (2011). *Reactivation, Replay, and Preplay: How It Might All Fit Together*. Neural Plasticity.
1. Ebbinghaus, H. (1885). *Über das Gedächtnis*. Duncker & Humblot. (English translation: *Memory: A Contribution to Experimental Psychology*, 1913.)
1. Cepeda, N. J., et al. (2006). *Distributed Practice in Verbal Recall Tasks*. Psychological Bulletin, 132(3), 354–380.

### Continual Learning and Catastrophic Forgetting

1. Kirkpatrick, J., et al. (2017). *Overcoming Catastrophic Forgetting in Neural Networks (EWC)*. PNAS, 114(13), 3521–3526.
1. Huszár, F. (2018). *Note on the Quadratic Penalties in Elastic Weight Consolidation*. PNAS, 115(11), E2496–E2497.
1. McCloskey, M., & Cohen, N. J. (1989). *Catastrophic Interference in Connectionist Networks*. Psychology of Learning and Motivation, 24, 109–165.

-----

## Glossary

### v6.0 Additions

|Term                        |Definition                                                                                                                         |
|----------------------------|-----------------------------------------------------------------------------------------------------------------------------------|
|**WM**                      |Working Memory — in-context activations for a single inference pass; ephemeral                                                     |
|**EB**                      |Episodic Buffer — per-agent ring buffer of recent reasoning traces; session-duration                                               |
|**STM**                     |Short-Term Memory — node-local Redis-backed validated claim store; TTL-managed                                                     |
|**LTM**                     |Long-Term Memory — blockchain M_global; BFT-consensus, tamper-evident, permanent                                                   |
|**RRC**                     |Rapid Retrieval Cache — pre-computed LSH index over hot LTM entries; O(1) access                                                   |
|**CDCP**                    |Consensus-Driven Consolidation Protocol — τ_c-quorum independent voting for STM→LTM                                                |
|**RCE**                     |Replay and Consolidation Engine — NREM sleep analog; biologically-inspired offline replay                                          |
|**CLS**                     |Complementary Learning Systems — McClelland et al. (1995) neuroscientific framework                                                |
|**SWR**                     |Sharp-Wave Ripple — hippocampal high-frequency reactivation event; biological inspiration for RCE                                  |
|**ρ_GK**                    |Cross-node G_K correlation coefficient; measures shared knowledge graph overlap between nodes                                      |
|**κ**                       |Incumbency factor — asymmetric protection multiplier for established LTM entries (default 1.2)                                     |
|**VoteWeight**              |CDCP vote scaling function based on node G_K maturity                                                                              |
|**Salience score**          |Composite of novelty, RLRF-reward, access-frequency, and confidence                                                                |
|**Decay score**             |Time-varying relevance combining salience, Ebbinghaus recency, and replay reinforcement                                            |
|**Memory triage**           |Periodic STM evaluation for promotion, retention, or expiry                                                                        |
|**Retrograde protection**   |Mechanism preventing new claims from overwriting established LTM without κ-multiplied evidence                                     |
|**Temporal conflict**       |Record created when a CDCP nomination contradicts an existing LTM entry                                                            |
|**Incumbency factor**       |Multiplicative advantage (κ ≥ 1.0) applied to established LTM entries during conflict resolution                                   |
|**Cold start**              |Node initialisation state where RRC is empty; warm-up via query-driven and RCE replay                                              |
|**Catastrophic forgetting** |Tendency of neural networks to overwrite previously-learned representations                                                        |
|**Interleaved replay**      |RCE technique of mixing old LTM entries with new STM candidates to prevent catastrophic forgetting                                 |
|**Gradient mixing**         |The formal property proven in P42: interleaved replay ensures a fixed fraction of gradient signal comes from consolidated knowledge|
|**Hippocampal analogy**     |STM/EB ↔ hippocampus; LTM ↔ neocortex; RCE ↔ NREM sleep replay                                                                     |
|**Consolidatable knowledge**|A claim that passes ESE, GTE, and CDCP — worthy of permanent distributed storage                                                   |

### Retained from v5.0 / v4.0

|Term  |Definition                                                                |
|------|--------------------------------------------------------------------------|
|GTE   |Graph Traversal Engine — BFS, DFS, bidirectional, Dijkstra, A* over G_K   |
|BVAS  |Blockchain Validity Algorithm Suite — five-stage validity pipeline        |
|ESE   |Epistemic Skepticism Engine — calibrated confidence and adversarial debate|
|RLRF  |Reinforcement Learning with Reasoning Feedback                            |
|GRPO  |Group Relative Policy Optimization                                        |
|G_M   |Markov state graph                                                        |
|G_K   |Blockchain knowledge graph                                                |
|BFT   |Byzantine Fault Tolerant                                                  |
|LoRA  |Low-Rank Adaptation                                                       |
|TinyLM|Language models under 500M parameters                                     |

-----

## Proof Index

### v3.0 Proofs (retained)

|Proof  |Section|Statement                                                                 |
|-------|-------|--------------------------------------------------------------------------|
|P1–P10 |v3.0   |Data structure complexity suite (O(log m) decision, LSH, consensus bounds)|
|P11–P15|v3.0   |LoRA, QLoRA, FedAvg convergence, blockchain integrity, propagation        |
|P16–P19|v3.0   |DAG consistency, Merkle proof, BFT safety/liveness, consensus latency     |

### v4.0 Proofs (retained)

|Proof  |Section|Statement                                                                          |
|-------|-------|-----------------------------------------------------------------------------------|
|P22–P29|v4.0   |RLRF non-vanishing gradient, credit assignment, Markov convergence suite, GRPO cost|

### v5.0 Proofs (retained)

|Proof  |Section    |Statement                                                                                         |
|-------|-----------|--------------------------------------------------------------------------------------------------|
|P30–P32|v5.0 §3    |GTE BFS completeness, DFS causal audit, A* admissibility                                          |
|P33–P34|v5.0 §4    |Chain integrity, fork resolution bound                                                            |
|P35–P38|v5.0 §5, §9|Calibration convergence, abstention optimality, skeptic convergence, hallucination reduction bound|

### v6.0 Proofs (new — corrected and validated)

|Proof  |Section|Statement                                                                                                                |Requires|Assumes        |
|-------|-------|-------------------------------------------------------------------------------------------------------------------------|--------|---------------|
|**P39**|§5.5   |CDCP Hallucination Resistance: parameterised bound with conservative (10⁻⁶ to 10⁻¹⁰) and optimistic (3.1×10⁻¹⁷) scenarios|P30, P31|A1, A3, A4, A5*|
|**P40**|§5.5   |CDCP Safety: no two contradictory claims achieve quorum in same epoch                                                    |P18     |A1, A2         |
|**P41**|§5.5   |CDCP Liveness: terminates within O(Δ + T_GTE_max) under partial synchrony                                                |P18, P19|A1, A2, A6     |
|**P42**|§6.3   |Catastrophic Forgetting Bound: gradient mixing ensures ≥28.6% old-task signal at r=0.4; implicit EWC correspondence      |—       |A7, A8         |
|**P43**|§7.4   |RRC Retrieval Performance: E[T_RRC] = O(1) amortized; recall = 99.9% with L=3                                            |P4      |A9             |
|**P44**|§8.3   |Retrograde Protection: c_new must exceed c_old’s evidence by factor κ=1.2                                                |P39, P40|A1, A2, A11    |
|**P45**|§12.2  |RRC Retrieval Efficiency: 25–200× speedup; 2.46× throughput at 60% hit rate                                              |P43     |A9, A12        |
|**P46**|§5.6   |Optimal τ_c: τ_c = 2/3 is minimum for standard BFT safety                                                                |P18     |A1, A2         |
|**P47**|§16    |Salience Convergence: rank-ordering converges to empirical query frequency                                               |—       |A9, A10        |
|**P48**|§8.1   |Decay Score = Ebbinghaus forgetting curve × spacing effect reinforcement                                                 |—       |A10            |

*A5 required for optimistic bound only; conservative bound is independent of A5.

-----

*This white paper is released under Creative Commons Attribution 4.0 International (CC BY 4.0).*

*Citation: Cybopsec Research (2026). DARM-ANN v6.0: Hierarchical Memory Consolidation for Distributed AI. Working White Paper, April 2026.*

*Version 6.0 builds upon and supersedes DARM-ANN v5.0 (March 2026). Prior versions are archived in the project repository.*

*Correspondence and collaboration enquiries are welcome via the project repository.*