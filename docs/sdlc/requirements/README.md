# Product Requirements

> Maintained by QuorQ AI SDLC. Text between `sdlc:auto` markers is regenerated; anything outside them is yours and is kept.

<!-- sdlc:auto:start narrative -->
## Summary

### REQ-STACK · approved · source: requirements:technology-stack

Technology stack approved by the product owner for the lightweight, client-side calculator. Most server-side layers are included only to satisfy the platform's standard layering, not because the features need them.

- Backend: FastAPI 0.115 -- all calculation happens in the browser and nothing is stored, so there is no real business logic for a server; FastAPI is kept as a thin shell (health check, serving built files).
- Cloud: AWS -- the app is public on desktop and mobile, so it needs reliable, globally reachable hosting that scales with traffic; no special configuration needed for this free, lightweight app.
- Database: PostgreSQL 16 -- there is no sign-up, no accounts and no persistent calculation history, so there is nothing to store; named only to fill the platform's default layer in case server-side storage is added later.
- Frontend: React 19 -- this is the whole product; the UI lives entirely in the browser (on-screen buttons, keyboard input, decimals, sign toggle, divide-by-zero handling) and must be assembled from Magic UI components previewed via the Magic UI MCP integration.

### REQ-SERVICES · approved · source: requirements:capabilities-in-scope

Platform capability layers nominally in scope for this lightweight delivery, though several do not apply to a stateless, account-free calculator.

Capabilities listed in scope: Authentication, Basic Project Structure, Dashboard, CRUD Screens, REST APIs, Database Integration, Basic Documentation.
- Of these, Authentication, CRUD Screens and Database Integration are platform-default layers only -- the functional requirements and EPIC-005 record them as not applicable because there are no user accounts and no persisted data.
- Dashboard scope is fulfilled by the calculator's single main screen.
- Basic Project Structure and Basic Documentation apply as stated.

**Related:** REQ-SCOPE

### REQ-SCOPE · approved · source: requirements:delivery-scope

Delivery scope is set to lightweight; this is requirements version 1, approved by the product owner.

- Delivery scope: lightweight.
- Requirements version: 1.
- Status: approved.
- Detailed in/out scope boundaries (no scientific functionality, no saved calculation history, no accounts, no payments) are captured in the Design & documentation functional requirement group (REQ-FUNC-5) and in EPIC-005 of the plan.

### REQ-FUNC-1 · approved · source: requirements:opening-the-calculator

Requirements covering instant, free access to the calculator and responsive behavior across devices.

- Open the calculator instantly: anyone can open the application URL in a browser and see the main screen ready to use, with no sign-up, login or account prompt.
- Free to use with no payment: no payment, billing or subscription step ever appears while entering, completing or clearing calculations.
- Adapt to desktop and mobile: the layout adapts to screen size, staying legible on desktop and usable by touch on mobile; resizing the browser window reflows the layout without cutting off or disabling any controls.

### REQ-FUNC-2 · approved · source: requirements:doing-calculations

Requirements for the core arithmetic operations the calculator must perform.

- Four basic arithmetic operations: add, subtract, multiply and divide two numbers and press equals to see the result.
- Calculate a percentage: pressing the percentage key converts the shown value to its percentage form (e.g. for tips or discounts) rather than causing an error.
- Enter decimal numbers: numbers may include a decimal point; pressing the decimal point key again while a number already has one does not add a second point.
- Toggle positive and negative: a sign toggle key switches the displayed number between positive and negative.

### REQ-FUNC-3 · approved · source: requirements:entering-numbers

Requirements for how numbers and operations can be entered and cleared.

- Use on-screen buttons: tap or click digit and operation buttons, with the display updating on each press, so the calculator works without a physical keyboard.
- Use the keyboard: type digits and operators and press Enter to calculate; keys that do not map to any calculator function are ignored and leave the display unchanged.
- Clear the entry or calculation: pressing clear resets the display to 0, discarding the current entry and any previous operands.

### REQ-FUNC-4 · approved · source: requirements:error-handling

Requirement for graceful handling of invalid operations.

- Handle divide by zero: dividing by zero shows a clear error message such as "Cannot divide by zero" instead of crashing; pressing clear returns the display to 0 and makes the calculator ready for a new calculation.

