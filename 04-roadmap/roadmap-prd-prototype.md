# Feature Roadmap, Module 4 · RouteLogic Velocity

**Team:** 2 engineers + 1 designer + 1 CS lead

## Strategic anchors
- **Persona:** The Fleet Coordinator
- **Primary metric:** Average daily time lost to manual workarounds. The baseline is 31 minutes a day. The target is a 30% reduction, to about 22 minutes.
- **Moment of misery:** Logging compliance checks after routes are assigned.
- **Guardrail:** Manager Reporting CSAT, currently 4.5, which must not fall below 4.0.

## Scoring
| Feature | Value | Effort | Quadrant | Decision | Rationale |
|---|---|---|---|---|---|
| B1 One-Click Compliance Checklist | 5 | 3 | Major Project | Now | It attacks the Moment of Misery directly. The 14.6-min step is about half the 31-min baseline, so even a 15% cut gets you 2+ min toward the 9-min target. |
| B2 Smart Daily Report Auto-Fill | 3 | 3 | Time Sinker | Next | It's real friction, but not the Moment of Misery. It sits directly on the 4.5 CSAT guardrail, and an AI auto-fill error is the most likely way to breach 4.0. |
| B3 Shift Handoff Wizard | 4 | 3 | Major Project | Next | A claimed 6.8 min/day is about 75% of the 9 minutes you need, and it targets a manual workaround. It doesn't touch Manager Reporting, so the CSAT guardrail is safe. |
| B4 Mobile-First Coordinator Dashboard | 4 | 5 | Major Project | Next | It's the right long-term shape, but it's a rebuild. Two engineers can't ship and measure it in a 4-week pilot. |
| B5 Step Progress Indicator | 2 | 1 | Fill-In | Later | Cheap, but it shows where you are without saving a single minute. It's also added UI where Velocity is meant to strip noise. |
| B6 Driver Alert Notifications | 4 | 4 | Major Project | Now | It serves the driver rather than the coordinator, and push infrastructure is heavy. A compliance-flag alert might help later, but not in this pilot. |
| B7 Contextual AI ETA Display | 1 | 2 | Fill-In | Cut | 11% adoption says coordinators don't want it. Surfacing it more widely adds noise and is unrelated to compliance or handoff friction. |
| B8 Fleet Analytics Manager View | 1 | 5 | Time Sinker | Cut | It's a sales-demo feature. It does nothing for the coordinator's daily time loss and costs the most to build. |
| B9 Compliance Audit Trail Export | 2 | 2 | Fill-In | Later | It serves after-the-fact audits, not the daily minutes lost, so it doesn't move the primary metric. |
| B10 In-App Coordinator Training | 2 | 2 | Fill-In | Later | Training doesn't remove a workaround. Your CS lead can run walkthroughs manually for 3 accounts. |

## Roadmap
### NOW, Pilot (4 weeks, 3 accounts)
- **B1 One-Click Compliance Checklist**, It attacks the Moment of Misery directly. The 14.6-min step is about half the 31-min baseline, so even a 15% cut gets you 2+ min toward the 9-min target.
- **B6 Driver Alert Notifications**, It serves the driver rather than the coordinator, and push infrastructure is heavy. A compliance-flag alert might help later, but not in this pilot.

### NEXT, GA Release (weeks 5-8)
- **B2 Smart Daily Report Auto-Fill**, It's real friction, but not the Moment of Misery. It sits directly on the 4.5 CSAT guardrail, and an AI auto-fill error is the most likely way to breach 4.0.
- **B3 Shift Handoff Wizard**, A claimed 6.8 min/day is about 75% of the 9 minutes you need, and it targets a manual workaround. It doesn't touch Manager Reporting, so the CSAT guardrail is safe.
- **B4 Mobile-First Coordinator Dashboard**, It's the right long-term shape, but it's a rebuild. Two engineers can't ship and measure it in a 4-week pilot.

### LATER, backlog
- **B5 Step Progress Indicator**, Cheap, but it shows where you are without saving a single minute. It's also added UI where Velocity is meant to strip noise.
- **B9 Compliance Audit Trail Export**, It serves after-the-fact audits, not the daily minutes lost, so it doesn't move the primary metric.
- **B10 In-App Coordinator Training**, Training doesn't remove a workaround. Your CS lead can run walkthroughs manually for 3 accounts.

### ✂ Cut List
- **B7 Contextual AI ETA Display**, 11% adoption says coordinators don't want it. Surfacing it more widely adds noise and is unrelated to compliance or handoff friction.
- **B8 Fleet Analytics Manager View**, It's a sales-demo feature. It does nothing for the coordinator's daily time loss and costs the most to build.
