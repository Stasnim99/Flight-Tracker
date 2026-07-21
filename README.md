# Chicago Aircraft Tracker

A small side project: a live map that shows aircraft currently flying over the
greater Chicago area, with rotating plane icons, click-for-details popups, and
a hover glossary for anyone who isn't familiar with aviation terms like
"squawk" or "ICAO24."

Built mostly as a way to get hands-on with mapping libraries and a live public
API outside of my usual analytics/BI stack. It can be accessed here: https://stasnim99.github.io/Flight-Tracker/

## Features

- Live aircraft positions plotted on an interactive map (pan/zoom supported)
- Plane icons rotate to match each aircraft's actual heading
- Click a plane for its callsign, squawk code, altitude, and speed
- Hover glossary explaining callsign / ICAO24 / heading in plain English
- Auto-refreshes every hour

## Tech

- [Leaflet](https://leafletjs.com/) for the map itself
- [OpenStreetMap](https://www.openstreetmap.org/) tiles
- [AirLabs](https://airlabs.co/) for live flight data
- Plain HTML/CSS/JS - no build step, no framework

## Running it locally

It's a single static `index.html` file, so there's nothing to install - just
open it in a browser. You will need your own free AirLabs API key
(1,000 requests/month on the free tier) dropped into the `AIRLABS_API_KEY`
constant near the top of the `<script>` block.

## Notes

- `local-proxy.js` is a leftover from an earlier version of this project that
  pulled data from OpenSky instead of AirLabs. OpenSky only allows CORS from
  its own domain, so that version needed a small local Node proxy to get
  around browser restrictions. AirLabs allows CORS from anywhere, so the
  current version calls it directly and the proxy isn't needed anymore -
  keeping the file around for now in case I revisit OpenSky later.
- The free AirLabs tier is capped at 1,000 calls/month, which is part of why
  this refreshes hourly instead of, say, every 30 seconds.

## Credits

Flight data from [AirLabs](https://airlabs.co/). Map tiles &copy;
[OpenStreetMap](https://www.openstreetmap.org/copyright) contributors.
