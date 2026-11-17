# Planning

> Maintained by QuorQ AI SDLC. Text between `sdlc:auto` markers is regenerated; anything outside them is yours and is kept.

<!-- sdlc:auto:start narrative -->
### EPIC-001 · approved · source: planning:EPIC-001

Core purpose of the product: a basic-arithmetic calculator supporting add, subtract, multiply, divide, percentage, clear and sign toggle on decimal numbers.

Explicitly limited to everyday arithmetic — no scientific functionality. Stories: US-001 (four basic operations), US-002 (percentage), US-003 (decimal entry), US-004 (sign toggle).

**Related:** US-001, US-002, US-003, US-004

### EPIC-002 · approved · source: planning:EPIC-002

Users can drive the calculator via on-screen buttons and keyboard, and can clear the current entry or whole calculation.

These behaviours are confirmed open assumptions: support for keyboard input, on-screen button input, and a clear function. Stories: US-005 (on-screen buttons), US-006 (keyboard), US-007 (clear).

**Related:** US-005, US-006, US-007

### EPIC-003 · approved · source: planning:EPIC-003

The calculator handles invalid operations such as divide-by-zero gracefully, surfacing a clear message instead of crashing, and recovers to a usable state.

Reflects the confirmed open assumption on graceful error handling. Story: US-008 (handle divide by zero gracefully).

**Related:** US-008

### EPIC-004 · approved · source: planning:EPIC-004

The product is delivered as a single responsive web application with a basic project structure; the calculator screen is the main (dashboard) view, open to anyone with no sign-up or accounts, free with no payments, and works on desktop and mobile browsers.

Open assumptions: responsive web app (not native mobile), no accounts required, free with no payments. The app design phase must use Magic UI MCP integration for interactive preview screens, and generated code in those preview screens must use the Magic UI integration. Stories: US-009 (open without signing up), US-010 (desktop/mobile responsiveness), US-011 (Magic UI design preview screens).

**Related:** US-009, US-010, US-011

### EPIC-005 · approved · source: planning:EPIC-005

Basic documentation for the calculator plus an explicit record of the scope boundaries chosen for this Lightweight MVP.

Several baseline capabilities at this scope do not apply to a public, account-free, client-side calculator and are recorded as assumptions rather than built: Authentication is not applicable (no sign-up/accounts); no persistent calculation history or user data is stored, so Database Integration and CRUD screens have no user-facing data to manage; there are no payments. Stories: US-012 (basic usage documentation), US-013 (record non-applicable baseline capabilities as scope assumptions).

**Related:** US-012, US-013

### SPRINT-1 · approved · source: planning:Sprint 1

Sprint 1 stands up the core calculator engine, on-screen input, sign toggle, clear, the Magic UI design integration, and the no-signup landing experience.

Plan v1, approved. Capacity: 20 points. Goal: Stand up the core calculator engine, on-screen input, sign toggle, clear, the Magic UI design integration, and the no-signup landing experience. Items assigned per goal scope: US-001 Perform the four basic arithmetic operations (5 pts, frontend-agent), US-004 Toggle the sign of a number (2 pts, frontend-agent), US-005 Use on-screen buttons (5 pts, frontend-agent), US-007 Clear the current entry or calculation (2 pts, frontend-agent), US-009 Open the calculator without signing up (2 pts, devops-agent), US-011 Design preview screens with the Magic UI integration (3 pts, frontend-agent). Sum of story points assigned: 19 against a capacity of 20.

**Related:** EPIC-001, EPIC-002, EPIC-004, US-001, US-004, US-005, US-007, US-009, US-011

### SPRINT-2 · approved · source: planning:Sprint 2

Sprint 2 adds percentage, decimals, keyboard input, divide-by-zero handling, responsive layout polish, and ships documentation and scope-boundary notes.

Plan v1, approved. Capacity: 20 points. Goal: Add percentage, decimals, keyboard input, divide-by-zero handling, responsive layout polish, and ship documentation and scope-boundary notes. Items assigned per goal scope: US-002 Calculate a percentage (3 pts, frontend-agent), US-003 Enter decimal numbers (3 pts, frontend-agent), US-006 Use the keyboard (3 pts, frontend-agent), US-008 Handle divide by zero gracefully (3 pts, frontend-agent), US-010 Use the calculator on desktop and mobile browsers (5 pts, frontend-agent), US-012 Provide basic usage documentation (2 pts, qa-agent), US-013 Record non-applicable baseline capabilities as scope assumptions (1 pt, qa-agent). Sum of story points assigned: 20, matching the capacity of 20.

**Related:** EPIC-001, EPIC-003, EPIC-004, EPIC-005, US-002, US-003, US-006, US-008, US-010, US-012, US-013
<!-- sdlc:auto:end narrative -->
