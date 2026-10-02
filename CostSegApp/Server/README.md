# Brad's Cost Segregation Studies

This folder contains the Node server and a ready-to-serve browser app. It has no npm dependencies and needs Node 22.5 or newer (for the built-in SQLite module).

## Run locally

```sh
cd Server
SECURE_COOKIES=0 node server.js
```

Then open http://localhost:8080. The first account registered becomes the owner. Local HTTP mode is for your own computer only; use HTTPS in deployment and omit `SECURE_COOKIES=0`.

The app is static files in `public/`; no separate build step is needed. The calculation engine, catalog, validation helpers, and report generator are served as browser modules from that folder. Data is stored under `Server/data/` by default. Set `DATA_DIR` to choose another location.

## Features

- Account registration and sign-in
- Studies saved to SQLite through the API
- Property overview and depreciable basis entry
- Manual asset takeoff with RS Means catalog lookup
- Preliminary cost segregation calculations
- Printable report in a new browser tab
- Versioned study saves and backup utility

The front end included here is a restored, compact interface because the original `cost-seg-app.jsx` named by the old handover was missing from the supplied folder and archive. Sitemap measurement, RS Means spreadsheet import, and the original multi-tab editor are not included.

## Backup

```sh
node backup.js
```

Backups are written to `Server/backups/` by default. For deployment, place the app behind an HTTPS reverse proxy and keep an off-machine copy of backups. Do not expose the HTTP port directly to the public internet.
