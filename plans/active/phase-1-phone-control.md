# Phase 1 — Phone Control Execution Plan

## Goal

Prove that a third-party Android APK can reliably observe and operate the UI on Huawei Mate XT / HarmonyOS 4.2.

The deliverable is **Cortana Lab v0.1**.

## Non-goals

Do not implement:

- AI/LLM integration;
- voice;
- wake word;
- memory;
- autonomous agents;
- OCR/vision;
- backend services;
- polished UI.

## Workstream 1 — Android project initialization

- Create a minimal Kotlin/native Android app.
- Keep dependencies small.
- Confirm Gradle build succeeds locally.
- Define an application ID suitable for development.
- Document min/target SDK decisions in `docs/DECISIONS.md`.

Acceptance:

- debug APK builds successfully.

## Workstream 2 — ADB and real-device loop

Prepare commands/workflow for:

- `adb devices`;
- installing/reinstalling debug APK;
- launching the app;
- reading filtered Logcat;
- checking accessibility state when practical.

Acceptance:

- Mate XT appears through ADB;
- debug APK installs and launches.

**REQUIRES REAL DEVICE VERIFICATION**

## Workstream 3 — AccessibilityService

Implement the smallest working service first.

Capture:

- foreground package;
- active window/root;
- class name;
- text;
- contentDescription;
- view/resource ID where available;
- bounds;
- clickable;
- scrollable;
- editable;
- enabled;
- focused;
- child relationships.

Acceptance:

- service can be enabled;
- active UI tree can be traversed;
- failures are visible in logs.

**REQUIRES REAL DEVICE VERIFICATION**

## Workstream 4 — UI normalization

Create a small internal `UiNode` model independent of `AccessibilityNodeInfo`.

Avoid speculative semantic layers.

Acceptance:

- UI tree can be converted into stable debug-friendly data.

## Workstream 5 — Screen Inspector

Create a developer UI showing:

- accessibility enabled/disabled state;
- current app/package;
- window/root state;
- visible nodes;
- key node properties;
- refresh/read action;
- action result/error.

Acceptance:

- developer can see what Cortana can actually observe.

## Workstream 6 — Actions

Implement clean action interfaces for:

- `tapNode(nodeId)`;
- `tapCoordinate(x, y)` if needed;
- `swipe(...)`;
- `scrollDown()`;
- `scrollUp()`;
- `goBack()`;
- `goHome()`.

Prefer node actions over coordinate gestures.

Acceptance:

- at least one real UI node can be clicked;
- swipe works;
- Back works;
- Home works.

**REQUIRES REAL DEVICE VERIFICATION**

## Workstream 7 — Screenshot

Implement MediaProjection permission flow and capture.

For v0.1:

- capture only;
- display/save locally as useful for debugging;
- no OCR;
- no upload;
- no vision model.

Acceptance:

- screenshot succeeds on Mate XT.

**REQUIRES REAL DEVICE VERIFICATION**

## Workstream 8 — Logging and diagnostics

Use concise Logcat tags.

Log:

- service lifecycle;
- active package/window changes when useful;
- requested actions;
- action result/failure;
- screenshot result/failure;
- exceptional HarmonyOS behavior.

Avoid continuous noisy full-tree dumping unless explicitly triggered.

## Workstream 9 — HarmonyOS compatibility recording

Update `docs/HARMONYOS_TEST_MATRIX.md` with actual findings.

Record any Huawei-specific steps such as:

- extra permission screens;
- background execution restrictions;
- battery optimization behavior;
- incomplete accessibility trees;
- overlay/service limitations.

Do not guess.

## Acceptance criteria

Phase 1 is complete only when all are verified on the real Mate XT:

1. APK installs.
2. App launches.
3. AccessibilityService can be enabled.
4. Foreground package is identified.
5. UI hierarchy is readable.
6. Visible text is extractable.
7. Clickable elements are detectable.
8. Editable elements are detectable.
9. Scrollable elements are detectable.
10. At least one UI element can be clicked programmatically.
11. Swipe works.
12. Back works.
13. Home works.
14. Screenshot works.
15. Useful failures appear in logs.
16. App survives normal switching among several apps.
17. HarmonyOS-specific limitations are documented.

## Completion rule

Do not move this plan to `plans/completed/` until the real-device acceptance criteria pass.