### REQ-FUNC-5 · approved · source: requirements:design-and-documentation

Requirements for the design toolchain, usage documentation and explicit scope boundaries.

- Build previews with Magic UI: interactive preview screens produced in the design phase must be created using the Magic UI MCP integration, and the code generated in those preview screens must use the Magic UI integration.
- Basic usage documentation: short documentation describing supported operations (add, subtract, multiply, divide, percentage, clear), decimal and sign-toggle support, and keyboard and on-screen input; it also states scope limits -- no scientific functionality, no saved history, no accounts, no payments.
- Record scope boundaries: excluded/non-applicable baseline capabilities are explicitly recorded as scope assumptions -- no accounts or login, no stored calculation history or user data to manage, and no payments or billing.

### NFR-001 · approved · source: requirements:NFR-001

[compatibility] The calculator must work in both desktop and mobile web browsers, supporting mouse, touch and keyboard input.

Layout must reflow to fit the screen so no controls are cut off or unusable, across desktop and mobile browsers.

### NFR-002 · approved · source: requirements:NFR-002

[performance] Every calculation runs entirely in the user's browser.

The display must update immediately with each button press or key press, with no waiting for a server.

### NFR-003 · approved · source: requirements:NFR-003

[privacy] The product stores no user data.

No calculation history, no personal data and no user accounts are kept anywhere; calculations happen only in the user's browser.

### NFR-004 · approved · source: requirements:NFR-004

[accessibility] The calculator must be fully usable with the keyboard alone.

Users can type digits and operators and press Enter to calculate without needing a mouse or touch.

### NFR-005 · approved · source: requirements:NFR-005

[scalability] The app is open to any member of the public, so hosting must stay reliably reachable under public traffic.

Must cope with public traffic without special configuration.

### NFR-006 · approved · source: requirements:NFR-006

[security] Accepted risk: the calculator is intentionally open with no sign-in.

No sign-up, login, sessions or accounts; no authentication or access control is built or required. This is an accepted risk, not an oversight.
<!-- sdlc:auto:end narrative -->

<!-- sdlc:auto:start summary -->
**Requirements version:** v1  
**Delivery scope:** lightweight  
**Approved:** 2026-11-17

**Capabilities in scope:** Authentication, Basic Project Structure, Dashboard, CRUD Screens, REST APIs, Database Integration, Basic Documentation

**Approved technology stack:**

| Layer | Choice | Rationale |
|---|---|---|
| backend | FastAPI | Your calculator does every calculation in the browser and stores nothing, so there is genuinely no business logic for a server to run. FastAPI is the platform's backend and is worth keeping only as a thin shell to serve the app and leave room for the odd operational need (a health check, serving the built files). I am recommending it to satisfy the layer, not because your features demand server-side code. |
| cloud | AWS | Your app is open to any member of the public on desktop and mobile, so it needs reliable, globally reachable hosting that scales with traffic. AWS is the platform's cloud and comfortably serves a free, lightweight web app to a general audience with no special configuration. |
| database | PostgreSQL | You confirmed there is no sign-up, no user accounts and no persistent calculation history, so the product stores no data and has nothing to put in a database. PostgreSQL is named here only because the layer must be filled; it is the platform default and the safe choice should you ever decide to keep anything server-side later. |
| frontend | React | This is the whole product. Your calculator lives entirely in the browser on both desktop and mobile, with on-screen buttons, keyboard input, decimals, sign toggle and divide-by-zero handling. React is the frontend this platform builds, and it fits your explicit requirement to assemble the interface from Magic UI components, which are React components designed to drop straight into a React app and preview through the Magic UI MCP integration. |
<!-- sdlc:auto:end summary -->

<!-- sdlc:auto:start epics -->
## EPIC-001: Basic Arithmetic Calculation

The core purpose of the product: a basic-arithmetic calculator that performs add, subtract, multiply, divide, percentage and clear operations on decimal numbers, with a sign toggle. This is explicitly limited to everyday arithmetic — there is no scientific functionality.

### US-001: Perform the four basic arithmetic operations

**Priority:** critical

> As a member of the public using the calculator, I want to add, subtract, multiply and divide two numbers, so that I can do everyday arithmetic quickly.

