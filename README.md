# Iron Log

Personal gym tracker for a 3×/week full-body bulk programme.

Tap to log sets, rest timer between sets, editable working weights, calendar
export of training days. Finishing a session posts it to a Cloudflare Worker,
which stores it in KV and relays it to Telegram.

## Where it actually runs

The app is **served by the Worker**, behind a passphrase login — not from
GitHub Pages. This repo is the source of truth for the page; the Worker embeds
it at deploy time (`src/app.js` is generated from `index.html`).

Serving it from the Worker means one origin, one credential, and **no secret in
client-side JavaScript** — the session cookie is httpOnly, so page scripts
cannot read it.

Worker source lives in the owner's private notes repo, not here.
