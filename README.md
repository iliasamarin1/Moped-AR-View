# Moped AR Ride View

Interactive first-person prototype of an augmented reality riding display for a semi-autonomous moped, designed for older adults with mild arthritis. Built for think-aloud usability testing.

**Live demo:** https://iliasamarin1.github.io/Moped-AR-View/

## What it does

- Rider's-eye view of a 3D neighborhood street with a see-through AR readout: speed, speed limit, next turn and riding mode.
- Steering wheel with clickable controls: blinker paddles, hazard button, horn and AUTO (riding assistance).
- Test controls along the top: start or pause the journey, pedestrian scenario, emergency takeover scenario, left and right blind-spot warnings, and reset.

Everything is simulated. It is a concept prototype, not vehicle software.

## Running it

Open `index.html` in a browser. It is a single file; the 3D street loads three.js from a CDN and falls back to a flat drawing if that is unavailable.
