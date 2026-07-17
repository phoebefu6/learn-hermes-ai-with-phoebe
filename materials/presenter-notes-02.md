# Presenter notes - Session 2 · Get it on your machine, properly

Student-facing page: courses/02-on-your-machine.html. These notes are for the presenter only.

## Preflight (do the night before, not the morning)

- [ ] Pull the 14B GGUF the night before - `ollama run hf.co/bartowski/NousResearch_Hermes-4-14B-GGUF:Q4_K_M` is a 9GB download that must never happen on venue wifi
- [ ] Keep `hermes3:8b` installed from Session 1 - Demo 1 is a side-by-side and dies without it
- [ ] Check demo Mac free RAM (Activity Monitor open) and free disk (~9GB was needed; confirm nothing evicted the model: `ollama list`)
- [ ] Pre-stage a `~/hermes-lab` folder and rehearse the Modelfile build once: create, `ollama create hermes4-14b-16k -f Modelfile`, `ollama show`, run
- [ ] Clipboard/snippets ready: the hard question prompt, the three Modelfile lines, both official pull commands
- [ ] Have a 2-3 page document ready to paste for the Demo 2 memory test (any real project brief works better than lorem ipsum)
- [ ] If showing the optional LM Studio branch: LM Studio installed, 14B MLX build downloaded, reasoning toggle located in advance
- [ ] Fast-moving product: re-verify that morning that there is still no official hermes4 in the Ollama library, and spot-check the quant file sizes on the bartowski and NousResearch HF repos - the tables in Part 1 go stale fast

## Run of show

| Min | Beat | Notes |
|-----|------|-------|
| 0-3 | Welcome + the premise | "Anyone can make it run; today it runs RIGHT." Three decisions: quant, runtime, context. Collect RAM numbers by show of hands - it warms up Part 2 |
| 3-9 | Part 1: quantization | Ladder SVG on projector zoom; land the photo analogy (RAW vs JPEG) and "Q4_K_M is the default answer". Quant-table card fast - it is a menu-reading skill, not a memorization test |
| 9-15 | Part 2: your rig | The pharmacy rule story sells the two-pull-paths card; then the RAM table - every attendee should point at their own row. Do NOT present the LM Studio self-study card |
| 15-19 | Part 3: the context gotcha | The senility SVG; num_ctx and the Modelfile. Say "the model was never broken, the window was" verbatim - it is the line people quote back |
| 19-29 | Demo 1: graduate to the hero | Everyone on the pre-pulled 14B (they pull at home); run the hard question on 14B, then hermes3:8b, compare out loud. The "which jobs need which brain" discussion is the point, not the answer |
| 29-39 | Demo 2: the Modelfile lab | Build hermes4-14b-16k together; `ollama show` to verify like an engineer; then the memory test - question about the START of a long pasted document |
| 39-40 | Cheat sheet + homework pointer | Quant ladder taste test + rebuild-from-memory assignments; quiz is self-serve |
| 40-45 | Q&A | Park deep LM Studio/MLX questions to the self-study card |

## Never-cut beats

1. The memory test in Demo 2 (asking about the top of a long document and getting it right) - this session's wifi-off moment; the audience must SEE the senility fix work
2. The pharmacy rule - pull from source-owned repos, never community re-ups; it protects them from the classic broken-template week of pain
3. "Q4_K_M is the sweet spot" + the RAM table row-pointing - the sizing instinct is the take-home skill
4. `ollama show` verification - trust, but verify; it seeds the engineering habit every later session leans on

## Cuts if long

- Demo 1 step 5 (the out-loud comparison discussion) - compress to one volunteer observation
- The quant-table menu card - the ladder SVG already carries the idea
- Demo 2 step 5 (the LM Studio branch) - it is optional by design and returns in Session 4
- Part 1 and Part 2 self-study cards (MLX vs GGUF, LM Studio) - never present them

## Q&A landmines

- "Why not just run Q8 for best quality?" - File size is RAM appetite: 15.7GB drowns a 16GB Mac once context and the OS join. And a bigger model at a lower quant beats a smaller one at a higher quant - spend RAM on parameters first.
- "I have a Windows/Linux machine, does any of this apply?" - Yes: GGUF, Ollama, quants, and num_ctx are identical. Only the Mac wired-memory ceiling and the MLX speed lane are Apple-specific.
- "My 36B pull fits on paper but crawls" - The macOS GPU wired-memory cap (~65-75% of RAM) is the culprit; drop to Q3_K_M or back to the 14B, and watch for swapping.
- "Do I need both Ollama and LM Studio?" - No. Ollama is the course spine (everything later scripts against it); LM Studio is an optional cockpit with an MLX speed win on Macs.
- "Can I just set num_ctx to the max?" - Context lives in RAM: 16K is the sane 16GB default, 32K+ is 32GB territory. Bigger window, less headroom, slower - size it like everything else today.
