# My Development — home screen wrapper

One static page whose only job is to give the Stanford Wrestling athlete app an icon when a
wrestler adds it to his home screen.

The app itself is a Google Apps Script web app. Apps Script serves it inside Google's own
wrapper document, so our HTML is the iframe and never the top-level page — and iOS reads the
home screen icon from the top-level document only. `HtmlService` strips `<link>` tags out of
the served file and offers no `apple-touch-icon` method, so there is nowhere inside the Apps
Script project to put an icon.

This page is the top-level document we control. It carries the icons and the manifest and
frames the real app full-bleed. Wrestlers add *this* URL to their home screen.

- `index.html` — the frame, plus the safe-area padding the framed app cannot do for itself
- `manifest.webmanifest` — Android / Chrome install metadata
- `icons/` — 180 (iOS), 192, 512, 512 maskable, 32 favicon

Nothing here holds any wrestler data. The app, the roster, and the notes all live in the
Apps Script project and its sheet.
