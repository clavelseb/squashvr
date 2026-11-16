# Squash VR Trainer

A solo squash training game that runs in a VR headset's web browser (WebXR). You don't install anything: it's one HTML file, served by GitHub Pages. `index.html` and `squash-vr.html` are the same game; `index.html` just gives it the shorter address.

You get a regulation 9.75 × 6.40 m court, a ball that behaves like a warm double-yellow, a ball machine with drills, and targets for nicks, boasts and deep drives.

**What you need:**
- A standalone VR headset whose browser supports WebXR.
- Two tracked controllers with thumbsticks, triggers and A/B/X/Y buttons.

The game runs at the highest refresh rate the headset's browser offers and steps down by itself if it starts dropping frames: 120 Hz on Quest 2 and 3S. Quest 3 with Horizon OS 2.7 or later can run apps at up to 207 Hz, but the browser may still offer web pages only up to 120 Hz: that is what a Quest 3 showed in November 2026. The info line under the refresh rate buttons in the menu shows what yours offers. It was developed and tested on Meta Quest 2.

**207 or 240 Hz on Quest 3 (developer mode):** with developer mode on and the headset connected to a computer, this command forces 207 Hz for everything, the browser included, at full resolution:

```
adb shell setprop debug.oculus.refreshRate 207
```

For 240 Hz, display scaling has to be turned on first (the image is rendered at a lower resolution and scaled up):

```
adb shell setprop debug.oculus.forceDisplayScaling 1
adb shell setprop debug.oculus.refreshRate 240
```

Any whole number from 72 to 240 works, so 180 or 144 are there if 207 drops frames. The settings last until the headset restarts. The game sees the forced rate, leaves it alone, and shows "developer mode" in the menu.

---

## Play it on your headset (from GitHub)

1. **Put on the headset** and clear about 2 × 2 m of floor. Keep the guardian or boundary on, because you will swing hard.
2. **Open the headset's web browser.**
3. **Go to this address** (tap the address bar and type it):

   ```
   clavelseb.github.io/squashvr
   ```

   (The longer `clavelseb.github.io/squashvr/squash-vr.html` opens the same game.) The page should say **"Headset ready. Put it on and press Enter VR."**
4. **Press Enter VR.** If the browser asks for permission to use VR, choose **Allow**.
5. **Play.** Press **B** (or **Y**) for the menu. Choose a drill under **Practice**, or stay in **Free play**: hold the trigger on your ball hand to hold the ball, release to toss, then hit.

Tip: bookmark the page in the headset's browser so you don't have to type the address again.

> **Use the github.io link, not the github.com one.** The link
> `github.com/clavelseb/squashvr/blob/main/squash-vr.html` only shows the file's source code. The game itself runs from
> **clavelseb.github.io/squashvr**.

---

## What's in the menu

- **Practice:** pick a drill (Free play, Lob serve, Hard serve, Volley feed, Loose ball, Boast feed, Boast practice, Drive practice). You also set the feed side (forehand, backhand or alternate), the target, the time between feeds, the ball type and temperature, and where you stand.
- **Racquet & settings:**
  - Racquet hand and grip, and racquet tilt, lean, face angle and distance from your hand.
  - **Hit assist:** a catch zone of 3, 6 or 10 cm around the strings, and **Perfect hits**, which plays every hit from the sweet spot. Both are on by default at the largest setting (10 cm); turn them down or off as your hitting improves.
  - Display options, sound and haptics.
  - **Refresh rate:** **Max** (the default) uses the highest rate the browser offers and steps down if frames start dropping, retrying the higher rate later. **72**, **90** and **120** fix a rate. On Quest 3, **207** and **240** ask the browser for those rates; the info line underneath says what happened (offered, not offered, or set in developer mode). Turn on **FPS** under Show to see the real rate, the time each frame takes and the share of late frames.
- **Ball physics:**
  - **Values:** 20 ball and bounce settings, adjusted live. Changed values show in amber, and **Reset all** puts them back. **Rigid ball** turns off the shell lag added in v1.13 (the soft ball trades less spin with a wall in a hard bounce), so you can compare with the old bounce.
  - **Drop test:** the official 254 cm drop.
  - **Replays and test shots:** **Replay my last hit**, plus test shots from where you stand (drive, crosscourt, boast, lob, drop shot, kill). They play at real speed, ½× or ¼× slow motion.

Settings are saved in the headset's browser, so they're still there the next time you open the page.
