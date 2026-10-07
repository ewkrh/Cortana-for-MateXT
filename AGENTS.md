# Cortana Mobile Agent Instructions

## Project purpose

Build a personal AI assistant for **Huawei Mate XT running HarmonyOS 4.2**.

Long-term capabilities may include natural conversation, screen understanding, phone control, contextual assistance, and autonomous tasks.

## Current priority

The current milestone is **Cortana Lab v0.1**.

The priority is to validate, on the real Huawei Mate XT:

1. Android project initialization
2. AccessibilityService
3. UI hierarchy reading
4. node inspection
5. tap
6. swipe/scroll
7. Back/Home
8. screenshot capture
9. diagnostic UI and logging
10. HarmonyOS 4.2 compatibility

Do not implement AI, voice, memory, or autonomous agents unless the active execution plan explicitly requires them.

## Development principles

- Keep v0.1 minimal.
- Prefer native Android APIs.
- Kotlin is the primary language.
- Test primarily on the real Huawei Mate XT.
- HarmonyOS behavior must be verified on real hardware.
- Avoid premature architecture complexity.
- Significant technical decisions must be recorded.
- Meaningful development progress and device findings must be logged.
- Do not claim a feature works on Mate XT unless it has actually been verified there.

## Read before substantial changes

Read:

- `README.md`
- `docs/PRODUCT.md`
- `docs/ARCHITECTURE.md`
- `docs/ROADMAP.md`
- `docs/DECISIONS.md`
- relevant files under `plans/active/`

## Planning rule

Complex tasks must have an execution plan under:

`plans/active/`

When completed, move the plan to:

`plans/completed/`

## Scope guardrail

For Cortana Lab v0.1, do not add:

- LLM integration
- OpenAI API integration
- voice/realtime audio
- wake word
- long-term memory
- autonomous agent loops
- OCR/computer vision
- cloud backend
- payments or sensitive transaction automation
- visual polish unrelated to debugging

## Real-device rule

If behavior requires the physical Mate XT and has not been tested there, write:

**REQUIRES REAL DEVICE VERIFICATION**

The emulator is not authoritative for HarmonyOS compatibility.
