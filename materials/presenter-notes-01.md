# Presenter notes - Session 1 · Meet Hermes: the AI that answers to you

Student-facing page: courses/01-meet-hermes.html. These notes are for the presenter only.

## Preflight (do the night before, not the morning)

- [ ] Ollama installed on presenter machine, `ollama run hermes3:8b` pulled AND tested (the 4.7GB download must never happen on venue wifi)
- [ ] Nous Chat account logged in, one warm-up conversation already in history
- [ ] OpenRouter playground open in a second tab as the fallback hosted route (Hermes 3 405B free tier)
- [ ] Projector zoom tested (toolbar button, 125%)
- [ ] Wifi-off test rehearsed once: know your machine's wifi toggle without fumbling
- [ ] Know your RAM number and have Activity Monitor open (someone will ask about memory)
- [ ] If org delivery: check install policy beforehand; if machines are locked down, Demo 2 becomes presenter-screen-only and the homework says "do it on your personal machine"

## Run of show

| Min | Beat | Notes |
|-----|------|-------|
| 0-3 | Welcome + the premise | "By the end of the hour an AI runs on YOUR laptop with wifi off." Say that sentence first - it is the hook for the whole course |
| 3-10 | Part 1: what Hermes is | Timeline SVG on projector zoom; family table briefly - the RAM rule of thumb is the take-home, not the specs |
| 10-16 | Part 2: neutral alignment | The "Red" negotiation prompt teaser; do NOT debate alignment politics here - the responsibility card covers the balance, D5 exists for the deep argument |
| 16-18 | Part 3: the running project | Ladder SVG; one sentence per rung, momentum matters more than detail |
| 18-26 | Demo 1: hosted first contact | Everyone on Nous Chat; run Red 3 rounds; the steering test (risk manager vs founder) with a volunteer's real question |
| 26-38 | Demo 2: first local run | The one-liner together; the wifi-off moment IS the session - milk the silence when it answers offline |
| 38-40 | ollama list + "that file is yours" | Point at the model on disk; land the ownership point |
| 40-45 | Q&A + homework pointer | Bring-your-RAM-number assignment for Session 2 |

## Never-cut beats

1. The wifi-off answer (the emotional core of the session - if time collapses, cut everything else first)
2. The "two Hermeses" warning (model vs agent) - saves endless confusion in week 8
3. The responsibility card - neutral alignment ships with ownership of safety, say it plainly once
4. The RAM rule of thumb - it is the bridge to Session 2

## Cuts if long

- Demo 1 steps 4-5 (steering test) - it reappears in Session 3 anyway
- Part 1 self-study cards (they are marked self-study for a reason - never present them)
- The Nous Research history card - one sentence and move on

## Q&A landmines

- "Is this as good as ChatGPT?" - Honest answer: hosted frontier models are stronger at the top end; the 8B you just ran is not the ceiling - Session 2 upgrades you, and the point is ownership + privacy + steerability, not beating a datacenter.
- "Is an uncensored model dangerous / legal?" - Reframe: neutral alignment means fewer refusals on legitimate work, not lawlessness; laws and your org's policy still apply to outputs; you write the guardrails (Session 3), and D5 treats the debate seriously.
- "Why is my download slow / laptop hot?" - First run downloads ~4.7GB and inference uses real compute; both are normal; smaller models exist; Session 2 sizes properly.
- "Can it access my files?" - No; it only sees what you paste. Tool access is opt-in and YOU build it in Session 6, with allowlists.
