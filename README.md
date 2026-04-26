# deutschfit-legal

Static legal pages for DeutschFit (privacy policy, terms of service, impressum,
about). Plain HTML + a single `styles.css` — no build step, no JS, no tracking.

## Live deployment

| Environment | URL                                              | Source branch |
| ----------- | ------------------------------------------------ | ------------- |
| Production  | <https://deutschfit-legal.vercel.app/index.html> | `main`        |

The production URL is what's referenced from:

- **App Store Connect** — "Privacy Policy URL" metadata field
- **Google Play Console** — "Privacy Policy URL" metadata field
- **Mobile app** — `Profile → Legal → Privacy / Terms / About / Impressum`
- **Web app** (`deutschfit-web`) — footer + `/legal/*` mirrors

The apex `deutschfit.app/legal/*` will eventually serve the same content via
the Next.js mirror in `deutschfit-web`; until that switch, the Vercel URL above
is the canonical live deployment.

## Pages

| File             | Purpose                                                                          |
| ---------------- | -------------------------------------------------------------------------------- |
| `index.html`     | Landing — links to every legal page + contact email                              |
| `privacy.html`   | GDPR Art. 13 privacy notice (controller, data, processors, retention, rights)    |
| `tos.html`       | Terms of Service (acceptance, beta status, AI disclosure, liability, governing law) |
| `impressum.html` | § 5 TMG / LCEN Art. 6 III / § 5 ECG operator disclosure                          |
| `about.html`     | App overview + version                                                           |
| `styles.css`     | Brand tokens (cream / ink / gold) + light/dark wordmark swap                     |

## Cross-repo coordination

- The user-facing prose is mirrored into `deutschfit-web` at `/legal/privacy`,
  `/legal/tos`, `/legal/about`, `/legal/impressum`. **Both surfaces must be
  updated together** — see `deutschfit-meta/docs/release/w6-store-compliance.md`
  §12 for the cross-track rule.
- Apple / Play submission metadata + App Privacy / Data safety answers live in
  `deutschfit-meta/docs/release/w6-store-compliance.md`.

## Branches

| Branch                    | Purpose                                          |
| ------------------------- | ------------------------------------------------ |
| `main`                    | Production. Auto-deploys to the Vercel URL.      |
| `chore/legal-deploy-prep` | Active polish branch — store-readiness PR queue. |

## Local preview

```bash
# any static server works; pick one:
python3 -m http.server 8000
# then open http://localhost:8000/index.html
```
