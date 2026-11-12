# Moped AR Ride View

Interactive first-person prototype of an augmented reality riding display for a semi-autonomous moped, designed for older adults with mild arthritis. Built for think-aloud usability testing.

**Live demo:** https://iliasamarin1.github.io/Moped-AR-View/

## What it does

- Rider's-eye view of a 3D neighborhood street with a see-through AR readout: speed, speed limit, next turn and riding mode.
- A separate controller for Wizard-of-Oz testing: blinkers, hazard, horn, AUTO (riding assistance), takeover, pedestrian, obstacle and blind-spot scenarios.
- A vertical phone display for the screen mounted on the wheel.

Everything is simulated. It is a concept prototype, not vehicle software.

## Wizard-of-Oz setup (three screens)

The same address serves three screens. Open the plain address first; it is the controller.

| Screen | Address ending | Who looks at it | What it shows |
| --- | --- | --- | --- |
| Controller | (nothing) | Wizards | A button for every rider action and scenario, a preview of the rider's view, and a session log. No wheel. |
| Participant | `#display` | Rider | The AR view only. |
| Phone | `#phone` | Rider | A vertical phone display: speed, limit, mode, next turn, route map, blinkers and alerts. |

**On one computer (laptop plus monitor or projector):** click **Open participant screen** and **Open phone screen** on the controller, then drag those windows where you need them. All windows must be in the same browser.

**On a real phone:** click **Connect a real phone** on the controller. It shows an address ending in `#phone-` and a five-character code. Open that address on the phone, or open the `#phone` address and type the code. Both devices need internet access. The ride state is relayed through a public message broker (broker.hivemq.com) under that random code; nothing personal is sent.

Keyboard shortcuts on the controller: arrow keys for blinkers, H hazard, B horn, A AUTO, G rider took over, S start or pause, P pedestrian, T obstacle, Q and E blind spots.

Messages meant only for the wizards (for example "Not enough straight road here") appear in the panel and the log, never on the rider's screens.

## Running it

Open `index.html` in a browser. It is a single file; the 3D street loads three.js from a CDN and falls back to a flat drawing if that is unavailable.
