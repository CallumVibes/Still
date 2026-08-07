# Still

A quiet place to steady yourself during panic and anxiety.

Still is a small, offline-first web app (PWA) built for the moments when you can barely
read a screen, let alone navigate one. The "in the moment" flow is one tap from launch,
low-text, and calm by design. All your data stays on your own device.

---

## What it does

**In the moment**
- **Breathing** — a slow expanding/contracting orb guides your breath, with four techniques:
  Long exhale, Box (4·4·4·4), 4·7·8, and the Physiological sigh. Mark any one as your
  **default** (★) and it opens automatically every time.
- **Grounding** — the 5-4-3-2-1 senses exercise, one prompt at a time, tap to advance.

**Ongoing**
- **Check in** — log how you feel on a 0–10 scale with an optional note.
- **Thought record** — a gentle CBT walk-through: situation → thought → evidence for →
  evidence against → a more balanced view.
- **History** — a trend line of your check-ins over time, plus past entries and thought records.

**Throughout**
- Twilight palette with soft, slowly drifting background glows — dim on purpose, so it
  doesn't wind you up further and works fine at night.
- Respects your device's reduced-motion setting.
- A discreet **"In crisis?"** panel with signposting to real help.

---

## Files

| File | Purpose |
|------|---------|
| `index.html` | The whole app — HTML, CSS, and JS in one file. No build step, no dependencies. |
| `manifest.webmanifest` | PWA metadata (name, icons, colours, standalone display). |
| `sw.js` | Service worker — caches the app so it launches offline. |
| `icon-192.png`, `icon-512.png` | Home-screen icons. |
| `icon-maskable-512.png` | Maskable icon for Android adaptive shapes. |
| `apple-touch-icon.png` | Home-screen icon for iOS. |

---

## Running it

The app **must be served over HTTPS or `localhost`** — a PWA won't install or cache from a
`file://` path. Double-clicking `index.html` runs the app but skips the service worker and
"Add to Home Screen".

**Test locally**
```bash
cd still
python3 -m http.server
# then open http://localhost:8000
```
On `localhost` the service worker registers, so you can confirm offline caching in your
browser's DevTools (Application → Service Workers).

**Put it on your phone**
1. Deploy the folder — the quickest no-account option is dragging it onto
   <https://app.netlify.com/drop>, which returns an HTTPS link in seconds. GitHub Pages,
   Cloudflare Pages, or any static host work too.
2. Open the link on your phone → browser menu → **Add to Home Screen**.
3. Launch from the icon. It opens full-screen and works with no signal.

---

## Your data & privacy

Everything you enter — check-ins, notes, thought records, your default technique — is stored
locally in your browser via `localStorage`. Nothing is sent anywhere; there is no account,
server, or analytics. Clearing your browser/site data, or uninstalling the app, removes it.

---

## Customising

- **Crisis numbers** — the defaults in the "In crisis?" panel are UK (Samaritans `116 123`,
  SHOUT text `85258`, emergency `999`). **Edit these for your region** in `index.html` before
  sharing the app with anyone. Search for `In crisis` in the file.
- **After any change, bump the cache** — change `CACHE = 'still-v1'` to `'still-v2'` in `sw.js`,
  otherwise the old cached version keeps loading.
- **Breathing techniques** — edit the `techniques` object in `index.html` to adjust phase
  durations or add your own.
- **Colours** — all defined as CSS variables in the `:root` block at the top of `index.html`.

---

## A note on what this is

Still is a self-help tool, **not a medical device and not a substitute for professional care,
diagnosis, or crisis support.** It can help you ride out a hard moment; it can't replace a
doctor, a therapist, or a trained person on the end of a phone. If you're struggling
regularly, or ever thinking about harming yourself, please reach out to a professional or one
of the services in the crisis panel.

---

## License

Not yet specified — add one if you plan to share or open-source it (e.g. MIT for permissive
reuse). Until then, all rights reserved by the author.