| ID | Given | When | Then |
|---|---|---|---|
| AC-001 | the calculator is open and showing 0 | I enter 7, press add, enter 3 and press equals | the display shows 10 |
| AC-002 | the calculator is open | I enter 9, press subtract, enter 4 and press equals | the display shows 5 |
| AC-003 | the calculator is open | I enter 6, press multiply, enter 5 and press equals | the display shows 30 |
| AC-004 | the calculator is open | I enter 8, press divide, enter 2 and press equals | the display shows 4 |

### US-002: Calculate a percentage

**Priority:** high

> As a member of the public using the calculator, I want to apply a percentage to a number, so that I can work out things like tips or discounts.

| ID | Given | When | Then |
|---|---|---|---|
| AC-005 | the calculator is open | I enter 200, press multiply, enter 10 and press the percentage key followed by equals | the display shows the result of 10 percent of 200, which is 20 |
| AC-006 | a number is shown on the display | I press the percentage key | the value is converted to its percentage form rather than throwing an error |

### US-003: Enter decimal numbers

**Priority:** high

> As a member of the public using the calculator, I want to enter numbers with a decimal point, so that I can calculate with non-whole amounts.

| ID | Given | When | Then |
|---|---|---|---|
| AC-007 | the calculator is open | I enter 2.5, press add, enter 1.25 and press equals | the display shows 3.75 |
| AC-008 | I am entering a number that already contains a decimal point | I press the decimal point key again | no second decimal point is added to the number |

### US-004: Toggle the sign of a number

**Priority:** medium

> As a member of the public using the calculator, I want to switch a number between positive and negative, so that I can calculate with negative values.

| ID | Given | When | Then |
|---|---|---|---|
| AC-009 | the display shows 5 | I press the sign toggle key | the display shows -5 |
| AC-010 | the display shows -5 | I press the sign toggle key | the display shows 5 |

## EPIC-002: Calculator Input and Clearing

Users can drive the calculator using both the on-screen buttons and the keyboard, and can clear the current entry or the whole calculation. These behaviours are open assumptions confirmed in the understanding: the calculator supports keyboard and on-screen button input and a clear function.

### US-005: Use on-screen buttons

**Priority:** critical

> As a member of the public on a touch or mouse device, I want to tap or click on-screen buttons for digits and operations, so that I can use the calculator without a physical keyboard.

| ID | Given | When | Then |
|---|---|---|---|
| AC-011 | the calculator is open on screen | I click the on-screen digit and operation buttons to compute 4 plus 5 | the display updates with each press and shows 9 after equals |
| AC-012 | the calculator is open on a touch device | I tap an on-screen button | the corresponding digit or operation is registered |

### US-006: Use the keyboard

**Priority:** high

> As a member of the public on a device with a keyboard, I want to type digits and operators and press Enter to calculate, so that I can calculate faster without clicking.

| ID | Given | When | Then |
|---|---|---|---|
| AC-013 | the calculator is open with keyboard focus | I type 4, +, 5 and press Enter | the display shows 9 |
| AC-014 | the calculator is open with keyboard focus | I press a key that does not map to any calculator function | the key is ignored and the display is unchanged |

### US-007: Clear the current entry or calculation

**Priority:** high

> As a member of the public using the calculator, I want to clear what I have entered, so that I can correct a mistake or start a new calculation.

| ID | Given | When | Then |
|---|---|---|---|
| AC-015 | the display shows a number or an in-progress calculation | I press the clear button | the display resets to 0 and no previous operands are retained |

## EPIC-003: Graceful Error Handling

The calculator handles invalid operations such as divide-by-zero gracefully, surfacing a clear message instead of crashing, and recovers to a usable state. This reflects the confirmed open assumption on graceful error handling.

### US-008: Handle divide by zero gracefully

**Priority:** high

> As a member of the public using the calculator, I want a clear message when I try to divide by zero, so that I understand the result is undefined and the app does not break.

| ID | Given | When | Then |
|---|---|---|---|
| AC-016 | the calculator is open | I enter 5, press divide, enter 0 and press equals | the display shows a clear error indication (for example "Error" or "Cannot divide by zero") rather than crashing |
| AC-017 | an error is shown on the display after an invalid operation | I press clear | the display returns to 0 and the calculator is ready for a new calculation |

