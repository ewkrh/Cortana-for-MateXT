# Architecture

## Current architecture

Cortana Lab v0.1 is split into three logical boundaries:

```text
Debug UI
  │
  ├── Perception
  │     ├── Accessibility UI Tree
  │     └── Screenshot
  │
  └── Actions
        ├── Node click
        ├── Coordinate/gesture tap if needed
        ├── Swipe / scroll
        ├── Back
        └── Home
```

## Perception

### Accessibility

Use `AccessibilityService` as the primary structured perception channel.

Normalize `AccessibilityNodeInfo` into an internal model so future AI code does not depend directly on Android framework objects.

Conceptual model:

```text
UiNode
- id
- className
- text
- contentDescription
- viewId
- bounds
- clickable
- scrollable
- editable
- enabled
- focused
- children
```

Keep this model minimal until real-device testing shows additional fields are necessary.

### Screenshot

Use `MediaProjection` for screen capture.

For v0.1, screenshots are for capability validation only.

No OCR, no vision model, no upload.

## Actions

Provide a clean internal action boundary.

Conceptual operations:

```text
readScreen()
tapNode(nodeId)
tapCoordinate(x, y)
swipe(startX, startY, endX, endY, duration)
scrollDown()
scrollUp()
goBack()
goHome()
takeScreenshot()
```

Prefer semantic node actions when possible.

Use gesture or coordinate actions only when necessary.

## Debug UI

The first UI is an engineering console, not a consumer interface.

It should make failures visible and answer:

- What app/window is active?
- What nodes are visible?
- Which nodes are clickable/editable/scrollable?
- Did an action succeed?
- Did screenshot capture succeed?
- What failed on HarmonyOS?

## Future architecture

Later versions may add:

```text
Voice / Text Agent
      ↓
LLM reasoning
      ↓
Tool calls
      ↓
Cortana Tool Layer
      ↓
Perception + Actions
```

Do not implement this future layer during v0.1.
