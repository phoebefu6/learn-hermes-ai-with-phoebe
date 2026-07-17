# Presenter notes - Session 8 · Go autonomous: Hermes Agent

Student-facing page: courses/08-hermes-agent.html. These notes are for the presenter only.

## Preflight (do the night before, not the morning)

- [ ] Hermes Agent desktop installed AND authenticated on the demo machine - run `hermes setup` fully the night before (Custom Endpoint → http://localhost:11434/v1 → hermes4-14b-16k) so class time is a re-walk, not a first walk
- [ ] Seed `~/hermes-course/notes` with 12 real markdown files - the first-delegation prompt names that exact folder and count
- [ ] Rehearse the full first delegation on the demo machine - a 14B brain on a 16K window is SLOW and thinks in short strides; know the real duration and where it usually stumbles so you can narrate instead of sweat
- [ ] Rehearse Demo 2 too: skill save, the Friday-4pm schedule, and the memory inspection - know what its memory dump looks like before showing it on a projector
- [ ] Docker installed and running - house rule 1 says sandbox first, and the demo machine should practice what the slide preaches
- [ ] Ollama serving and `hermes4-14b-16k` responding (`ollama list`); the troubleshooting card's three failures (endpoint, model name, context stall) rehearsed
- [ ] Clipboard/snippets ready: the inventory prompt, the first-delegation prompt, the skill-teaching prompt
- [ ] Fast-moving product: released Feb 25, 2026 and moving weekly - re-verify that morning the install URL, the `hermes setup` flow, the Custom Endpoint wording, and the Portal free-tier claim before repeating any of them out loud

## Run of show

| Min | Beat | Notes |
|-----|------|-------|
| 0-3 | Welcome + the last upgrade | "Seven sessions ago you were warned: two things share the name Hermes. Tonight you meet the second one." The shape changes: goal in, result back |
| 3-9 | Part 1: the other Hermes | Architecture SVG on projector zoom: your model is the brain, the agent is everything around it. Then the honest limits card - 14B tops out at 40,960 context, agents want 64K+; set expectations BEFORE the demo, not after it disappoints |
| 9-15 | Part 2: skills, memory, channels | The self-improving loop SVG: does a task, writes a skill, reuses it - "a chatbot resets to zero every morning; an agent appreciates". Channels in one breath: one identity, many doors |
| 15-20 | Part 3: the safety conversation | The five house rules table, one by one, plus the sixth mindset: memory is sensitive data. This is the responsible-adult card of the whole course - do not rush it |
| 20-34 | Demo 1: the graduation | Setup re-walk (it worked last night, say so), inventory prompt ("it is a newborn"), then the first delegation - and the most important beat: WATCH it work. Plan, file reads, draft, result. Debrief the seams honestly |
| 34-40 | Demo 2: teach it one skill | Skill-teaching prompt, Friday-4pm schedule, then read its memory slowly on screen - house rule six in practice. Channel connection is homework, not live |
| 40-45 | Q&A + graduation checklist | Read the 8-session checklist aloud, S2 through S8. "Nobody rents this to you. You built it, you steer it, you own it" - close on that line |

## Never-cut beats

1. Watching the agent work through the first delegation end to end - house rule 4 made live; the plan-then-act rhythm is this session's wifi-off moment
2. Model vs agent - Session 1's "two Hermeses" warning finally pays off; if a headline says "Hermes did X autonomously" they must know which one it means
3. The five house rules - especially sandbox first and confirm destructive/outward actions; this is the course's whole safety posture compressed
4. The memory inspection in Demo 2 - seeing their own file contents inside its memory store turns "memory is sensitive data" from a slide into a chill
5. The graduation checklist - eight sessions of work named and checked; it is the emotional close of the course

## Cuts if long

- Demo 2 step 4 (the messaging channel) - already optional and after-class by design
- Part 2's channels card - compress to one sentence and the SVG; the inventory prompt shows the real list anyway
- The ecosystem examples (self-evolution, autonovel) - one sentence of "proof of range", not a tour
- Part 2 and Part 3 self-study cards (boundaries, why-this-is-calm) - never present them

## Q&A landmines

- "Will scheduled jobs run while my laptop is asleep or closed?" - No magic: the agent and Ollama must be running for the cron to fire. A always-on machine or small server is the real answer for standing jobs; for now, Friday 4pm with the lid open.
- "Does my data go to Nous Research?" - On tonight's path - local model, local backend - the work stays on your machine; that has been the course thesis since Session 1. Choose Portal for hosted brains and your prompts go to hosted models: a deliberate trade, not a default.
- "Why is mine so much dumber than the demos online?" - Those run frontier hosted brains; yours is a 14B on a modest window. Fine for short, well-scoped tasks; the upgrade paths (bigger local model, or Portal) keep tonight's architecture unchanged.
- "Can I point it at ChatGPT or Claude instead?" - It is model-agnostic by design - any capable OpenAI-compatible endpoint can be the brain. The course path is local first because you own it; nothing you built tonight breaks if you swap brains later.
- "What if it deletes or overwrites something?" - That is why the first delegation says "do not modify or delete any existing file" and why house rules 1 and 5 exist: sandbox, and confirm destructive actions. If it happened, your allowlist was too wide - narrow it, then check what its memory retained.
