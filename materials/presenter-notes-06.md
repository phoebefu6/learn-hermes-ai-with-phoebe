# Presenter notes - Session 6 · Tool calling: give it hands

Student-facing page: courses/06-tool-calling.html. These notes are for the presenter only.

## Preflight (do the night before, not the morning)

- [ ] Test the weather tool script against local Ollama that morning - run tools.py plus the full 20-line loop end to end and watch a complete tool_call → execute → tool_response → answer cycle succeed
- [ ] Session 5 venv activates cleanly with the `openai` package; `ollama serve` up; `hermes4-14b-16k` responds
- [ ] Create `~/hermes-notes` on the demo machine with one real small text file (a meeting note beats lorem ipsum for the summarize step)
- [ ] All three code blocks (tools.py, SCHEMAS, the loop) ready to PASTE, never typed live - and pre-shared with builders so they paste along
- [ ] Rehearse all three Demo 2 breaks: the AMD stock question, the ../../.ssh/id_rsa escape, the range(2) cap - know what YOUR model does with each, it varies run to run
- [ ] Rehearse the wifi-off run (Demo 1 step 6) - know your machine's wifi toggle without fumbling, same drill as Session 1
- [ ] Fast-moving product: re-verify that morning that your installed Ollama version still supports `tools=` on the OpenAI-compatible endpoint with your custom model - tool support has shifted between Ollama releases, and this single fact carries both demos

## Run of show

| Min | Beat | Notes |
|-----|------|-------|
| 0-3 | Welcome + from talking to doing | "A language model plus a loop that executes its requests is the entire recipe for an agent." Today they build the loop by hand |
| 3-9 | Part 1: the format | Five-step loop SVG on projector zoom; walk the raw exchange (tools, tool_call, tool_response) once slowly. The vLLM parser named "hermes" is the credibility beat - when infrastructure names a parser after your format, you set the standard |
| 9-14 | Part 2: two ways in | The raw-vs-tools= table; house position: build with tools=, be the person who can read the raw tags. Do not present the canon-repo self-study card - one pointer sentence max |
| 14-18 | Part 3: you own the hands | The safety trio: allowlist, validate arguments, cap iterations - plus the destructive-action rule. "The model proposes, your loop disposes" verbatim |
| 18-32 | Demo 1: the 20-line agent loop | Paste-along: tools + allowlist, schemas, loop. Run the weather question, then the note question, then the no-tool question (it just answers). Finish with wifi OFF and run it again - whole agent offline |
| 32-38 | Demo 2: break it on purpose | Three failures: no-tool-fits improvisation, the allowlist escape caught by the path check, the range(2) early stop. Each failure is a lesson, name them |
| 38-45 | Q&A + homework pointer | One real read-only tool on THEIR notes; run the escape attempt against their own validation before adding a second tool |

## Never-cut beats

1. The wifi-off agent run - local model, local tools, local files; this session's wifi-off moment is literal, and it is the course thesis made executable
2. The escape attempt (../../.ssh/id_rsa) caught by the path check - "the model was never the security layer; your validation was" must be SEEN, not stated
3. "The model never executes anything - it proposes, your loop disposes" - the sentence that reorganizes their threat model before Session 8
4. The no-tool-fits fix - "if no available tool can answer, say so; never guess" into the constitution: the cheapest reliability upgrade in the course, say it as such

## Cuts if long

- Part 1 card 2 (why an open standard mattered) - compress to the vLLM parser sentence alone
- Demo 1 step 5 (the OTHER-tool and no-tool questions) - keep the no-tool question, drop the second tool question
- Demo 2 step 3 (the range(2) cap experiment) - state the seatbelt lesson verbally instead
- Part 2 self-study card (Hermes-Function-Calling repo) - homework stretch, never presented

## Q&A landmines

- "Can it call real APIs and browse the internet?" - Yes, any Python function can be a tool - today's weather stub is canned so the demo never depends on an API. Real network tools mean real consequences: allowlist, validate, and keep the destructive-action rule.
- "What if the model emits malformed JSON arguments?" - It happens; wrap json.loads in a try and return an error message as the tool_response - the model reads it and retries. Session 5's validation muscle applies to inputs too.
- "Is this the same as MCP?" - Same family of ideas: MCP standardizes how tools are discovered and served across apps; today is the wire-level protocol underneath. Learn this and MCP will read as a packaging layer.
- "The model answered without calling my tool" - Working as trained: Hermes also learned when NOT to call. If it should have called, sharpen the tool description in the schema - the description is the menu text it orders from.
- "Is this safe to run on my work laptop?" - Today's build is read-only inside one allowlisted folder with a capped loop - that is the safety model. Adding write, send, or spend tools without the confirmation step is where safe stops; org policy still applies.
