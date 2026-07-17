# Official Course Map - learn-hermes-ai-with-phoebe

Research date: 2026-07-17. Hermes moves fast - re-verify the Nous releases page and changelog before each delivery.

## Scope decisions (grilled + locked)

- Topic: Nous Research Hermes model family (+ Hermes Agent capstone)
- Audience: dual - org teams AND public/KOL followers
- Access paths taught: Local (Ollama / LM Studio) PRIMARY + Nous Portal API secondary
- Format: 8 sessions x 45 min (3 welcome / ~15 concepts / ~22 build-along / 5 Q&A)
- Spine: running-project arc - every session upgrades the same artifact: "your own private AI assistant"
- Repo: public + GitHub Pages from day one
- Design: Nous brand-mimic (paper / ink / electric blue, serif + mono)

## Source universe (fetched, not guessed)

| # | Source | URL | Status |
|---|--------|-----|--------|
| S1 | Nous Research releases timeline (23 items, 03/2024-02/2026) | nousresearch.com/releases | fetched |
| S2 | Hermes 4 Technical Report (41pp, arXiv 2508.18255) | arxiv.org/abs/2508.18255 | fetched, full section map |
| S3 | Hermes 4.3 announcement (Psyche-trained, 512K ctx) | nousresearch.com/introducing-hermes-4-3 | fetched |
| S4 | HF model cards: Hermes 4 405B/70B/14B, 4.3-36B, Hermes 3, DeepHermes-3 | huggingface.co/NousResearch | fetched |
| S5 | Hermes-Function-Calling repo (canonical tool-calling format) | github.com/NousResearch/Hermes-Function-Calling | fetched |
| S6 | Hermes Agent docs (local-ollama-setup, providers, nous-portal) | hermes-agent.nousresearch.com/docs | fetched |
| S7 | Ollama library (hermes3 official; Hermes 4 via hf.co pulls) | ollama.com/library/hermes3 | fetched |
| S8 | LM Studio Hermes pages (GGUF + MLX, reasoning toggle UI) | lmstudio.ai/models/nousresearch | fetched |
| S9 | OpenRouter Nous listings + pricing | openrouter.ai/nousresearch | fetched |
| S10 | Community tutorial corpus (YouTube, guides, Unsloth, OpenRouter blog) | various | surveyed |

Login-walled / bot-gated: portal.nousresearch.com (429/Vercel gate), hermes4.nousresearch.com. Pricing numbers must be hand-verified in a browser before publishing.

## Verified facts (teaching backbone)

### Model family

| Model | Params | Base | Context | License | Template | Released |
|---|---|---|---|---|---|---|
| Hermes 4.3 36B | 36B | Seed-OSS-36B | 512K | Apache 2.0 | Llama-3-style headers (re-verify) | 2025-12-03 |
| Hermes 4 14B | 14B | Qwen3-14B | 40,960 | Apache-2.0-family | ChatML | 2025-08-26 |
| Hermes 4 70B | 70B | Llama-3.1-70B | 131K (LM Studio source) | Llama 3 | Llama-3 headers | 2025-08-26 |
| Hermes 4 405B | 405B | Llama-3.1-405B | 131K | Llama 3 | Llama-3 headers | 2025-08-26 |
| Hermes 3 | 3/8/70/405B | Llama-3.1/3.2 | 128K | Llama 3 | ChatML | 2024-08 |
| DeepHermes-3 8B | 8B | Llama-3.1-8B | 128K | Llama 3 | ChatML | 2025-02 |

