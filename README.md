# tap-scripts

Site scripts for [tap](https://github.com/vaayne/tap) — 106 scripts across 47 sites.

## Structure

```
sites/
  {site}/
    {action}.js
```

Each `.js` file contains a `@meta` block with metadata (name, description, domain, args) and an async function that runs against the site.

## How it works

On every push to `main` that changes `sites/**`, a GitHub Actions workflow syncs all scripts to the [tap web app](https://tap.vaayne.com) via `POST /api/batch`.

The tap CLI caches these scripts locally at `~/.cache/tap/sites/` (refreshed every 24h).

## Adding a script

1. Create `sites/{site}/{action}.js`
2. Include a `@meta` block (see existing scripts for examples)
3. Push to `main` — scripts auto-sync to production

## License

MIT
