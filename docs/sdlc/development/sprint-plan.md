# Sprint Plan

> Maintained by QuorQ AI SDLC. Text between `sdlc:auto` markers is regenerated; anything outside them is yours and is kept.

<!-- sdlc:auto:start sprints -->
## Sprint 1: Sprint 1

Stand up the core calculator engine, on-screen input, sign toggle, clear, the Magic UI design integration, and the no-signup landing experience.

Capacity: 20 points · Committed: 19

| Key | Type | Title | Points | Role | Depends on |
|---|---|---|---|---|---|
| US-001 | Story | Perform the four basic arithmetic operations | 5 | frontend-agent | — |
| US-004 | Story | Toggle the sign of a number | 2 | frontend-agent | US-001 |
| US-005 | Story | Use on-screen buttons | 5 | frontend-agent | US-001 |
| US-007 | Story | Clear the current entry or calculation | 2 | frontend-agent | US-001 |
| US-009 | Story | Open the calculator without signing up | 2 | devops-agent | US-005 |
| US-011 | Story | Design preview screens with the Magic UI integration | 3 | frontend-agent | — |

## Sprint 2: Sprint 2

Add percentage, decimals, keyboard input, divide-by-zero handling, responsive layout polish, and ship documentation and scope-boundary notes.

Capacity: 20 points · Committed: 20

| Key | Type | Title | Points | Role | Depends on |
|---|---|---|---|---|---|
| US-002 | Story | Calculate a percentage | 3 | frontend-agent | US-001 |
| US-003 | Story | Enter decimal numbers | 3 | frontend-agent | US-001 |
| US-006 | Story | Use the keyboard | 3 | frontend-agent | US-001, US-005 |
| US-008 | Story | Handle divide by zero gracefully | 3 | frontend-agent | US-001 |
| US-010 | Story | Use the calculator on desktop and mobile browsers | 5 | frontend-agent | US-005 |
| US-012 | Story | Provide basic usage documentation | 2 | qa-agent | US-001, US-002, US-003, US-004, US-005, US-006, US-007, US-008, US-010 |
| US-013 | Story | Record non-applicable baseline capabilities as scope assumptions | 1 | qa-agent | — |

## Unscheduled

_Nothing unscheduled._
<!-- sdlc:auto:end sprints -->
