# Region / Area / County Map

An interactive Google Maps viewer for ham radio repeater coverage areas.
Loads a CSV (exported from a companion CHIRP tool -- see
[region_picker](../region_picker)) and colors US counties by which "area"
and "region" they belong to.

## Features

- Click a region or area in the sidebar to highlight and zoom to it
- **Find My Location** -- uses your browser's GPS to detect which
  area/region you're currently standing in, via real point-in-polygon
  matching against county boundaries
- Plots individual repeater locations as map markers when GPS data is
  available in the CSV
- Save multiple CSV datasets locally in your browser and switch between
  them without re-uploading
- Mobile-friendly -- collapsible sidebar drawer, touch-optimized controls

## Usage

Open `index.html` in a browser (or visit the hosted GitHub Pages link),
click **Choose File**, and load a CSV with either:

- Simple format: `county, state, area, region, color` columns, or
- A combined CHIRP export with `Area`/`Region`/`Color`/`Comment` (and
  optionally `Lat`/`Lon`) columns -- exactly what
  [region_picker.py](../region_picker) exports

## Setup for your own use

You'll need your own **Google Maps JavaScript API key** (free tier is
generous for personal use) -- replace `YOUR_API_KEY_HERE` in `index.html`
with your key from the
[Google Cloud Console](https://console.cloud.google.com/).

**Restrict your key** under Credentials -> your key -> Application
restrictions -> HTTP referrers, listing the domain you host this on.
This is standard practice for any client-side Google Maps key, since
it's visible in the page source to anyone who looks.

**Note on Find My Location:** browsers only allow geolocation over
HTTPS (or `localhost`) -- it won't work from a plain local file, so
this needs to be hosted somewhere with a real HTTPS address (GitHub
Pages works fine for this).

## Companion project

Counties are colored using data exported from
[region_picker.py](../region_picker), a custom CHIRP repeater-lookup
tool. The two are designed to work together but the map app itself
only needs a properly formatted CSV -- it doesn't depend on CHIRP or
Python at all.
