# USC Network Projects Portal

GitHub Pages site for University of South Carolina network infrastructure projects, managed by Telcom Inc.

## Setup

1. Create a new GitHub repository (e.g. `usc-network-projects`)
2. Upload ALL files in this folder to the repository root
3. Go to **Settings → Pages → Branch: main → / (root)** and save
4. Your site will be live at `https://yourusername.github.io/usc-network-projects/`
5. To use a custom domain, add it in Settings → Pages → Custom Domain

## Files

- `index.html` – Login portal + project dashboard
- `strom_thurmond_map.html` – Strom Thurmond interactive floor map (copy from outputs folder)
- `_config.yml` – GitHub Pages config (disables Jekyll)

## Credentials

Default logins (edit in `index.html` under the `USERS` object):
- `ryan` / `telcom2025`
- `admin` / `usc2025`

> Note: These are client-side only credentials suitable for a private/internal tool.
> For higher security, add GitHub's built-in repository access controls.

## Adding Future Projects

1. Add the new project's HTML file to the repo
2. Add a new entry to the `USERS` object in `index.html` if needed  
3. Add a new project card in `index.html` (copy the Strom Thurmond card block)
4. Update the stats row numbers

