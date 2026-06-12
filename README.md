# Wingfoiling forecast dashboard — near Zürich

A single-page wind dashboard for beginner wingfoiling at 13 spots around Zürich, central Switzerland, and the northern Italian lakes (Lago Maggiore, Lago di Como). It scores each spot's chance of a rideable session (beginner target: **≥ 12 kn consistent**), shows live "now" conditions, and cross-checks the forecast against real ground stations and webcams.

The whole thing is **one self-contained `index.html` file** with no build step and no backend — all data is fetched live in the browser, so it stays current wherever it's hosted.

## What it shows

- **Synoptic context** — live Föhn (Δp Lugano − Zürich) and Bise (Δp Geneva − Güttingen) charts computed from sea-level pressure, including today, with a "now" marker.
- **Macro-pattern ground validators** — live MeteoSwiss stations (Payerne/Wynau/Güttingen for Bise; Altdorf/Vaduz/Glarus for South Föhn) that confirm whether the synoptic pattern has actually materialised on the ground.
- **Today now — verify before you drive** — per-spot current wind in knots from the nearest live anemometer (or the model, clearly labelled), a rideability badge, and a dynamic marker for the most relevant (downwind) station given the current wind.
- **Per-spot probability** — a 6-day go/no-go grid (green / yellow / red) with the heuristic, triangulated notes, and curated station/webcam/forecast links for each spot.

## How it works

Everything runs client-side. On load the page calls:

- **[Open-Meteo](https://open-meteo.com/)** (ICON-D2 / AROME) for the 6-day forecast and the reference-city pressures that drive the Föhn/Bise indices.
- **[Existenz.ch](https://api.existenz.ch/)** for live MeteoSwiss SwissMetNet station readings.
- **[tecdottir](https://tecdottir.metaodi.ch/)** for the Zürich Wasserschutzpolizei lake stations (Mythenquai).
- **[Holfuy](https://holfuy.com/)** for the Isleten (Urnersee) live station.

No API keys, no server. Refreshing the page (or the **Refresh forecast** button) pulls fresh data.

## Run it

- **Locally:** just open `index.html` in any modern browser.
- **Hosted (GitHub Pages):** put `index.html` at the root of a public repo, then enable **Settings → Pages → Deploy from a branch → `main` / root**. The site appears at `https://YOUR-USERNAME.github.io/REPO-NAME/`. Because all data is fetched in the visitor's browser, the hosted page is always live with no server of yours running.

## Data & attribution

The license below covers **this dashboard's code only**. The weather data it displays belongs to its providers and remains under their terms:

- **Open-Meteo** — forecast/model data, licensed **CC BY 4.0**.
- **MeteoSwiss / SwissMetNet** (via the Existenz.ch API) — © MeteoSwiss; **free for public, non-commercial use**, MeteoSwiss credited as the source.
- **Stadt Zürich Wasserschutzpolizei** lake stations — via the tecdottir open-data API.
- **Holfuy** — live-station network.

All other stations, webcams and forecasts in the dashboard (Windguru, Windfinder, Wunderground, BrevaGuru, sailing-club and school pages) are **linked out** to their operators — their data is not redistributed here.

Please keep these attributions in place, and note that the data's non-commercial terms (MeteoSwiss/Existenz) still apply to anyone reusing the *data*, independent of this project's code license.

## Disclaimer

This is a **personal planning aid, not a safety service**. Forecasts and even live readings can be wrong, and several spots have real hazards (gusty Föhn, severe lee effects, cold water, nature-reserve restrictions). Always assess conditions on site, respect local zoning and access rules, and use appropriate safety gear.

## License

Code © 2026 TY, released under the [MIT License](LICENSE). See `LICENSE` for the full text.
