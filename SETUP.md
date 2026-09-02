# Surprise Wheelie — Setup Guide

## What you'll have
| URL | Who sees it |
|---|---|
| `https://your-username.github.io/surprise-wheelie/` | Your girlfriend — spin wheel, no links visible |
| `https://your-username.github.io/surprise-wheelie/admin.html` | Only you — add/edit outfits with buy links, PIN protected |

---

## Step 1 — Create a Firebase Project

1. Go to [https://console.firebase.google.com](https://console.firebase.google.com)
2. Click **Add project** → give it a name (e.g. `surprise-wheelie`) → Continue
3. Disable Google Analytics (not needed) → **Create project**

---

## Step 2 — Enable Firestore

1. In Firebase Console, click **Firestore Database** (left sidebar)
2. Click **Create database**
3. Choose **Start in test mode** → Next
4. Pick any location → **Enable**

---

## Step 3 — Get your Firebase Config

1. In Firebase Console, click the **gear icon** → **Project settings**
2. Scroll to **Your apps** → click **</>** (Web app)
3. Register app with any name → click **Register app**
4. You'll see a code block like this — **copy all values**:

```js
const firebaseConfig = {
  apiKey: "AIza...",
  authDomain: "your-project.firebaseapp.com",
  projectId: "your-project-id",
  storageBucket: "your-project.appspot.com",
  messagingSenderId: "123456789",
  appId: "1:123...:web:abc..."
};
```

5. Open **both** `index.html` and `admin.html`
6. Find the section that says `// ── PASTE YOUR FIREBASE CONFIG HERE ──`
7. Replace the `REPLACE_WITH_YOUR_*` values with your actual values in **both files**

---

## Step 4 — Upload to GitHub Pages

1. Go to [https://github.com/new](https://github.com/new)
2. Create a repo named `surprise-wheelie` → **Public** → Create
3. Upload these files to the repo:
   - `index.html`
   - `admin.html`
   - `firestore.rules` (optional, for reference)
4. Go to repo **Settings** → **Pages**
5. Under **Source**, select `main` branch → `/root` → **Save**
6. Wait ~1 minute → your site is live at:
   `https://your-username.github.io/surprise-wheelie/`

---

## Step 5 — Add your outfits

1. Open `https://your-username.github.io/surprise-wheelie/admin.html`
2. Enter your PIN: **07092026**
3. Add outfit names + buy links — they're stored in Firebase
4. The spin wheel page updates instantly — no re-deploy needed!

---

## How it works

```
admin.html  ──write──▶  Firebase Firestore  ◀──read──  index.html
(PIN locked)              (cloud database)             (public wheel)
```

- **Buy links are never shown** on the spin page — only revealed when the wheel stops and she clicks "Reveal & Shop"
- **PIN is checked client-side** — sufficient for a fun personal project
- All outfit data lives in **Firebase**, so you can update anytime without touching code

---

## Your PIN
`07092026` — keep this safe, don't share it!
