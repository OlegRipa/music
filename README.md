# Pocket Lab

A single-page mobile playground, served from GitHub Pages. Open it on a phone and it will
show you what the browser knows about the device, react to tilt, draw multi-touch trails,
and buzz on demand.

Everything lives in `index.html` — no build step, no dependencies.

## What's in it

- **Tilt** — a ball driven by `deviceorientation` (with the iOS 13+ permission prompt handled).
- **Multi-touch** — a pointer-events canvas that tracks several fingers at once and picks up
  stylus pressure where the browser reports it. Double-tap to clear.
- **This device** — live viewport, screen, pixel-ratio, touch-point and orientation readouts.
- **Buttons** — vibration, fullscreen, and a light/dark theme toggle.
- Safe-area insets, `100svh`, dark mode, reduced-motion support, and a web app manifest so
  "Add to Home Screen" launches it standalone.

## Publishing it

Two ways; pick one.

> **Enable Pages first.** Until someone turns Pages on in the repo settings, the workflow
> fails with `Get Pages site failed … Not Found`. The workflow cannot enable it for you —
> creating a Pages site is not something `GITHUB_TOKEN` is permitted to do. Note also that
> Pages on a **private** repo requires a paid plan; on the free plan the repo has to be
> public.

### GitHub Actions (already wired up)

`.github/workflows/pages.yml` deploys the repo root on every push to `main` or to the
`claude/github-pages-mobile-test-djt7ug` branch.

1. Repo **Settings → Pages → Build and deployment → Source: GitHub Actions**.
2. Re-run the workflow (or push). The run posts the live URL on its `deploy` job.

### Deploy from a branch

1. Repo **Settings → Pages → Source: Deploy from a branch**.
2. Pick the branch and the `/ (root)` folder, then save.

Either way the site lands at `https://<user>.github.io/<repo>/` within a minute or two.

## Running it locally

```sh
python3 -m http.server 8000
```

Then open `http://<your-computer-ip>:8000` on a phone on the same Wi-Fi. Note that tilt and
some other sensor APIs require HTTPS in most browsers, so the deployed Pages URL is the
honest test.
