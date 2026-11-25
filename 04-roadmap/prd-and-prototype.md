# One-Click Compliance Checklist, Simplified PRD (RouteLogic)

**Author:** Me · **Status:** Draft · **Target:** High-Fidelity Prototype · **Persona:** The Fleet Coordinator

## 1. The Big Picture
- **Vision:** The moment a route is assigned, the Fleet Coordinator confirms a pre-filled compliance checklist in one click, turning a 14.6-minute chore into a few seconds and giving back the time that manual workarounds cost them every day.
- **Press release:** Every Fleet Coordinator knows the moment: the routes are finally assigned, and then comes the compliance logging. Every route, every check, every field typed out by hand, a 14.6-minute step that eats nearly half of the 31 minutes a day coordinators lose to manual workarounds. With RouteLogic Velocity's One-Click Compliance Checklist, that moment disappears. The instant a route is assigned, the checklist is already filled in from what RouteLogic knows about the route, driver and vehicle. The Coordinator confirms it, overrides anything that isn't right, and moves on.

Coordinators get to stop being data-entry clerks and go back to dispatching, with the same compliance record and the same reporting their managers already trust. Our goal for the pilot is a 30% cut in daily time lost to workarounds, from 31 minutes to about 22, starting with the single step coordinators dread most.
- **Success metric:** Average daily time lost to manual workarounds. The baseline is 31 minutes a day. The target is a 30% reduction, to about 22 minutes.
- **Guardrail:** Manager Reporting CSAT, currently 4.5, which must not fall below 4.0.

## 2. The Details
### User stories
- As a Fleet Coordinator, I want the compliance checklist pre-filled the moment I assign a route, so that I confirm instead of typing.
- As a Fleet Coordinator, I want to pass or fail each check with one tap, so that a normal route takes seconds, not minutes.
- As a Fleet Coordinator, I want to override any pre-filled value, so that the compliance record is still accurate when something is different.
- As a Fleet Coordinator, I want to submit the whole checklist with one click, so that I can get back to dispatching.
- As a Fleet Coordinator, I want to see how long the check took, so that I can see the time I'm getting back each day.
### Screens to build
- 1. Route Assignment (entry point): the list of just-assigned routes, each with a "Log compliance" button that opens the checklist for that route.
- 2. Compliance Checklist (feature core): one screen with the route, driver and vehicle fields pre-filled, one-tap pass/fail on every check, editable fields, and a single Submit button.
- 3. Confirmation (success): "Compliance logged" with the route, the number of checks passed or failed, and the time taken, plus a button back to the next unlogged route.
### Functional requirements
- The system must pre-fill route, driver, vehicle, and assignment time on the checklist with no typing required.
- The system must show every required field from the current compliance flow, so no field is dropped.
- The system must let the user mark each check pass or fail in one tap, with pass as the default.
- The system must let the user edit any pre-filled value before submitting.
- The system must submit the full checklist with one click and block submission only if a required field is empty.
- The system must open the checklist directly from the route assignment screen, with no navigation through other modules.
- The system must measure and display time-on-task from opening the checklist to submitting it.
- The system must write the result in the same shape as the existing compliance record (mocked in the prototype).
### Smart behaviors (Situation → Outcome)
- If a route is assigned → the "Log compliance" button appears on that route with the checklist already pre-filled.
- If the user taps Fail on any check → a short required reason field appears for that item only.
- If the user edits a pre-filled value → that field is marked as changed so the override is visible before submitting.
- If a required field is empty → Submit is disabled and the missing field is highlighted.
- If all checks are passed with no edits → Submit stays one click and the confirmation shows a fast time-on-task.
- If the user submits → the timer stops, the confirmation screen shows the time taken, and the route is marked as logged.
### Technical constraints
- No external API calls; all route, driver and vehicle data is hardcoded mock data.
- React useState only; no database, no local or session storage, no backend.
- No AI-generated answers; pre-fill comes only from the mock route data.
- No push notifications or driver-facing views.
- No changes to the daily report or Manager Reporting output.
- No audit PDF export, per-account checklist configuration, or mobile redesign.
- Exactly 3 screens; no extra pages, settings, or navigation.

## 3. The Logistics
### Features out
- No push or driver-facing compliance alerts.
- No changes to the daily report or Manager Reporting output.
- No AI-generated answers to compliance items.
- No per-account configurable checklists.
- No audit PDF export.
- No mobile redesign.
### Edge cases & safety guard
- Required field empty → Submit is disabled and the missing field is highlighted.
- Check marked Fail with no reason → block submission and prompt for the reason.
- Pre-fill data missing for a field → leave it blank and flag it for the Coordinator, never guess.
- Submit clicked twice → record only one submission.
- Route already logged → show it as logged and don't allow a duplicate checklist.
- Safety: never invent or auto-answer a compliance value; never submit without the Coordinator's explicit click; never silently change a pre-filled value; never alter the daily report.
### Decision log
- Removed AI-generated answers to focus on pre-filling only from known route data, because a wrong guess on a compliance record is a regulatory risk.
- Kept the output identical to the existing compliance record and left Manager Reporting untouched, to protect the 4.5 CSAT guardrail (floor 4.0).
### Evals
- Pre-fill accuracy: at least 95% of pre-filled fields match the source route data with no edit needed.
- Time-on-task: an all-pass route is logged in 60 seconds or less, against the 14.6-minute baseline.
- Safety: 0 submissions with an empty required field or a Fail without a reason, and 0 AI-invented values.

## MoSCoW scope
- **Must:** Pre-filled checklist per assigned route. Pull every field we already know (route, driver, vehicle, assignment time) so the Coordinator confirms rather than types. This is the feature.; Single-screen form, launched from the route assignment. The Moment of Misery is logging checks right after assignment, so it can't be a separate trip into another module.; Per-item pass/fail with one tap, defaulting to the most common answer, with the Coordinator able to override any pre-filled value.; One-click submit that writes to the same compliance record the current flow does. If the record differs, downstream reporting breaks and your 4.5 CSAT is at risk.; Instrumentation of time-on-task for the compliance step. Without it you can't show movement against the 31→22 target, so it's a must even though no user sees it.; Parity with every field the current flow requires. If a required field is dropped, the feature fails.
- **Should:** Flag-and-explain on failed checks. One short free-text or reason-code field when an item fails, so no side note is needed.; Save-as-draft and resume, since interruptions are normal in dispatch.; Pre-fill for repeat routes. Carry over answers from the same driver/vehicle's last check, but only if the pilot data shows they're stable.; A before/after baseline timing from the 3 pilot accounts, owned by your CS lead. You have the 14.6-min figure but should confirm it at each account.
- **Could:** Bulk-confirm across several routes assigned at once; Keyboard shortcuts for power users; Confidence indicators on pre-filled values; A history view of past checklists per route; Smarter defaults that learn per account
- **Won't (now):** Pushing compliance flags to drivers (B6). It's the most likely add-on, and it brings in a different persona and push infrastructure.; Any change to the daily report or Manager Reporting output (B2). This is your CSAT guardrail risk, so B1 writes to the existing compliance record and nothing downstream changes.; AI-generated answers on compliance items. Pre-fill only from data we already hold, because a wrong guess on a compliance record is a regulatory problem.; Per-account configurable checklists. All 3 pilot accounts get one standard checklist.; Audit PDF export (B9). It would turn up in the first review as "while you're in there."; Redesigning the surface for mobile (B4). Build on the current surface.

---
**Builder hook:** Build a working prototype based on this PRD. Use the User Story as the core flow, Functional Requirements as build constraints, and prioritize speed and clarity over visual complexity.
