# Arena Admin V4.2.1 — Card Intake Prototype

Single-file static prototype. Purchase order through release, including the phone
scan app emulator.

## Layout

```
arena-demo/
  public/index.html   the whole prototype, ~1.8 MB, images inlined as base64
  vercel.json         static config + cache headers
  package.json        local dev script only, nothing to build
```

No framework, no build step, no dependencies. Vercel serves `public/` as-is.

## Deploy

**CLI, fastest**

```bash
cd arena-demo
npx vercel          # preview URL
npx vercel --prod   # production
```

First run asks: link to existing project or create new, scope, and directory —
accept the defaults. Framework preset is **Other**, output directory `public`.

**Dashboard**

1. Push the folder to a Git repo.
2. vercel.com → Add New → Project → import the repo.
3. Framework Preset **Other**, Output Directory `public`, no build command.
4. Deploy.

## Local check

```bash
npm run dev     # http://localhost:3000
```

Or just open `public/index.html` — it has no server dependencies.

## Notes

- Everything lives in one HTML file: markup, CSS, JS, and every scan and label
  image as inlined base64. That keeps it portable but makes the file big, so the
  first load pulls ~1.8 MB. Vercel gzips it on the way out.
- No API calls, no storage, no env vars. State resets on refresh.
- Clicking the **ARENA** mark in the nav returns to the landing page and resets
  the run.

## Updating

Replace `public/index.html` with the newer export and redeploy. Nothing else
changes.
