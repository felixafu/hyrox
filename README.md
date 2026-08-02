# Hyrox London 2026 · Training App

Single-file web app for the 18-week Doubles plan. No backend, no build step, no dependencies. Just `index.html`.

---

## Deploy to GitHub Pages (about 2 minutes)

1. Go to [github.com/new](https://github.com/new). Name it `hyrox`. Set it to **Public** and create it.
   *(Pages on a private repo needs a paid plan. There is nothing sensitive in here.)*
2. On the empty repo page click **uploading an existing file**, drag in `index.html`, then **Commit changes**.
3. Go to **Settings → Pages**. Under *Source* pick **Deploy from a branch**, set branch to `main` and folder to `/ (root)`, then **Save**.
4. Wait about a minute. Your app is live at:
   ```
   https://<your-username>.github.io/hyrox/
   ```

**To update it later:** open `index.html` in the repo, click the pencil icon, paste new content, commit. Live within a minute.

---

## Add to your phone home screen

**iPhone (Safari):** open the URL → Share button → *Add to Home Screen*.
**Android (Chrome):** open the URL → three dots → *Add to Home screen*.

It launches full screen with no browser chrome, so it behaves like a normal app.

---

## How it works

| Tab | What it does |
|---|---|
| **Today** | Auto-detects the date and shows that day's session with full detail. One tap to complete. |
| **Week** | Seven-day strip. Tap any day to see its session. Green dot means done. |
| **Plan** | All 18 weeks, collapsed. Tap to expand. |
| **Stats** | Adherence, streaks, completion split by session type and by phase. |

Completed sessions get a free-text box for splits, loads and how it felt, so the app doubles as a training log.

---

## Important: where your data lives

Ticks and notes are saved in **your browser's local storage on that one device**. That means:

- It survives closing the app, restarting your phone, and losing signal.
- It does **not** sync between your phone and laptop. They keep separate records.
- Clearing browser data, or "Clear History and Website Data" on iOS, wipes it.
- Private/incognito browsing will not save anything.

**Use the Export backup button in Stats every few weeks.** It downloads a small JSON file. *Restore* reads it back on any device.

If cross-device sync matters to you, that is the one thing that genuinely needs a server, and Railway would be the right tool for it. It would mean adding a small database and a login. Worth it only if you actually want to log from two devices.

---

## Editing the plan

All programming lives in the `W` array near the top of the `<script>` block. Each week looks like this:

```js
{n:5, ph:'Build', km:25,
 wed:{t:'4 x 800m @ 5K pace', s:'90s jog recovery', b:['bullet','bullet'], c:'coaching note'},
 sat:{t:'Easy Z2 run', s:'40min'},
 sun:{t:'Compromised running', s:'4 rounds: 1km + station', b:[...], c:'...'}}
```

- `t` title, `s` subtitle, `b` bullet list, `c` italic coaching note
- `km` weekly run volume target, `dl:1` marks a deload week
- Strength days come from the `PUSH`, `PULL` and `lower()` templates just above `W`

Change a number, commit, done. The schedule, dates and stats all recalculate themselves.

---

## Key dates baked in

- **Plan starts:** Monday 3 August 2026
- **5K time trial:** Wednesday 19 August 2026 (sets all your pace targets)
- **First full doubles sim:** Sunday 8 November 2026
- **Dress rehearsal sim:** Sunday 15 November 2026
- **Race:** Wednesday 2 December 2026, ExCeL London
