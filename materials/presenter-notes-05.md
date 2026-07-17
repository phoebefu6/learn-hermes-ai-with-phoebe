# Presenter notes - Session 5 · Structured output: JSON that validates

Student-facing page: courses/05-structured-output.html. These notes are for the presenter only.

## Preflight (do the night before, not the morning)

- [ ] Hero model pulled and warm: `ollama run hf.co/bartowski/NousResearch_Hermes-4-14B-GGUF:Q4_K_M` answers a test prompt (never download 9GB on venue wifi)
- [ ] Python env ready: `pip install openai pydantic` in a clean venv; `python -c "import openai, pydantic"` passes
- [ ] extract.py from the page copied locally, run once end to end - confirm it prints a typed Contact object
- [ ] The vandalized-JSON repair prompt tested once - confirm the repaired output passes model_validate_json
- [ ] The {intent, answer, confidence} assistant prompt tested for 2-3 turns - know what its replies look like on screen
- [ ] Terminal font size bumped; projector zoom tested (toolbar button, 125%)
- [ ] Fallback if the 14B misbehaves live: `hermes3:8b` pulled and the model line swap rehearsed
- [ ] If org delivery: confirm learner machines have Python 3.10+; if locked down, demos become presenter-screen-only and homework says "on your personal machine"

## Run of show

| Min | Beat | Notes |
|-----|------|-------|
| 0-3 | Welcome + the premise | "Chat answers are for humans. JSON is for programs. Today your assistant becomes software." Say it in the first 30 seconds - it frames everything |
| 3-8 | Part 1: prose to contract | Pipeline SVG on zoom; the three prose failure modes fast; then the canonical schema prompt SLOWLY - have them read it, stress it is verbatim from the model cards, not folklore |
| 8-11 | Part 1: why it works | One sentence on Pydantic rejection sampling ("trained only on examples that passed the validator") - the full story is the self-study card, do not lecture it |
| 11-18 | Part 2: the validation loop | Loop SVG; Pydantic's four roles (define, dump, validate, error-report); land "the fail path is the design, cap retries at 2" |
| 18-28 | Demo 1: extraction | Type or paste extract.py live; run it; pause on the typed object printing. Then the stress steps: remove phone (null comes back), add second person (single-object schema strains - tees up wrapper models) |
| 28-36 | Demo 2: repair shop + upgrade | Vandalize JSON on screen (trailing comma, unquoted key), watch Hermes fix it; then swap in the {intent, answer, confidence} prompt and chat 3 turns - every reply parseable |
| 36-40 | The project moment | "Your assistant just grew an API." Connect forward: intents today become tool routing in Session 6 |
| 40-45 | Q&A + homework pointer | Homework: build one extractor for their own recurring messy text + keep the JSON prompt on for a day |

## Never-cut beats

1. The canonical schema prompt read verbatim - it is the single copy-paste asset of the session; everything else is commentary
2. The typed object printing in Demo 1 - messy text in, contract out, nothing left the machine; let the moment breathe
3. "Cap retries at 2, then human" - the difference between a demo and software, one sentence
4. Temperature discipline in one line: chat 0.6, extraction 0.2 - it saves half the "it keeps varying" support questions later

## Cuts if long

- Demo 1 step 6 (the stress tests) - point at them as homework instead
- The rejection-sampling self-study card - never present it, one sentence and move on
- The temperature self-study table - compress to the one-liner above
- Demo 2 steps 1-3 (repair shop) squeeze to a 90-second presenter-only show if needed; the assistant upgrade (steps 4-5) is the project spine and stays

## Q&A landmines

- "Why not just use Ollama's format=json flag / structured outputs?" - Fair tool, different lesson: the schema prompt is the trained, provider-portable behavior that works identically on Portal and OpenRouter in Session 7; server-side enforcement is a nice belt to wear WITH these suspenders.
- "What if the model returns extra keys / wrong types anyway?" - That is exactly why validation is in the loop; Pydantic catches it at the door, the error goes back for one repair round, and repeat offenders mean your temperature is too high or field names are ambiguous.
- "Can I trust the confidence number?" - It is self-reported, not calibrated probability. Use it for routing thresholds you tune empirically, never as a statistical guarantee.
- "Does this work on the 8B?" - Yes, the schema prompt is trained into Hermes 3 too; the 14B is just steadier on gnarly nested schemas. Demo the swap if someone insists.
- "Nested objects? Lists? Enums?" - All fine - Pydantic models compose and the schema dump carries it. Show a wrapper model with a list field if time allows, otherwise point at homework.
