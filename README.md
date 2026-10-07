# Arm Split

A tiny offline web app for a 3-day dumbbell arm split.

- Shows today's day (Biceps → Triceps → Forearms → repeat) and its two exercises.
- Enter weight (kg) and reps for each of the 3 sets; last session's numbers show as a hint and as greyed placeholders.
- **Mark complete** saves the sets to the log and moves to the next day (with Undo).
- **Rest timer** – tap the floating button: counts down 60s, beeps/vibrates, then counts up (`+0:15`) so you can stretch to 90s. Tap again to reset. Keeps the screen awake while running.
- Half-entered workouts survive closing the app.
- **Export log (CSV)** – every set ever logged: `date, day, exercise, set, weight_kg, reps`.
- **Back up / Restore** – full JSON snapshot of the app's data.

No build step, no server, no account. Data lives in your browser's local storage on the device.

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

Back up occasionally – clearing site data or deleting the home-screen app wipes it.
