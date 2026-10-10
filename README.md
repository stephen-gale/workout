# Arm Split

A tiny offline web app for a 2-day dumbbell arm split, with forearm work (wrist curl + reverse curl) supersetted every day.

- Shows today's day (Biceps → Triceps → repeat) as two supersets: main lift + wrist curl (palms up), then main lift + reverse curl (palms down).
- Enter kg and reps for each set (weight can change between sets). Last session's numbers show as greyed placeholders – tap a box to type the real value.
- **Mark complete** saves the sets to the log and moves to the next day (with Undo).
- **Rest timer** – tap the floating button: counts down 60s, beeps/vibrates, then counts up (`+0:15`) so you can stretch to 90s. Tap again to reset. Keeps the screen awake while running.
- Half-entered workouts survive closing the app.
- **Export log (CSV)** – every set ever logged: `date, day, exercise, set, weight_kg, reps`.
- **Back up / Restore** – full JSON snapshot of the app's data.

No build step, no server. Data lives on the phone and, once **GitHub sync** is set up, is also committed to `data/log.json` in this repo after every completed day, so clearing the browser loses nothing.

## GitHub sync setup (once)

1. github.com → Settings → Developer settings → Personal access tokens → **Fine-grained tokens** → Generate new token.
2. Repository access: **Only select repositories** → `workout`. Permissions → Repository → **Contents: Read and write**. Pick a long expiry.
3. In the app, tap **GitHub sync** at the bottom and paste the token.

After clearing the browser, tap **GitHub sync** and paste the token again: the log and current day come back from the repo. If a save fails (no signal), it retries next time the app is opened.

## Install on your phone

1. Repo **Settings → Pages → Deploy from a branch**, pick the branch and `/ (root)`.
2. Open the Pages URL on your phone.
3. iPhone: Share → *Add to Home Screen*. Android: menu → *Install app*.

## Data

Stored in `localStorage` under `armsplit:v1`:

```json
{ "day": 0, "log": [{ "date": "2026-10-07T18:00:00.000Z", "day": "Biceps",
  "exercise": "Hammer curl", "set": 1, "weight": 10, "reps": 12 }], "draft": {} }
```

Without GitHub sync, back up occasionally – clearing site data wipes it.
