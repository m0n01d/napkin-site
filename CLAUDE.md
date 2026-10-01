# napkin-site (snapkin.tools)

The Snapkin marketing site, live at https://snapkin.tools. The app is a separate repo and a separate
origin: `m0n01d/caliper-companion` → https://app.snapkin.tools. Never move the app's domain: each
tester's parts live in that origin's browser storage.

## Shared conventions

Workspace-wide conventions live in the private repo `m0n01d/claude-conventions`. On the Mac they
auto-load via `~/code/CLAUDE.md`. A cloud sandbox does not see them, so fetch them before you work:

```sh
git clone https://github.com/m0n01d/claude-conventions /tmp/conventions && cat /tmp/conventions/CLAUDE.md
```

If the clone fails, continue with this file.

## Rules

- **Static only.** HTML, one CSS file, SVG, images, the video. No JavaScript, no build step, no
  dependencies. If a feature ever needs script, ask first. Per the conventions, web code is ReScript.
- **A push to `main` publishes.** Pages deploys from the branch, and there is no CI. Verify before
  you push.
- **Do not edit or delete `CNAME` or `.nojekyll`.** `CNAME` holds the custom domain.
- **Absolute URLs stay on the domain.** `og:url`, `og:image` and `canonical` name
  `https://snapkin.tools/`. `404.html` uses root paths, because Pages serves it at any depth.
- **Brand.** Follow `docs/brand/README.md` in `caliper-companion`. Ivory means tap, blue means
  measured, red means wrong. Space Grotesk 600 is for headlines only. Body text uses the system
  stack. Add no new colours or fonts.
- **Claims match the app.** Check the app's code before the page states a feature. The phone on the
  page is a static mock of the app's Annotate screen, so update it when Annotate changes a lot.

## Verify before a push

```sh
python3 -m http.server 8080
```

Render `http://localhost:8080/` at 1440 × 900 and 390 × 844. Check for no horizontal overflow, no
failed requests, and that the Space Grotesk font loads. Render `/404.html` too.

## Pull requests

The conventions' PR rules apply: screenshots on every change that shows on the page. This repo
publishes from `main`, so open a PR when the owner wants to review a change before it goes live.
