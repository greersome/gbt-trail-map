# Greenbay Trail Day — Stake Location Page

A single-page web app volunteers open on their phone to confirm their GPS is
accurate before placing a trail stake. It checks the phone's location
permission, walks the user through turning it on (iPhone / Android steps),
and shows a live accuracy readout that must reach a good fix before they can
continue.

## Files

- **index.html** — the page that goes live. Currently the **high-vis** variant:
  the whole screen floods red → amber → green with a large accuracy number.
  Built for a gloved hand, bright sun, and a two-second glance.
- **alt-instrument-version.html** — the **instrument** variant: kraft-paper
  look with a shrinking GPS-uncertainty circle against 8 m / 20 m reference
  rings. Quieter, more crafted feel.

To switch which one is live, just copy the other over index.html:

    cp alt-instrument-version.html index.html

## Deploy to GitHub Pages

1. Push this folder to your repo (main branch).
2. On GitHub: **Settings → Pages → Source: Deploy from a branch →
   main / (root) → Save**.
3. Wait ~1 minute. Live at `https://<you>.github.io/<repo>/`.

That URL is what goes behind the permanent trail QR code — deploy over it each
year and the QR never has to change.

## Important notes

- **Must be https.** Phones only share location over a secure connection, which
  GitHub Pages provides automatically. It will not work over plain http or
  inside an embedded/preview frame.
- **Test on an actual phone**, not a desktop preview — open the live Pages URL
  as a normal browser tab in Safari (iPhone) or Chrome (Android).
- **Accuracy thresholds** are constants near the top of the `<script>` block:
  `GREEN = 8` and `AMBER = 20` (meters). Tune them once you've walked the real
  trail and seen what the canopy allows.

## Not built yet

The capture step — stake number field, photo, and the payload
`{stake#, lat, lon, accuracy, photo}` that feeds the Drive → map pipeline.
This page ends right at its doorstep.
