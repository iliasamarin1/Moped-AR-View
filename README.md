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
| Controller | (nothing) | Wizards | The wheel (click its paddles, hazard, horn, AUTO and grips), gas and brake pedals to hold, scenario buttons, a preview of the rider's view, and a session log. |
| Participant | `#display` | Rider | The AR view only. |
| Phone | `#phone` | Rider | A vertical phone display: speed, limit, mode, next turn, route map, blinkers and alerts. |

**On one computer (laptop plus monitor or projector):** click **Open participant screen** and **Open phone screen** on the controller, then drag those windows where you need them. All windows must be in the same browser.

**On separate devices (controller laptop, participant laptop, phone):**

1. On the controller laptop, open the plain address and click **Connect other devices**. The bar shows a five-character code and two addresses.
2. On the participant laptop, open the address ending in `#display-CODE` (or open `#display` and type the code). Make it full screen and click once anywhere so the browser allows sound.
3. On the phone, open the address ending in `#phone-CODE` (or open `#phone` and type the code).
4. The controller bar says "Participant laptop connected. Phone connected." when both are linked.

**Latency.** After joining, the devices take a few seconds to set up a direct link to the controller, and the controller bar then says "connected directly". Over a direct link, presses reach the participant screen in a few milliseconds plus the local network. If a direct link cannot be made (some campus Wi-Fi blocks devices from talking to each other), the bar says "through the internet relay (slower)": motion stays smooth, but presses can take a few hundred milliseconds. Putting all devices on the same phone hotspot usually allows the direct link.

All three devices need internet access. The ride state is relayed through a public message broker (broker.hivemq.com, secure WebSocket on port 8884) under that random code; nothing personal is sent. Sounds (beeps, horn) play on the participant laptop while it is linked, and the controller stays quiet. The controller remembers its code, so reloading it reconnects to the same devices. To use a different broker, add `?broker=wss://host:port/path` to every device's address.

**Destination.** At the start the phone shows "Where to?" with Pharmacy, Grocery store and Home. When the rider taps one, the route is set on every screen and the end of the route is named ("Pharmacy in 180 ft", "You have arrived at the pharmacy"). The wizards can also pick it with the Destination buttons on the controller. If the journey starts with no destination, it is set to the pharmacy.

Keyboard shortcuts on the controller: left and right arrows for blinkers, hold up arrow for gas and down arrow for brake, H hazard, B horn, A AUTO, G rider took over, S start or pause, P pedestrian, T obstacle, Q and E blind spots.

Power: the button on the steering column below the wheel (or O) switches the moped on and off. When it is off the rider's AR display and phone go dark and every other control is ignored. The moped must be stopped before it can be switched off.

Steering: drag the slider under the wheel (or hold Z or X) to turn the wheel. The rider's view swings and the moped drifts across the lane while it is moving; the slider springs back when released. Turns at junctions still happen automatically. Steering while AUTO is on switches to manual.

Pedals: holding gas speeds up (to 30 mph; the limit ring turns red above 25) and starts the journey if it has not started. Holding brake slows to a stop. Braking while AUTO is on switches to manual, and braking during a takeover request counts as taking over.

Messages meant only for the wizards (for example "Not enough straight road here") appear in the panel and the log, never on the rider's screens.

## Running it

Open `index.html` in a browser. It is a single file; the 3D street loads three.js from a CDN and falls back to a flat drawing if that is unavailable.
