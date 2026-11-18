# Competitive Analysis & Journey Map (Module 2)

## Responses
- **Role, who are you solving for? (the specific user segment or profile):** Diego, Delivery Driver (3 years)
Role: A frontline delivery driver who completes dozens of stops a day, often outdoors and one-handed.
- **Goal, what is this user ultimately trying to achieve?:** Goal: To confirm each delivery quickly and move to the next stop without the app slowing him down.
- **Friction, the main barrier (moment of misery) stopping them from succeeding:** Friction: At a rainy doorstep with a package in hand, he must tap through three screens to mark a stop delivered (UXR-01, BUG-2055), so he has started texting his dispatcher instead.
- **External tools, the outside platforms or tools the user is forced to use:** The research documents one external tool for Diego: text messages to his dispatcher (UXR-01). The sequence below is reconstructed from that quote and the related bug report
- **The process, the 3 to 5 manual steps the user takes to get the job done:** Arrives at the stop and completes the handoff, still holding the package, in the rain.
Skips the in-app “Mark Delivered” flow (3 taps across 3 screens, BUG-2055).
Texts the dispatcher that the stop is delivered.
Moves on to the next stop without updating the app.
The dispatcher then has to reconcile the text against what the dashboard shows, and may update the stop manually or simply carry the knowledge in their head.
- **Core frustration, the exact moment the process feels most “broken”:** Core frustration: Diego can’t complete the most basic, most frequent action in the app without stopping what he’s doing.

The exact moment it feels most broken: He is standing at a doorstep in the rain, a package still in one hand, and has to tap through three screens just to mark the stop delivered (UXR-01, BUG-2055). The delivery itself is done. The app is the only thing between him and the next stop, and it demands two free hands and his full attention at the point where he has neither.
- **The evidence, a specific quote or behavior from the research that proves this:** The evidence: UXR-01, Diego, delivery driver, 3 years:

“To mark a stop delivered I tap through three screens. In the rain, at a doorstep, with a package in one hand. I’ve started just texting my dispatcher instead.”
- **Your journey map, a shareable link, or the map file you committed (e.g. journey-map.html):** https://github.com/taylorsmith-prod/pm-final-project/blob/c83a38e8ddede60c3068f84335abde3126fa61e1/02-discovery/velocity-future-state-journey.html
