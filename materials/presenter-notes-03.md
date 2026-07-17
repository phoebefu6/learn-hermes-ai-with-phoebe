# Presenter notes - Session 3 · Steer it: system prompts and personas

Student-facing page: courses/03-steer-it.html. These notes are for the presenter only.

## Preflight (do the night before, not the morning)

- [ ] `hermes4-14b-16k` from Session 2 builds and runs on the demo machine - Demo 1 edits that exact Modelfile, so `~/hermes-lab/Modelfile` must be where the session left it
- [ ] Keep the PLAIN 14B build available too (`ollama run hf.co/bartowski/...:Q4_K_M`) - Demo 2's run A needs the no-SYSTEM version
- [ ] Write your own example constitution in advance and rehearse the full loop: add SYSTEM, rebuild, say hello, run all three attacks - know how YOUR persona responds before doing it live
- [ ] Clipboard/snippets ready: the constitution skeleton, the anti-sycophancy line, the upgraded Modelfile block, the deliberately flawed BI-migration plan
- [ ] Have a backup constitution pre-filled for attendees who freeze on the blank-page five minutes
- [ ] Expect stragglers without the Session 2 build - prepare the one-liner catch-up (pull command + 3-line Modelfile) on a slide or handout, not live debugging
- [ ] Fast-moving product: re-verify the template map before class - 14B/Hermes 3 = ChatML, 70B/405B/4.3 = Llama-3 headers; any new Hermes release since the page was written may add a row

## Run of show

| Min | Beat | Notes |
|-----|------|-------|
| 0-3 | Welcome + cashing Session 1's promise | "Today your assistant stops being A model and becomes MY assistant." Most people never touch the system prompt - that is the hook |
| 3-9 | Part 1: the constitution | Anatomy SVG on projector zoom: identity, knowledge and tone, rules, guardrails. The onboarding-buddy story sells persona persistence; say plainly that Hermes will NOT add its own guardrails - you write them |
| 9-14 | Part 2: chat templates | One card only: the ChatML block on screen, the midnight-bug story, "the template is usually the crime scene". Do not present the why-two-formats self-study card |
| 14-19 | Part 3: sampling + anti-sycophancy | Official trio fast (they already baked temperature 0.6 in Session 2); spend the time on anti-sycophancy - "it changes the reasoning, not just the tone" is the session's biggest claim |
| 19-31 | Demo 1: the persona lab | 5 min silent writing (skeleton on screen), then SYSTEM into Modelfile, rebuild, hello, and the three attacks: break character, flatter-bait, contradict. Score out loud |
| 31-39 | Demo 2: A/B steering | Flawed plan into plain build (run A) then their build (run B); compare WHERE each engages; push back on B and watch it hold. This reproduces the report's claim on their laptops |
| 39-40 | Cheat sheet + homework pointer | v2 constitution, one real pushback case for Session 4, second persona |
| 40-45 | Q&A | Park template internals and the assistant-to-me curiosity to self-study |

## Never-cut beats

1. The Demo 2 A/B moment - same model, same plan, the anti-sycophancy build attacks the premise while the default flatters; this is the session's wifi-off equivalent
2. The three attacks in Demo 1 - persona trust is EARNED by attacking it, and the edit-rebuild-attack loop IS prompt engineering
3. "Guardrails are yours to write" - neutral alignment means the refusal policy comes from their constitution, not the lab; say it once, plainly
4. "Vague steers nothing" - replace friendly-and-professional with behaviors a stranger could grade; this one line fixes 80% of flat personas

## Cuts if long

- Part 3 sampling card - compress to "you already set 0.6; lower for extraction, higher for brainstorming" in 30 seconds
- Demo 2 step 4 (the push-back-on-B round) - the A/B comparison alone carries the claim
- The midnight-bug story in Part 2 - the ChatML block plus "crime scene" line suffices
- Self-study cards (why two formats, curiosity corner) - never present them

## Q&A landmines

- "Can someone extract or override my system prompt?" - Assume yes with enough effort; the constitution is steering, not security. Real secrets never go in prompts, and Session 6 covers where enforcement actually lives (your code).
- "Is putting facts about me in the prompt a privacy risk?" - It stays on your machine with a local model - that is the whole point of the course. On hosted routes, treat the constitution like anything else you upload.
- "My persona slipped on attack 1 - is Hermes overhyped?" - Slips usually trace to vague wording or a thin identity layer. Tighten the layer that broke, rebuild, re-attack. The report's claim is strong adherence, not invincibility.
- "Should temperature be 0 for serious work?" - Near-0 is for extraction and strict formatting. 0.6 is the official recommendation for general work; move one dial at a time from the trio.
- "Will the anti-sycophancy build just be contrarian about everything?" - Written well, it challenges shaky premises and agrees with sound ones. If it argues with everything, your rule said "always disagree" - fix the wording, not the idea.
