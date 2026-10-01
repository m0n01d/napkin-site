# napkin-site

The Snapkin marketing site → **https://snapkin.tools**

The app is a separate repo and a separate domain: [`m0n01d/caliper-companion`](https://github.com/m0n01d/caliper-companion)
→ https://app.snapkin.tools. The brand kit and the design docs live there too.

- **Static:** `index.html`, `site.css`, SVG art and the demo video. No JavaScript, no build step,
  no dependencies.
- **Deploy:** GitHub Pages → *Deploy from a branch* → `main` → `/ (root)`. A push to `main` is live
  about a minute later. `CNAME` holds the custom domain and `.nojekyll` serves the files as they are.

## Preview

```sh
python3 -m http.server 8080   # then open http://localhost:8080/
```

Serve the folder from its own root, as Pages does. `404.html` uses root paths (`/site.css`).

## Files

| Path | What |
|---|---|
| `index.html` | The page: hero, how it works, the photo rule, export to Fusion, details, demo, sign-up, FAQ |
| `site.css` | All styles. The tokens mirror the app's `src/theme.css` |
| `404.html` | Served by Pages for any unknown path |
| `img/` | The napkin sketch, the hinge-pin "photos", the lockup, the demo poster |
| `fonts/` | Space Grotesk 600 (latin subset, SIL OFL 1.1, see `fonts/OFL.txt`), headlines only |
| `og.png` | The 1200 × 630 link preview |
| `snapkin-demo.mp4` | The 66 s demo recorded from the app |
| `favicon.svg`, `icon-192.png`, `apple-touch-icon.png` | The app icon |

## Domain

DNS for `snapkin.tools` is at Squarespace. Records checked on 2026-09-24:

| Type | Host | Data |
|---|---|---|
| TXT | `_github-pages-challenge-m0n01d` | The value from github.com/settings/pages → Add a domain (verifies the domain for the account) |
| A | `@` | `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153` |
| AAAA | `@` | `2606:50c0:8000::153`, `2606:50c0:8001::153`, `2606:50c0:8002::153`, `2606:50c0:8003::153` |
| CNAME | `www` | `m0n01d.github.io` (GitHub redirects www to the apex) |
| CNAME | `app` | `m0n01d.github.io` (the app, from `caliper-companion`) |

Then Settings → Pages → Custom domain `snapkin.tools`, and **Enforce HTTPS** once GitHub offers it.

## Sign-up

The beta form is disabled until a sign-up service is connected. To connect it, put the service's form
URL in the form's `action`, remove `disabled` from the submit button, and remove the `.form-note`
paragraph. The field names follow Kit (`email_address`, `fields[...]`); Formspree accepts them as they are.