## EPIC-004: Responsive Web App, Main Screen and Project Structure

The product is delivered as a single responsive web application with a basic project structure. The calculator screen is the main (dashboard) view of the app. It is open to anyone with no sign-up or user accounts, is free to use with no payments or billing, and works on both desktop and mobile browsers. Open assumptions surfaced here: it is a responsive web app (not a native mobile app), open to anyone with no accounts, and free with no payments. The app design phase must use the Magic UI MCP integration for the interactive preview screens, and the code generated in those preview screens must use the Magic UI integration.

### US-009: Open the calculator without signing up

**Priority:** critical

> As a member of the public, I want to open the calculator in my browser and use it immediately, so that I can do quick arithmetic without creating an account.

| ID | Given | When | Then |
|---|---|---|---|
| AC-018 | I navigate to the application URL in a browser | the page loads | the calculator main screen is shown and usable with no sign-up, login or account prompt (assumption: open to anyone with no user accounts) |
| AC-019 | I am using the calculator | I complete and clear calculations | I am never asked for payment and no billing step appears (assumption: free to use with no payments or billing) |

### US-010: Use the calculator on desktop and mobile browsers

**Priority:** high

> As a member of the public on any device, I want the calculator layout to adapt to my screen size, so that I can use it comfortably on a phone or a desktop.

| ID | Given | When | Then |
|---|---|---|---|
| AC-020 | I open the app in a desktop browser | the calculator loads | the buttons and display are laid out legibly for a large screen |
| AC-021 | I open the app in a mobile browser | the calculator loads | the layout adapts to the small screen and all buttons remain usable by touch (assumption: responsive web app, not a native mobile app) |
| AC-022 | the calculator is open | I resize the browser window | the layout reflows without controls becoming cut off or unusable |

### US-011: Design preview screens with the Magic UI integration

**Priority:** high

> As a designer building the app in the design phase, I want the interactive preview screens to be built with the Magic UI MCP integration, so that the delivered UI matches the required design toolchain.

| ID | Given | When | Then |
|---|---|---|---|
| AC-023 | the app design phase is underway | interactive preview screens are produced | they are created using the Magic UI MCP integration |
| AC-024 | an interactive preview screen generates code | the generated code is reviewed | it uses the Magic UI integration |

## EPIC-005: Documentation and Scope Boundaries

Basic documentation for the calculator, plus an explicit record of the scope boundaries chosen for this Lightweight MVP. Several baseline capabilities included at this scope do not apply to a public, account-free, client-side calculator and are recorded here as assumptions rather than built as features: Authentication is not applicable because there are no sign-up or user accounts; no persistent calculation history or user data is stored, so Database Integration and CRUD screens have no user-facing data to manage; and there are no payments.

### US-012: Provide basic usage documentation

**Priority:** medium

> As a new user or stakeholder, I want short documentation describing what the calculator does and how to use it, so that I understand its features and its limits.

| ID | Given | When | Then |
|---|---|---|---|
| AC-025 | the project is delivered | I open the basic documentation | it describes the supported operations (add, subtract, multiply, divide, percentage, clear), decimal and sign-toggle support, and keyboard and on-screen input |
| AC-026 | I read the documentation | I look for scope boundaries | it states that there is no scientific functionality, no persistent calculation history, no accounts and no payments |

### US-013: Record non-applicable baseline capabilities as scope assumptions

**Priority:** low

> As a stakeholder tracking scope, I want the excluded or non-applicable baseline capabilities to be explicitly recorded, so that there is no expectation of features the product deliberately omits.

| ID | Given | When | Then |
|---|---|---|---|
| AC-027 | the calculator has no sign-up or user accounts | the Authentication capability is considered | it is recorded as not applicable to this product (assumption: open to anyone with no accounts), with no login, session or account features built |
| AC-028 | no persistent calculation history or user data is stored | the Database Integration and CRUD-screen capabilities are considered | they are recorded as having no user-facing data to persist or manage (assumption: no persistent calculation history is stored) |
| AC-029 | the app is free | payment-related scope is considered | it is recorded that there are no payments, billing or subscriptions |
<!-- sdlc:auto:end epics -->
