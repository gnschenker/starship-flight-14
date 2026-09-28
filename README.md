# Starship Flight 14

A browser animation of Starship Flight 14: Super Heavy B21 and Ship 41 lifting off from Starbase Pad 2 on 28 September 2026, inserting into orbit, deploying 26 Starlink V3 satellites, and splashing down in the Pacific off Chile.

Everything lives in one file, [`starship-flight-14.html`](starship-flight-14.html). Three.js draws the Earth, the stack, engine plumes, and a picture-in-picture of Super Heavy after hot-staging. Playback follows the published event timeline, with an automatic time warp through the long coasts and a cinematic camera that tracks the ship.

## Run it

Open [`starship-flight-14.html`](starship-flight-14.html) in a browser. Three.js and the Earth imagery load from the network, so the page needs an internet connection. WebGL 2 is required.

Add a `t` query parameter to start at a mission elapsed time in seconds. `starship-flight-14.html?t=142` opens at hot-staging; `?t=1517` opens at the orbital insertion burn.

## Controls

| Input | Action |
| --- | --- |
| Drag | Orbit the camera around the vehicle. Turns off auto camera. |
| Scroll or pinch | Zoom. Turns off auto camera. |
| Space | Play or pause. |
| ← / → | Jump to the previous or next timeline event. |
| Timeline | Click an event to jump there. |
| Scrubber | Drag to any point in the flight. |
| Speed | Playback multiplier on top of the automatic time warp. |
| Auto camera | Toggle the scripted camera. Restart turns it back on. |
| Labels | Show or hide callouts. |

After separation, a picture-in-picture follows Super Heavy through boostback and landing in the Gulf of America. The main view stays on Starship.

## What the animation models

Mission times, phase names, and the event list come from the [SpaceX Flight 14 page](https://www.spacex.com/launches/starship-flight-14). Liftoff in the animation is 12:46 UTC (7:46 a.m. CDT). The timeline in the page is marked approximate.

The ship’s path is generated in the page:

- Ascent is integrated from speed and flight-path-angle profiles through engine cutoff at T+491 s.
- A coast to apogee is followed by a short insertion burn into a roughly 275 km apogee orbit at 26.4° inclination. Perigee is chosen so the ground track ends near 72.9° W, about 200 km off Chile, after six and a half revolutions.
- Deorbit, entry, the belly-flop, and the landing flip are scripted profiles down to splashdown.
- Super Heavy follows the ship until hot-staging, then a separate boostback and landing path to the Gulf of America.

Vehicle size is magnified as the camera pulls back, so the stack stays readable against the Earth. Speeds and altitudes on the HUD are outputs of this model.

## Credits

Earth day imagery is NASA Blue Marble via [three-globe](https://github.com/vasturiano/three-globe). Night lights and the bump, roughness, and cloud map are from the [three.js](https://github.com/mrdoob/three.js) examples (Black Marble). Launch-site context uses Esri, Maxar, and Earthstar Geographics imagery. Three.js itself is loaded from jsDelivr (`three@0.170.0`).
