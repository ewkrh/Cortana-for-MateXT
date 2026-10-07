# Technical Decisions

## Decision 001 — Native Android first

**Decision:** Use Kotlin + native Android APIs for the first implementation.

**Reason:** AccessibilityService, MediaProjection, foreground services, overlays and ADB debugging require close Android integration.

**Status:** accepted.

---

## Decision 002 — Accessibility UI Tree before vision

**Decision:** Use the accessibility tree as the primary perception channel.

**Reason:** It is structured, relatively cheap to process and exposes semantic UI information when available.

Screenshots are a fallback/complement, not the primary v0.1 interpretation mechanism.

**Status:** accepted.

---

## Decision 003 — Real Mate XT is authoritative

**Decision:** Treat Huawei Mate XT / HarmonyOS 4.2 behavior as the source of truth.

**Reason:** Emulator/AOSP behavior may not match Huawei permission, background-service or accessibility behavior.

**Status:** accepted.

---

## Decision 004 — Build a lab before an assistant

**Decision:** The first app is a developer-facing Cortana Lab, not a polished assistant UI.

**Reason:** The highest-risk unknown is device-control reliability, not presentation.

**Status:** accepted.
