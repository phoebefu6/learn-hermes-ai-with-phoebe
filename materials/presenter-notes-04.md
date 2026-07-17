# Presenter notes - Session 4 · Think when it matters: hybrid reasoning

Student-facing page: courses/04-hybrid-reasoning.html. These notes are for the presenter only.

## Preflight (do the night before, not the morning)

- [ ] The full DeepHermes toggle prompt verbatim in your clipboard manager - Demo 1 step 2 types `/set system "..."` live and fumbling the quote marks kills the momentum
- [ ] Run the scheduling puzzle through BOTH gears on the demo machine the night before - know your instant-gear answer (right or wrong, both are usable) and the real wall-clock time of the reasoning run at your tokens/sec
- [ ] Know the expected answer cold: Ana 9am, Cara 10am, Ben 11am, 1pm free - you will referee the group check
- [ ] LM Studio installed with the 14B loaded, reasoning toggle AND keep-CoT option located in advance - do not hunt for UI elements on the projector
- [ ] Clipboard/snippets ready: the puzzle, the thank-you-note counter-demo prompt, the Modelfile.think block for the homework pointer
- [ ] `hermes4-14b-16k` responds; remember its 16K window - a deep reasoning run can genuinely fill it, so know the symptom (cut-off answer) before it surprises you live
- [ ] Fast-moving product: re-verify the LM Studio toggle placement and the `thinking=` / `keep_cots=` chat-template flags that morning - UI and template kwargs move between releases

## Run of show

| Min | Beat | Notes |
|-----|------|-------|
| 0-3 | Welcome + the second gear | "Your assistant has had one speed. Today it gets judgment about effort." Right problems: transformative. Wrong problems: hot laptop |
| 3-9 | Part 1: one model, two gears | Two-lanes SVG on projector zoom; think tags are a readable scratchpad, the model budgets its own deliberation. Then the 30k self-stop yarn - tell it as a story, it lands the context lesson for free |
| 9-15 | Part 2: when thinking pays | The evidence table - read the AIME rows twice as the page says (11.4 to 81.9); then the ON/OFF rule of thumb and "tokens are seconds on your machine" |
| 15-20 | Part 3: the three switches | System prompt (verbatim, works everywhere), LM Studio toggle (one click), thinking=True in code. One minute each is enough - the demos do the teaching |
| 20-32 | Demo 1: the two-gear experiment | Puzzle in instant gear, note speed and confidence; /set system with the toggle prompt; same puzzle again; read the think block ALOUD together; check the answer as a group; count the cost |
| 32-40 | Demo 2: LM Studio + the counter-demo | Toggle route on the same puzzle, then the thank-you note in both gears - watch it deliberate about a thank-you note for nothing. Say the ON/OFF rule out loud one more time |
| 40-45 | Q&A + homework pointer | The reasoning-worthy checklist (5 real tasks, ON or OFF) feeds Session 5 routing - flag that it is not optional |

## Never-cut beats

1. Reading a real chain of thought aloud together in Demo 1 - the backtracking moment ("wait, that violates constraint 2") is this session's wifi-off moment and the thing hosted apps hide
2. The counter-demo - paying seconds and tokens to deliberate over a thank-you note; the OFF half of the rule only lands when they feel the waste
3. The AIME headline (11.4 instant vs 81.9 reasoning) - the one number that justifies the whole session
4. "Tokens are seconds on your machine" - the local cost intuition that hosted models hide behind someone else's GPUs

## Cuts if long

- Demo 2 steps 1-2 (the LM Studio toggle route on the puzzle) - show the toggle exists in 30 seconds and jump straight to the counter-demo
- The 30k self-stop card - compress to two sentences: "it used to think past its own context and score zero; Nous taught it to wrap up by ~30k"
- Switch 3 (the chat-template flag) - point at the cheat sheet; it becomes daily reality in Session 5 anyway
- Part 1 self-study card (why hybrid beats dedicated) - never present it

## Q&A landmines

- "Why not leave reasoning on all the time?" - The analyst story: every rephrase-this-Slack-message took ninety seconds and the assistant felt broken. Everyday answers barely improve; you just pay time, battery, and context. Two named variants, pick per task.
- "Is the think-tag text the model's REAL reasoning?" - Treat it as a useful scratchpad, not a court transcript: it explores, backtracks, and can be wrong on the way to right. Only what follows the closing tag is the answer.
- "My reasoning answer got cut off mid-thought" - Context, not the model: a deep run can fill the 16K window from Session 2. Raise num_ctx or shrink the problem - and recall the 30k self-stop story.
- "Is this the same as the hosted thinking models?" - Same idea, two differences: you see every word of the deliberation locally, and it is one set of weights with two gears - no second model, no second download.
- "Does the toggle prompt work on hermes3 or other models?" - It is trained-in behavior published with DeepHermes-3 and carried into Hermes 4. Elsewhere you get imitation think tags at best - do not expect the AIME jump on models that were not trained for it.
