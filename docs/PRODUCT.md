# Product Definition

## Product

**Cortana for Mate XT** is a personal AI phone assistant intended to eventually combine:

- natural conversation;
- awareness of the current phone screen;
- contextual assistance;
- phone UI control;
- AI reasoning;
- multi-step task execution.

A useful shorthand is:

> **Siri + ChatGPT Voice + Computer Use**

## Current product stage

The current product is **not yet an AI assistant**.

The first deliverable is **Cortana Lab v0.1**, an engineering validation app.

Its purpose is to answer:

> Can a third-party Android APK on Huawei Mate XT / HarmonyOS 4.2 reliably observe and operate the current phone UI?

## Cortana Lab v0.1

The debug app should expose:

- accessibility service state;
- foreground package/window information;
- visible accessibility nodes;
- node text, class, content description, IDs and bounds;
- clickable/scrollable/editable flags;
- refresh/read-screen control;
- node click test;
- swipe/scroll test;
- Back/Home;
- screenshot test;
- clear errors and diagnostic logs.

Appearance is secondary.

## Success condition

v0.1 is successful only when the above capabilities are demonstrated on the real Mate XT.

## Later product stages

After the device-control layer is stable:

1. Tool layer
2. Text AI agent
3. Realtime voice
4. Autonomous article reading
5. Multi-step agent
6. Memory and personalization

These are intentionally deferred.
