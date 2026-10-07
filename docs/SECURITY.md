# Security and Safety Boundaries

Cortana is intended to gain powerful phone-control capabilities. Development should make sensitive operations explicit rather than silently automating them.

## v0.1 boundaries

Cortana Lab v0.1 must not automate:

- payments;
- money transfers;
- account recovery;
- password entry;
- security-setting changes;
- destructive data deletion;
- purchases;
- consent dialogs where the user's intent is ambiguous.

## Engineering principle

Observation and control must remain inspectable.

During development:

- surface the active app/window;
- log requested actions;
- make action failures visible;
- avoid hidden background behavior;
- minimize stored screen content;
- do not upload screenshots unless a later feature explicitly requires it.

## Later agent behavior

Any future autonomous agent should include confirmation boundaries for sensitive actions and should distinguish between:

- read-only actions;
- reversible actions;
- irreversible or financially sensitive actions.

Those policies are outside the current v0.1 implementation scope.
