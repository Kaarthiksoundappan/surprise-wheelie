# surprise-wheelie

A spinning wheel site that collects clothing "buy links" from different websites and
turns picking an outfit into a game. The wheel page never shows the links — they're
only revealed after the wheel stops.

## Pages

| URL | Who it's for |
|---|---|
| `https://kaarthiksoundappan.github.io/surprise-wheelie/` | Public — spin the wheel, no links visible |
| `https://kaarthiksoundappan.github.io/surprise-wheelie/admin.html` | You only — add/edit outfits with buy links, PIN protected |

## How it works

```
admin.html  ──write──▶  Firebase Firestore  ◀──read──  index.html
(PIN locked)             (cloud database)              (public wheel)
```

Outfit data lives in Firebase, so the wheel updates instantly when you add an outfit —
no redeploy needed.

## Setup

See [SETUP.md](SETUP.md) for the full walkthrough. Short version:

1. Create a Firebase project + enable Firestore.
2. Paste your Firebase web config into the marked block in **both** `index.html` and `admin.html`.
3. Enable GitHub Pages: repo **Settings → Pages → Source: `main` / root**.
4. Open `admin.html`, enter your PIN, add outfits.

`firestore.rules` is included for reference — the default rules allow public
read **and** write, which is fine for a personal project but not secure. Tighten
them with Firebase Auth if you want.
