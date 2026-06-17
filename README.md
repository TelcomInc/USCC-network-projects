# USC As-Built Workspace

Static prototype for a Telcom Inc closeout portal used to produce low-voltage AS BUILT and project closing documents.

## Current Prototype

- Plain HTML/CSS/JavaScript deployable to GitHub Pages or Cloudflare Pages.
- Project intake form with CSV device-list import.
- Client-specific column picker for device schedules.
- Building plan image upload preview.
- Assisted automatic symbol placement workflow mockup.
- Packet manifest export for AS BUILT package generation.
- Existing Strom Thurmond interactive floor map retained as `strom_thurmond_map.html`.

## Important Security Note

This repository used to include client-side usernames and passwords. Those were removed because static-site credentials are visible to anyone who can load or inspect the site source.

Before client data, plans, test results, serial numbers, MAC addresses, warranty documents, or generated packets are uploaded, protect the deployment with Cloudflare Access or a real backend authentication layer.

## Cloudflare Pages Deployment

Recommended first deployment:

1. Cloudflare dashboard -> Workers & Pages -> Create application -> Pages -> Connect to Git.
2. Select `TelcomInc/USC-network-projects`.
3. Production branch: `main`.
4. Build command: leave blank.
5. Build output directory: `/`.
6. Add a Cloudflare Access application in front of the Pages hostname.

The included `_headers` file adds baseline browser security headers for Cloudflare Pages.

## Production Architecture Target

The finished product should move project data out of browser storage and into durable backend services:

- Cloudflare Pages: frontend app.
- Cloudflare Access: user/client authentication.
- Cloudflare Workers: API, imports, packet generation coordination.
- Cloudflare D1 or external SQL: clients, projects, devices, templates, packet runs, approvals.
- Cloudflare R2: plans, workbooks, cable test files, warranty documents, generated packets.
- Queue or processing service: PDF rasterization, OCR, legend extraction, symbol matching, and packet rendering.

See `docs/cloudflare-migration.md` for the implementation path.

## Files

- `index.html` - Main workspace prototype.
- `strom_thurmond_map.html` - Existing interactive floor map.
- `_headers` - Cloudflare Pages security headers.
- `_config.yml` - GitHub Pages compatibility config.
- `docs/cloudflare-migration.md` - migration and product architecture notes.
