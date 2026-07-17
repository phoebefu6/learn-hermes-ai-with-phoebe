# Presenter notes - Session 7 · Hermes as a service: Portal, OpenRouter, licenses

Student-facing page: courses/07-hermes-as-a-service.html. These notes are for the presenter only.

## Preflight (morning-of items are marked - pricing goes stale overnight)

- [ ] MORNING OF: hand-verify Nous Portal pricing + tiers in a normal browser (portal.nousresearch.com is bot-gated - scripts cannot check this for you); note any changes vs the page's numbers out loud in session
- [ ] MORNING OF: confirm the OpenRouter Hermes 3 405B `:free` variant is still listed (openrouter.ai/nousresearch) - it is the spine of Demo 1 backend 2; if gone, fall back to the cheapest 70B listing and say so
- [ ] OpenRouter account + API key created, key loaded in the demo shell env
- [ ] Nous Portal account + key if possible; if not, backend 3 becomes "here is what would change" on slides - rehearse that version
- [ ] Session 5 extract.py runs against localhost baseline on the presenter machine
- [ ] The two-line swap rehearsed for all three backends - fumbling base_urls live kills the "it's trivial" message
- [ ] Current OpenRouter prices for Hermes 4 70B and 405B written on a sticky note for the cost-math step
- [ ] Projector zoom tested (toolbar button, 125%); hub SVG legible from the back row
- [ ] If org delivery: check whether learner machines can reach openrouter.ai (some corp networks block it); if blocked, Demo 1 is presenter-screen-only

## Run of show

| Min | Beat | Notes |
|-----|------|-------|
| 0-3 | Welcome + the premise | "Everything you built already works against every provider - you swap one base_url." That sentence is the session; say it first |
| 3-11 | Part 1: the provider menu | Hub SVG on zoom; Portal (endpoint, free eval tier, Tool Gateway) then OpenRouter (the :free trick gets an audible reaction - let it); Nebius/Lambda is self-study, one sentence |
| 11-17 | Part 2: licenses | The license table row by row; the 700M MAU clause gets a laugh - use it, then land the serious version: "Apache bucket for products, and you never have the conversation" |
| 17-21 | Part 3: the decision | Decision table fast, then the two-lane SVG; "route per workload, not per religion" is the take-home |
| 21-31 | Demo 1: three backends | Localhost first (baseline), then the two-line swap to OpenRouter :free - the 405B answering for $0.00 is the wow beat; Portal third if keyed. Then the cost math ON SCREEN with today's sticky-note prices, not the page's |
| 31-37 | Demo 2: production tiers | Worksheet with a volunteer's three real workloads; privacy vetoes first, then "test your 14B before paying anyone" |
| 37-40 | Bridge to the finale | Assistant picks its default backend today; Session 8 hands it autonomy - Hermes Agent, skills, memory, a channel |
| 40-45 | Q&A + homework pointer | Homework: three-backend run + hand-check Portal pricing themselves + read the Llama 3 license once |

## Never-cut beats

1. The two-line swap performed live at least once - seeing base_url change and the same script answer is the entire architecture lesson
2. The cost math with real, morning-verified numbers - decision-makers in the room came for exactly this slide
3. "Sensitive data stays local, full stop" - privacy as the first gate of the decision table, said plainly once
4. The license one-liner: Apache bucket (4.3 36B, 14B) for products; Llama 3 license models are fine to use but carry Meta's conditions

## Cuts if long

- Demo 1 backend 3 (Portal) - describe the two lines verbally, keep localhost + OpenRouter live
- The Nebius/Lambda hosting card - it is self-study, never present it
- The privacy-tiers self-study table - compress to the "classify data BEFORE picking a backend" sentence
- Demo 2 shrinks from three workloads to one done well; assign the other two as homework

## Q&A landmines

- "Are these prices right?" - The page's numbers are anchors dated mid-2026 with a verify-live flag; quote what YOU checked this morning, and teach the habit: marketplace prices move monthly, Portal pricing must be checked in a browser because the page is bot-gated.
- "Why is a 405B free on OpenRouter - what's the catch?" - Rate limits and best-effort capacity; it is a marketing/community tier, great for learning, wrong for anything a client depends on. That is exactly the free-tier row of the decision table.
- "Is my data safe with the free tier?" - No stronger promise than any hosted tier: router ToS plus underlying host ToS apply. Free changes the price, not the privacy classification - sensitive data still stays local.
- "Can we use the Llama-licensed models commercially or not?" - Yes for most commercial use; the 700M MAU clause bites almost nobody, but naming/attribution requirements are real, and if you want zero conversation with legal, ship the Apache bucket.
- "Why not self-host the 70B on a cloud GPU instead?" - Legit third lane for teams: open weights mean any GPU box can serve it (vLLM even has a named hermes tool parser); it trades API convenience for ops burden - deep-dive D3 covers serving properly.
- "Which one should MY company pick?" - Refuse the general answer; run their actual workload through the Demo 2 worksheet in front of everyone. The framework is the deliverable, not a vendor pick.
