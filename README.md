# Moped AR Ride View

Interactive first-person prototype of an augmented reality riding display for a semi-autonomous moped, designed for older adults with mild arthritis. Built for think-aloud usability testing.

**Live demo:** https://iliasamarin1.github.io/Moped-AR-View/

## What it does

- Rider's-eye view of a 3D neighborhood street with a see-through AR readout: speed, speed limit, next turn and riding mode.
- Steering wheel with clickable controls: blinker paddles, hazard button, horn and AUTO (riding assistance).
- Test controls along the top: start or pause the journey, pedestrian scenario, emergency takeover scenario, left and right blind-spot warnings, and reset.

Everything is simulated. It is a concept prototype, not vehicle software.

## Wizard-of-Oz setup (two screens)

The wheel and test controls can run on one screen while the participant sees only the AR view on another.

1. Open the live demo on the controllers' laptop. This is the controller: it has the wheel and the test controls.
2. Click **Open participant screen**. A second window opens at the same address ending in `#display`. It shows only the AR view.
3. Drag that window to the external monitor or projector the participant faces and make it full screen (F11, or Ctrl+Cmd+F on a Mac).
4. Everything the controllers press on the wheel or the test bar appears on the participant screen straight away.

Both windows must be in the same browser on the same computer. Sounds play from the controller window.

## Running it

Open `index.html` in a browser. It is a single file; the 3D street loads three.js from a CDN and falls back to a flat drawing if that is unavailable.