- Sampling recommendation (official): temperature 0.6, top_p 0.95, top_k 20
- Hybrid reasoning: `<think>` tags; enable via chat-template `thinking=True`, system prompt, or LM Studio UI toggle; self-terminates ~30k reasoning tokens (2nd SFT stage)
- Tool calling: JSON schemas in `<tools>...</tools>` system block; model emits `<tool_call>{...}</tool_call>`; results in `<tool_response>`; vLLM parser literally named `hermes`
- JSON mode: `<schema>` system prompt, Pydantic-validated, trained to repair malformed JSON
- RefusalBench (Nous's signature metric): Hermes 4 405B 57.1 vs DeepSeek R1 16.7; 4.3 hits 74.6 - the "neutral alignment" quantification
- Hermes 4 recipe: DataForge (DAG synthetic data), Atropos rejection sampling, ~5M samples/19B tokens (4.3: ~60B), pure SFT, 192 B200s
- Hermes 4.3 = first production model post-trained on Psyche (DisTrO, 24 nodes, Solana-coordinated); centralized twin released as research artifact
- Hermes Agent (2026-02-25, MIT): flagship open-source agent, desktop app, model-agnostic, channels (Telegram/Discord/Slack/WhatsApp/Signal/Email), skills + persistent memory. NOT a model - the community tutorial ecosystem pivoted to it.

### Mac feasibility (local track)

| Mac RAM | Comfortable | Course role |
|---|---|---|
| 16GB | Hermes 3 8B; Hermes 4 14B Q4_K_M (9.0GB, bartowski GGUF) | 14B = hero model |
| 32GB | 14B up to Q8; 4.3-36B Q3_K_M (17.6GB) safe, Q4_K_M borderline | 36B stretch demo |
| 64GB | 70B Q4_K_M (~40GB) | power users |
| any | 405B local: no (Q4 ~229GB) | API only |

Key commands (verified from official pages):
- `ollama run hermes3:8b` (official library)
- `ollama run hf.co/bartowski/NousResearch_Hermes-4-14B-GGUF:Q4_K_M` (HF pull path)
- `ollama run hf.co/NousResearch/Hermes-4.3-36B-GGUF:Q4_K_M`
- Modelfile: `FROM hf.co/... / PARAMETER num_ctx 16384` then `ollama create`
- Context gotcha: Ollama default ctx tiny; every community guide teaches raising it (`OLLAMA_CONTEXT_LENGTH` / num_ctx)

### API track

- Nous Portal: portal.nousresearch.com; endpoint `https://inference-api.nousresearch.com/v1`, OpenAI-compatible; free eval tier; tiers bundle Tool Gateway
- Pricing (UNVERIFIED - trackers conflict; hand-check): 70B ~$0.13/$0.40 (OpenRouter) vs ~$0.05/$0.20 (Portal per llmreference); 405B $1.00/$3.00
- OpenRouter: Hermes 3 405B has a `:free` variant - zero-cost API demo path for learners

## Session coverage map

Legend: full coverage ✓ / partial ◐

| Session | Title | Difficulty | Sources | Coverage |
|---|---|---|---|---|
| 1 | Meet Hermes - the AI that answers to you | green | S1 ✓, S3 ◐, S9 ◐ | family map, lineage, neutral alignment, first chat (Nous Chat + `ollama run hermes3:8b`) |
| 2 | Get it on your machine | green | S4 ◐, S7 ✓, S8 ✓ | quants, GGUF vs MLX, HF pull, LM Studio, context gotcha, Modelfile lab |
| 3 | Steer it - system prompts and personas | yellow | S2 §5 ✓, S4 ◐ | templates (ChatML vs Llama-3), sampling, persona lab, anti-sycophancy |
| 4 | Think when it matters - hybrid reasoning | yellow | S2 §3 ◐, S4 ✓, S8 ◐ | think tags, 3 activation surfaces, reasoning-vs-instant tradeoff table |
| 5 | Structured output - JSON that validates | orange | S5 ✓, S2 §2.2.4 ◐ | schema prompt, Pydantic, repair property, messy-text extraction |
| 6 | Tool calling - give it hands | orange | S5 ✓, S2 §2.2.5 ◐ | tools/tool_call/tool_response loop in ~20 lines Python vs localhost:11434/v1 |
| 7 | Hermes as a service - Portal, OpenRouter, licenses | yellow | S6 ◐, S9 ✓ | endpoint config, pricing math, license implications, local-vs-hosted decision |
| 8 | Capstone - your assistant goes autonomous (Hermes Agent) | red | S6 ✓, S10 ◐ | install, point at local Ollama or Portal, skills, memory, one channel |

## Deep-dive track (self-paced overflow)

- D1: How Hermes is made - DataForge, Atropos, rejection sampling (S2 §2)
- D2: Trained by the swarm - Psyche, DisTrO, the centralized-twin experiment (S3)
- D3: Production serving - vLLM `--tool-call-parser hermes`, SGLang, llama.cpp --jinja
- D4: Fine-tune your own Hermes - Unsloth/LoRA path
- D5: Reading RefusalBench - what "neutral alignment" means operationally + responsible use

## Not covered by design (honest list)

- Training/RL-tuning with Atropos itself (archived 2026-07-04; taught as history in D1)
- Forge Reasoning API (never left beta, dormant)
- Psyche node operation / GPU contribution
- Simulators/WorldSim lore (one culture callout in S1 only)
- Nomos 1 / NousCoder / Minos specialist models (namechecked in S1 family map)
- Official certificates do not exist for Hermes; no certification claims anywhere

## Pre-delivery re-verify list

- Portal pricing + tiers (bot-gated; hand-check in browser)
- Hermes 4.3-36B chat template (card says Llama-3 headers despite Seed base - test tokenizer)
- `llama-server` binary name (HF page snippet says `llama serve`)
- 36B Q4 on 32GB Mac (macOS wired-memory ceiling - test live)
- Hermes Agent star count + any new model since 2026-07
