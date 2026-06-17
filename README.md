# ♡ payments-tracker ♡

A soft, pastel finance tracker for monthly payments — sync across your laptop, phone, and tablet, secured by a personal password.

Built as a single HTML file. No build step, no install, no fuss.

## ✨ Features

- Track payments to multiple payees, each with multiple items
- Per-owner totals (Primary / Secondary / Combined) per month
- Automatic month blocks based on each item's end date
- Auto-collapses paid months · grand total summary panel
- Live sync across devices via Firebase Realtime Database
- Password-locked: your data lives at a SHA-256 hashed path, unreachable without it
- Anonymous Firebase auth — no email, no account, no tracking

## 🌸 Try it

**Blank template:** [open the live demo →](https://camachoj-ds-exp.github.io/t/payments-blank.html)

Set it up with your own Firebase project and password in about 5 minutes. Your data stays in *your* Firebase, completely separate from anyone else's.

## 🛠 Setup (one-time per person)

1. Open the blank template link above
2. Create a free [Firebase project](https://console.firebase.google.com) → add a Web App → enable **Realtime Database** (start in test mode) → enable **Anonymous Authentication**
3. In the tracker, tap **⚙** → paste your `firebaseConfig` → pick a password → **Save & Connect**
4. Repeat step 3 on every device you want to sync (same config + same password)
5. (Recommended) Lock down your database — Firebase Console → Realtime Database → Rules:

   ```json
   {
     "rules": {
       "payments": {
         "$ws": {
           ".read": "auth != null && $ws.length >= 16",
           ".write": "auth != null && $ws.length >= 16"
         }
       }
     }
   }
   ```

## 🎨 Theme

Soft cream, baby pink, baby blue, lilac. Designed to feel calm — money shouldn't feel stressful.

## 🔒 What's actually in this repo

The HTML is just the interface. None of the following are stored here:

- Your Firebase config (lives in your browser's localStorage)
- Your password (also localStorage only — never sent anywhere)
- Your actual figures (in your private Firebase, behind auth + hash)

The repo is public so the template can be shared, but every user's data is fully isolated in their own Firebase project.

---

Made with ♡
