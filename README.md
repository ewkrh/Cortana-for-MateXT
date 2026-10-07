# Cortana for Mate XT

A personal AI phone assistant prototype for **Huawei Mate XT running HarmonyOS 4.2**.

The long-term vision is:

> **Siri + ChatGPT Voice + Computer Use**

The project is intentionally being built from the bottom up. The current milestone is **not** a full AI assistant. The first objective is to prove that a third-party Android APK can reliably observe and control the Mate XT UI.

## Current milestone: Cortana Lab v0.1

Cortana Lab is a developer-facing capability-validation app.

It should prove that the Mate XT can:

- run our APK reliably;
- enable and keep an `AccessibilityService` active;
- identify the foreground app/window;
- read the accessibility UI hierarchy;
- extract visible text and useful node metadata;
- click UI nodes;
- perform gestures such as swipe/scroll;
- trigger Back and Home;
- capture the current screen;
- expose useful diagnostics when something fails.

Real-device behavior on **Huawei Mate XT / HarmonyOS 4.2** is authoritative.

## Technical direction

Initial stack:

- Kotlin
- Native Android
- Android SDK
- AccessibilityService
- MediaProjection
- Foreground Service where required
- ADB real-device debugging

Do not introduce Huawei-specific APIs unless standard Android APIs prove insufficient on the Mate XT.

## Not in scope for v0.1

Do **not** implement yet:

- LLM/API integration
- realtime voice
- speech recognition or TTS
- wake-word detection
- long-term memory
- autonomous multi-step agents
- computer vision/OCR
- cloud backend
- payment or sensitive-operation automation
- polished visual design

## Repository map

- `AGENTS.md` — operating instructions for Codex/AI coding agents
- `docs/PRODUCT.md` — product definition and user experience goals
- `docs/ARCHITECTURE.md` — technical architecture and module boundaries
- `docs/ROADMAP.md` — milestone sequence and status
- `docs/DECISIONS.md` — durable technical decisions
- `docs/DEVLOG.md` — meaningful implementation progress and device findings
- `docs/SECURITY.md` — safety boundaries for phone control
- `docs/HARMONYOS_TEST_MATRIX.md` — Mate XT / HarmonyOS compatibility observations
- `plans/active/` — active execution plans
- `plans/completed/` — completed execution plans

## First development path

```text
Mac
  ↓
Android Studio
  ↓
ADB
  ↓
Huawei Mate XT
  ↓
Cortana Lab APK
  ↓
AccessibilityService
  ↓
UI Tree
  ↓
Tap / Swipe / Back
  ↓
Screenshot
```

The project should not move to AI/voice work until this chain is stable on the real device.

## Development discipline

Before substantial changes, read:

1. `AGENTS.md`
2. `docs/PRODUCT.md`
3. `docs/ARCHITECTURE.md`
4. `docs/ROADMAP.md`
5. `docs/DECISIONS.md`
6. the relevant active plan under `plans/active/`

If a behavior cannot be verified without the physical Mate XT, mark it:

> **REQUIRES REAL DEVICE VERIFICATION**

Do not claim device compatibility based only on an emulator or standard Android device.
