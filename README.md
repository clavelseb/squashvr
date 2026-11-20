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

- **Practice:** pick a drill (Free play, Lob serve, Hard serve, Volley feed, Loose ball, Boast feed, Boast practice, Drive practice). You also set the feed side (forehand, backhand, alternate or alternate +), the target, the time between feeds, the ball type and temperature, and where you stand.
  - **Alternate** runs a sequence of blocks. The default is on the volley feed: 10 backhand crosscourt nicks, 10 backhand straight nicks, 10 forehand crosscourt nicks and 10 forehand straight nicks. Each block's drill, side (forehand, backhand or both), target, feed and number of shots can be changed, and you can have up to 30 blocks.
  - **Alternate +** is a longer sequence of its own (320 shots). Each of the four nicks gets 10 shots off the normal feed (about 61 km/h), 10 off a slightly wider crosscourt feed, 10 off a feed slightly behind you, 10 off one further behind, 20 off a faster feed (about 80 km/h) and 20 off an even faster one (about 92 km/h). You stay at the normal feed's spot, so you move to the ball; the far-behind feed passes over your shoulder unless you step back. The menu shows six blocks at a time (◀ ▶ to page), and the final score is broken down by shot and by kind of feed.
  - You're placed once at the start of each block. The feeds are identical unless you turn on **Small variation**.
  - Every shot scores 3 points for a nick or anything within 10 cm of it, 2 within 30 cm and 1 within 70 cm (measured as the height above the nick where it hits the side wall, or how far from the wall it bounces first; all three distances can be changed in the menu). Boasts and drives score the same way from their own ratings, and the total shows at the end. Press A or X to start again.
- **Racquet & settings:**
  - Racquet hand and grip, and racquet tilt, lean, face angle and distance from your hand.
  - **Hit assist:** a catch zone of 3, 6 or 10 cm around the strings, and **Perfect hits**, which plays every hit from the sweet spot. Both are on by default at the largest setting (10 cm); turn them down or off as your hitting improves.
  - Display options, sound and haptics, and which stick moves you: the racquet hand's (the default) or the ball hand's. The other stick turns you 30° and tilts the racquet.
  - **Refresh rate:** **Max** (the default) uses the highest rate the browser offers and steps down if frames start dropping, retrying the higher rate later. **72**, **90** and **120** fix a rate. On Quest 3, **207** and **240** ask the browser for those rates; the info line underneath says what happened (offered, not offered, or set in developer mode). Turn on **FPS** under Show to see the real rate, the time each frame takes and the share of late frames.
- **Ball physics:**
  - **Values:** 22 ball and bounce settings, adjusted live. Changed values show in amber, and **Reset all** puts them back. **Bounce spin** and **Racquet spin** set how much of the spin from a bounce or a hit the ball keeps (0 % = no spin; **No spin** sets both). **Shell lag** and **Skin that grips** make the soft ball trade less spin with a wall in a hard bounce; **Rigid ball** (or a shell lag of 0) turns that off.
  - **Defaults:** a warm (50 °C) double yellow, rigid ball and no spin. Turn **No spin** or **Rigid ball** off to try spin or the soft shell.
  - **Drop test:** the official 254 cm drop.
  - **Replays and test shots:** **Replay my last hit**, plus test shots from where you stand (drive, crosscourt, boast, lob, drop shot, kill). They play at real speed, ½× or ¼× slow motion.

Settings are saved in the headset's browser, so they're still there the next time you open the page.
