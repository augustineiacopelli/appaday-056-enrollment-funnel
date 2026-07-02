# AppADay 056 — Enrollment Funnel

Part of [AppADay](https://augustineiacopelli.github.io/appaday/), a personal challenge to design, build, and publish one complete, functional, mobile-friendly web app every day.

**Live app:** https://augustineiacopelli.github.io/appaday-056-enrollment-funnel/

## What it does

Enrollment Funnel visualizes any multi-stage pipeline as a proportional funnel chart. Enter a count for each stage and the funnel narrows to scale, with the conversion rate between every pair of stages computed live and shown alongside the stage name in a lane to the right of the chart. An overall yield stat strip below the chart summarizes total conversion, total lost, and the final stage's count.

The number of stages is fully customizable from 2 to 8 through a settings gear in the header, where each stage can also be renamed. Data can be populated by hand in the ledger panel, pasted in bulk through an Import Data dialog as `Name, Count` per line, or reset to a sample four-stage admissions funnel. The finished chart can be exported as a standalone JPG image with one tap.

## Design

Styled to Wichita State University brand standards: near-black background, Shocker Yellow (`#FFDB00`) as the sole accent, Titillium Web for display type, and Georgia italic for the descriptive tagline, without any WSU branding elements (no logo, no institutional name) actually applied to the page itself. The funnel's own color gradient runs from a dark chrome tone at the top stage to full Shocker Yellow at the final stage, with each segment's text color chosen for contrast against its own fill rather than a fixed value.

## How it's built

Single-file vanilla HTML, CSS, and JavaScript. No frameworks, no build step, no external libraries. The funnel is hand-drawn SVG, sized and colored procedurally based on however many stages are configured. Segment widths are computed as the greater of a value's proportional share and the actual measured width of that segment's own number, so a large number can never overflow onto the page background and lose contrast. Stage data, including custom stage counts and names, persists to `localStorage`. JPG export clones the live SVG, inlines the styling that otherwise lives in the page stylesheet, rasterizes it to a canvas at 2x scale against a solid background, and triggers a same-page download, all without any external rendering library.

Fully responsive from a 375px mobile viewport up through desktop.
