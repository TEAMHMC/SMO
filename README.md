# Street Medicine Outreach

Standalone site for Health Matters Clinic's Street Medicine Outreach program,
built to match the Unstoppable page so animation and button behaviour are
identical across HMC surfaces.

Live target: https://streetmedicine.healthmatters.clinic (GitHub Pages, see CNAME)

## Structure

    index.html                     the page
    assets/css/hmc-parallax.css    shared parallax + reveal layer
    assets/js/vendor/              GSAP, ScrollTrigger, Lenis (vendored, not CDN)
    assets/js/hmc-immersive.js     scroll layer: reveals, count-ups, parallax
    assets/js/hmc-parallax.js      lightweight layer: kinetic marquee
    assets/site/hmc-buttons-1.0.1.css  shared HMC button system
    photos/                        field photography

## Animation hooks

Driven by `hmc-immersive.js`, copied unmodified from TEAMHMC/Unstoppable:

- `[data-reveal]` scroll reveal
- `.impact-num` count-up. Only matches `^\d+%?$`, so decimals are split:
  the integer animates and the decimal tail sits in a sibling span.
- `.hmc-bg-layer` hero parallax drift
- `.hmc-kinetic-row` marquee

The immersive layer disables itself under `prefers-reduced-motion`, when GSAP
is missing, and when the page is inside an iframe. That last case matters: if
this page is ever embedded in Webflow, the animations will not run, exactly as
happens with Unstoppable.

## Buttons

Use `hmc-btn` plus `hmc-btn-primary` or `hmc-btn-secondary`, and set
`data-hmc-label` to the same text as the label. The 1.0.1 CSS builds the
roll-up from that attribute and needs no JavaScript. Do not also load
`hmc-buttons-1.0.0.js`: it wraps text nodes for the older 1.0.0 CSS and
renders every label twice against 1.0.1.

## Open items

- Report PDFs are not linked yet. Both download buttons point at `#`.
- HIV brief percentages are not published on the page. The source PDF is
  image-only, so prior-testing, age and race figures need confirming against
  the raw data before any percentage goes live. Recipient count (115) is solid.
- Confirm the contact number. The report and the hero photo shirt both show a
  213 number; the 2026 capability statement uses (323) 990-4325.
