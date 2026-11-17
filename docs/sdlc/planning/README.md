# Planning

> Maintained by QuorQ AI SDLC. Text between `sdlc:auto` markers is regenerated; anything outside them is yours and is kept.

<!-- sdlc:auto:start narrative -->
### EPIC-001 · approved · source: planning:EPIC-001

Core purpose of the product: a basic-arithmetic calculator performing add, subtract, multiply, divide, percentage and clear operations on decimal numbers, with a sign toggle.

Explicitly limited to everyday arithmetic -- there is no scientific functionality.

**Related:** US-001, US-002, US-003, US-004

### EPIC-002 · approved · source: planning:EPIC-002

Users can drive the calculator using both on-screen buttons and the keyboard, and can clear the current entry or the whole calculation.

Confirmed open assumption: the calculator supports keyboard and on-screen button input plus a clear function.

**Related:** US-005, US-006, US-007

### EPIC-003 · approved · source: planning:EPIC-003

The calculator handles invalid operations such as divide-by-zero gracefully, surfacing a clear message instead of crashing, and recovers to a usable state.

Reflects the confirmed open assumption on graceful error handling.

**Related:** US-008

### EPIC-004 · approved · source: planning:EPIC-004

The product is delivered as a single responsive web application with a basic project structure; the calculator screen is the main (dashboard) view, open to anyone with no accounts and no payments, working on desktop and mobile browsers.

Open assumptions: responsive web app (not native mobile), open to anyone with no accounts, free with no payments. The app design phase must use the Magic UI MCP integration for interactive preview screens, and generated code in those screens must use the Magic UI integration.

**Related:** US-009, US-010, US-011

### EPIC-005 · approved · source: planning:EPIC-005

Basic documentation for the calculator, plus an explicit record of the scope boundaries chosen for this Lightweight MVP.

Several baseline capabilities at this delivery scope do not apply to a public, account-free, client-side calculator and are recorded as assumptions rather than built: Authentication is not applicable (no sign-up or accounts); no persistent calculation history or user data is stored, so Database Integration and CRUD screens have no user-facing data to manage; there are no payments.

**Related:** US-012, US-013
<!-- sdlc:auto:end narrative -->
