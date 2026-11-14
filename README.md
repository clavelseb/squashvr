# Squash VR Trainer

A solo squash training game that runs in a VR headset's web browser (WebXR). You don't install anything: it's one HTML file, served by GitHub Pages. `index.html` and `squash-vr.html` are the same game; `index.html` just gives it the shorter address.

You get a regulation 9.75 × 6.40 m court, a ball that behaves like a warm double-yellow, a ball machine with drills, and targets for nicks, boasts and deep drives.

**What you need:**
- A standalone VR headset whose browser supports WebXR.
- Two tracked controllers with thumbsticks, triggers and A/B/X/Y buttons.

The game asks for 120 Hz and drops to 90 or 72 Hz where the headset doesn't offer it; a headset that runs WebXR at 120 Hz gives the smoothest swings. It was developed and tested on Meta Quest 2.

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
  - Display options, refresh rate (72, 90 or 120 Hz), sound and haptics.
- **Ball physics:**
  - **Values:** 18 ball and bounce settings, adjusted live. Changed values show in amber, and **Reset all** puts them back.
  - **Drop test:** the official 254 cm drop.
  - **Replays and test shots:** **Replay my last hit**, plus test shots from where you stand (drive, crosscourt, boast, lob, drop shot, kill). They play at real speed, ½× or ¼× slow motion.

Settings are saved in the headset's browser, so they're still there the next time you open the page.
