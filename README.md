# Squash VR Trainer

A solo squash training game for **Meta Quest 2** that runs in the headset's web browser (WebXR). You don't install anything: it's one HTML file, `squash-vr.html`, served by GitHub Pages.

You get a regulation 9.75 × 6.40 m court, a ball that behaves like a warm double-yellow, a ball machine with drills, and targets for nicks, boasts and deep drives.

---

## Play it on your Quest (from GitHub)

1. **Put on the headset** and clear about 2 × 2 m of floor. Keep the guardian on, because you will swing hard.
2. **Open the Browser app** (Meta Quest Browser) from the app library.
3. **Go to this address** (tap the address bar and type it):

   ```
   clavelseb.github.io/squashvr/squash-vr.html
   ```

   The page should say **"Headset ready. Put it on and press Enter VR."**
4. **Press Enter VR.** If the browser asks for permission to use VR, choose **Allow**.
5. **Play.** Press **B** (or **Y**) for the menu. Choose a drill under **Practice**, or stay in **Free play**: hold the trigger on your ball hand to hold the ball, release to toss, then hit.

Tip: bookmark the page in the Quest Browser so you don't have to type the address again.

> **Use the github.io link, not the github.com one.** The link
> `github.com/clavelseb/squashvr/blob/main/squash-vr.html` only shows the file's source code. The game itself runs from
> **clavelseb.github.io/squashvr/squash-vr.html**.

---

## One-time setup: turn on GitHub Pages

The github.io address only works once GitHub Pages is on for this repository. You only do this once.

1. On github.com, open the repository and go to **Settings → Pages**.
2. Under **Build and deployment**, set **Source** to **Deploy from a branch**.
3. Choose branch **main** and folder **/ (root)**, then press **Save**.
4. Wait a minute or two. The page then shows **"Your site is live at https://clavelseb.github.io/squashvr/"**.

GitHub Pages serves over HTTPS, which WebXR needs, so nothing else is required.

---

## Put up a new version

1. On github.com, open the repository and choose **Add file → Upload files**.
2. Drop in the new `squash-vr.html` (keep that exact name) and press **Commit changes**.
3. Wait a minute or two for Pages to publish it, then reload the page in the Quest Browser.

**Check you have the new version:** the version number is in the top-right corner of the in-game menu (for example **v1.9**).

**Still the old version?** GitHub Pages lets browsers keep a copy for up to 10 minutes. Wait a few minutes and reload, or add anything after a `?` to the address so the browser fetches it fresh:

```
clavelseb.github.io/squashvr/squash-vr.html?v=2
```

---

## Try it on a computer first (optional)

Open the same github.io link in Chrome or Edge on your computer. Without a headset, the page shows the court and says **"No VR headset detected"**. That's expected: it confirms the page loads. Playing needs the headset.

---

## Controls (right-handed; swapped when you choose left-handed in the menu)

| Ball hand (left) | |
|---|---|
| Trigger | Hold the ball, release to toss |
| X | Ball back to hand · next feed now |
| Y | Menu |
| Stick | Move around the court |
| Stick click | Replay your last hit (speed set in Ball physics) |

| Racquet hand (right) | |
|---|---|
| A | Ball back to hand · next feed now |
| B | Menu |
| Stick ◀ ▶ | Turn 30° |
| Stick ▲ ▼ | Tilt the racquet in your hand |
| Stick click | Adjust grip: grab the racquet with your other hand and set it where it feels right; the other stick moves it nearer or further |

Point at the menu with either controller and pull the trigger to press a button.

---

## What's in the menu

- **Practice:** pick a drill (Free play, Lob serve, Hard serve, Volley feed, Loose ball, Boast feed, Boast practice, Drive practice). You also set the feed side (forehand, backhand or alternate), the target, the time between feeds, the ball type and temperature, and where you stand.
- **Racquet & settings:**
  - Racquet hand and grip, and racquet tilt, lean, face angle and distance from your hand.
  - **Hit assist:** a catch zone of 3, 6 or 10 cm around the strings, and **Perfect hits**, which plays every hit from the sweet spot.
  - Display options, refresh rate (72, 90 or 120 Hz), sound and haptics.
- **Ball physics:**
  - **Values:** 18 ball and bounce settings, adjusted live. Changed values show in amber, and **Reset all** puts them back.
  - **Drop test:** the official 254 cm drop.
  - **Replays and test shots:** **Replay my last hit**, plus test shots from where you stand (drive, crosscourt, boast, lob, drop shot, kill). They play at real speed, ½× or ¼× slow motion.

Settings are saved in the Quest Browser, so they're still there the next time you open the page.

---

## If something goes wrong

| Problem | Fix |
|---|---|
| The page shows code instead of a court | You opened the github.com link. Use **clavelseb.github.io/squashvr/squash-vr.html** |
| "404 – There isn't a GitHub Pages site here" | GitHub Pages isn't on yet, or is still publishing (see *One-time setup*) |
| **Enter VR** is greyed out | Open the page in the Quest's own Browser app, from the github.io address |
| Still the old version after an upload | Wait a few minutes and reload, or add `?v=2` to the address |
| Hitting the ball feels too hard | Menu → Racquet & settings: turn up **Hit assist**, turn on **Perfect hits**, or move the racquet **nearer** |
| The bounce feels off after tuning | Menu → Ball physics → **Reset all** |
