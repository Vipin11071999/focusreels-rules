# focusreels-rules

Signed detection rules for the FocusReels Android app. Data only (no code, no user data), served by GitHub Pages.

| Path | What |
|---|---|
| `stable/rules.json` + `stable/rules.json.sig` | What the app downloads: `https://vipin11071999.github.io/focusreels-rules/stable/` |
| `beta/` | The owner's check before promotion. No app reads it. |
| `archive/v<N>/` | Every promoted version, unchanged. |

- `rules.json.sig` holds `{"keyId", "signature"}`: an Ed25519 signature over the exact `rules.json` bytes. The app verifies it against public keys built into the app, so a file changed here (or in transit) is refused.
- Versions only go up. The app refuses a lower `version` than it already has, so a rollback is a new, higher version with the old content.
- Files are written by the `rules.yml` workflow in the app repo after an approval. Don't edit them by hand.
- Format: `rules/schema.json` and ADR 0011 in the app repo.
