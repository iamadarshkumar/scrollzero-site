# scrollzero-site

Public files for the ScrollZero app, served with GitHub Pages.

## `config.json`: remote config (kill switches)

Served at `https://iamadarshkumar.github.io/scrollzero-site/config.json`. The app reads it on launch,
and again when it returns to the foreground after 15+ minutes.

**Pause a broken shield:** edit `config.json` (✏️ on GitHub) and commit:

```json
{
  "schemaVersion": 1,
  "pause": { "instagram": ["storyAdSkip"] }
}
```

Names you can pause (exact spelling; several allowed):
`hideExplore`, `hideAds`, `storyAdSkip`, `fitStoryPhotos`, `catchupTab`, `singleReel`.

**Resume:** remove the name (or set `"pause": {}`) and commit.

Optional fields: `"minAppVersion": "1.0.1"` (asks older builds to update) and
`"message": { "id": "unique-id", "text": "Short note shown on the home screen" }`.

Changes go live within a minute or two; phones may keep a fetched copy for up to 10 minutes.
Check what users get by opening the URL above.

Rules:
- Data only. Never put scripts or secrets here: this repo is public.
- Keep `"schemaVersion": 1`. Without it the app ignores the whole file.
- The Reels feed block can't be paused, by design.

The full format and runbook live in the app repo, in `docs/remote-config.md`.
