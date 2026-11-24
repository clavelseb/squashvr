# Squash VR Trainer

A solo squash training game that runs in a VR headset's web browser (WebXR). You don't install anything: it's one HTML file, served by GitHub Pages. `index.html` and `squash-vr.html` are the same game; `index.html` just gives it the shorter address.

You get a regulation 9.75 × 6.40 m court, a ball that behaves like a warm double-yellow, a ball machine with drills, and targets for nicks, boasts and straight drives. Two main drills (nick shots and straight length) are scored, and the last 10 you finish are kept.

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

1. **Put on the headset** and clear about 2 × 2 m of floor, or about 3 m across if you want to walk back to the T between shots (see below). Keep the guardian or boundary on, because you will swing hard.
2. **Open the headset's web browser.**
3. **Go to this address** (tap the address bar and type it):

   ```
   clavelseb.github.io/squashvr
   ```

   (The longer `clavelseb.github.io/squashvr/squash-vr.html` opens the same game.) The page should say **"Headset ready. Put it on and press Enter VR."**
4. **Press Enter VR.** If the browser asks for permission to use VR, choose **Allow**.
5. **Play.** The **Nick shot drill** starts by itself. Press **B** (or **Y**) for the menu: it opens on the main drills, where you can pick the **Straight length drill** and see your history. The solo drills are on the **Solo & options** tab. In **Free play** you feed yourself: hold the trigger on your ball hand to hold the ball, release to toss, then hit.

Tip: bookmark the page in the headset's browser so you don't have to type the address again.

> **Use the github.io link, not the github.com one.** The link
> `github.com/clavelseb/squashvr/blob/main/squash-vr.html` only shows the file's source code. The game itself runs from
> **clavelseb.github.io/squashvr**.

---

## What you see on the front wall

Five boxes hang in a row above the out line:

- **Drill** (far left): what you're playing and how far along you are. In a main drill: the block, the shot, what the block asks for, the block's points and the total. In a solo drill: the side, the target and your running averages. In free play: your shots, nicks and best speed, and the ball's temperature.
- **Speed:** the speed of your last shot. It stays up until your next shot, with the drill's average (or your best) under it. It's amber for a hit off the frame and light blue for a hit the hit assist helped. Show: Speed in the menu takes the box down.
- **Last shot** (in the middle): the result of your last shot (NICK!, a drive's rating, TIN, OUT, Not hit…), the **points it earned** in a badge, and the details under it: accuracy and pace, how far from the target, where a drive died. With no target, it says how far above the tin the ball met the front wall and where it first bounced. The same box announces each new block and shows the result at the end of a drill.
- **Back to the T:** how well you went back to the T after your last shot (next section). In free play it counts the shots of your rally instead, and keeps your best.
- **Debug** (far right, only with Show: FPS on): the real refresh rate, the time a frame takes and the share of late frames.

**The last three shots.** The Speed, Last shot and Back to the T boxes keep the two shots before the last one, so you can compare: the last shot is the largest, the one before is smaller under it (in the Last shot box: beside it, under "Before"), and the one before that is smaller and fainter still. For each you see its speed, its result with the points it earned, and how well you went back to the T. A new drill starts the three afresh, and the result at the end of a drill is shown on its own.

## Back to the T

In squash you go back to the T after every shot. In the drills with a feed, the game now rates how well you do it:

- After each shot a **ring on the floor** shows where to go back to. It's red when you leave, turns yellow as you get closer and green when you're there. The box on the front wall says the same: **Go back**, **Closer**, **Excellent**.
- You're rated on how much of the way you covered **before the next ball leaves**: all the way is 100 %, staying where you hit is 0 %, and part of the way counts in proportion. Standing within 35 cm of the middle of the ring counts as being there. The box then shows the verdict, **Excellent** (80 % or more, green), **Good** (40 % or more, yellow) or **Bad** (red), and your average so far.
- **At the end of a main drill** (or a custom sequence) the box shows your back-to-the-T score for the drill, as a percentage. It's kept in the history with the drill's points.
- A ball you didn't hit isn't rated, and neither is a recovery cut short by a new block.
- Once you've walked away, a small mark on the floor shows the hitting spot to come back to.

**How far you walk** is set on the Solo & options tab:

- **Up to 1 m** (the default): back to the T itself when it's within a metre of walking, which it is in the two main drills and Volley feed (the T is 1.2 m from the hitting spot, and the last 35 cm count as there). In the solo drills played from further back, the ring is a metre towards the T.
- **Up to 0.5 m:** for a small room; the ring is half a metre towards the T.
- **To the T:** always the T itself, however far. From the back corners that's about 3 m, so it needs a large room.
- **Off:** no rating, no ring, and the box comes down.

**Fitting the court to your room.** A web page can't make the headset show its boundary, but there are three ways to put the court where your room has space, at any time, in the middle of a drill too. Open the menu (the game is paused while it's open), then:

- **Move with the stick.** The stick that moves you works with the menu open as well, and the menu comes along. Walk to where you want to play from, then slide the court under you.
- **Hitting spot here** (Solo & options, in the Move me row): puts the drill's hitting spot under your feet, wherever you stand.
- **Room outline:** if the headset's browser gives the page its play area, the game draws its outline in blue on the floor, so you can see where your room is in the court. It's shown while the menu is open; the button next to Hitting spot here sets it to always or off. On Quest this is the rectangle of your play area, not the exact boundary you drew, and with a stationary boundary there may be none: the line under the buttons says what the headset gave. A small mark on the floor shows the hitting spot while the menu is open.

**Where the game puts you.** With back to the T on, you're placed on the hitting spot once, when the drill starts: stand where you have room to walk about 1.2 m back to your left and to your right. For the later blocks the court is moved so that the hitting spot stays at the same place in your room, wherever you happen to be standing; in the main drills that only happens when the side changes, and the T is then on your other side. With back to the T off, you're put back on the hitting spot at the start of every block, as before.

---

## What's in the menu

- **Main drills** (the menu opens here):
  - Two drills, each a sequence of blocks off the volley feed, scored 0 to 3 points a shot, with the total at the end.
    - **Nick shot drill** (320 shots). Each of the four nicks (backhand crosscourt and straight, then forehand crosscourt and straight) gets 10 shots off the normal feed (about 61 km/h), 10 off a slightly wider crosscourt feed, 10 off a feed slightly behind you, 10 off one further behind, 20 off a faster feed (about 80 km/h) and 20 off an even faster one (about 92 km/h). Every shot scores 3 points for a nick or anything within 10 cm of it, 2 within 30 cm and 1 within 70 cm (measured as the height above the nick where it hits the side wall, or how far from the wall it bounces first; all three distances can be changed in the menu).
    - **Straight length drill** (160 shots). The same feeds on the backhand, then the forehand, and you drive the ball straight down the wall to a length. Each drive is rated on length (where it dies, a touch long beats short), how tight it stays to the side wall all the way back, and touching the side wall late or not at all: 3 points for a drive rated 85 or more, 2 for 70, 1 for 50.
    - The hitting spot is the normal feed's spot for every block, so you move to the ball; the far-behind feed passes over your shoulder unless you step back. The feeds are identical unless you turn on **Small variation**. **Edit the blocks** changes any block's drill, side, target, feed and number of shots (six blocks a page, up to 30); **Back to the default drill** restores it. Press A or X to start again.
  - **History**, under the two drills: the last 10 drills you played to the end (main drills or custom sequence), newest first, with the points, the score, the average speed of your shots, your back-to-the-T score and how many shots scored 3, 2 and 1, and a star on your best of each drill. Tap one for its breakdown by shot and by kind of feed (score and average speed), and the ball it was played with; tap it again to close it.
- **Solo & options:**
  - **Solo drills:** Free play, Lob serve, Hard serve, Volley feed, Loose ball, Boast feed, Boast practice and Drive practice, each with its feed side (forehand, backhand or both sides, every other feed) and target. **Custom sequence** (the old Alternate) is a sequence of your own, by default 10 backhand crosscourt nicks, 10 backhand straight nicks, then the same on the forehand.
  - The time between feeds, the ball type and temperature, and **Back to the T** (off, up to 0.5 m, up to 1 m, to the T).
  - **Move me:** to the T, the front or a back corner; **Hitting spot here**; the **Room outline** (with the menu, always, off). The stick moves you with the menu open too.
- **Racquet & settings:**
  - Racquet hand and grip, and racquet tilt, lean, face angle and distance from your hand.
  - **Hit assist:** a catch zone of 3, 6 or 10 cm around the strings, and **Perfect hits**, which plays every hit from the sweet spot. Both are on by default at the largest setting (10 cm); turn them down or off as your hitting improves.
  - **Short swing assist**, for drops, slow shots and volleys with a very short swing. It's on by default at **Slow swings + timing**; the switch is still there to compare:
    - **Off:** the hit assist only helps a swing above about 7 km/h of racquet speed, and a hit is played at the speed the racquet has at the instant the ball meets the strings.
    - **Slow swings:** the hit assist also helps a slow swing, as soon as the strings are moving at the ball at about 2 km/h, so a gentle push comes off the sweet spot like a full swing does. A racquet that is held still, drifts sideways or gives with the ball is still not helped.
    - **Slow swings + timing** (the default): also, a hit is played at the top speed the strings reached within 35 ms before or after the ball met them. A short swing is only fast for a few hundredths of a second; with this setting it gives the same shot whether you meet the ball a little early or a little late. The help is complete up to about 22 km/h of racquet speed and fades out by 43 km/h, so a full swing is not changed at all. The trade-off: braking in the last instant before the ball no longer takes pace off it. For a softer shot, swing more slowly, or give with the ball.
    - The Drill box on the front wall says so when the setting isn't the default.
    - The engine fix that came with this switch in v1.24 is now always on: a fast ball that caught the edge of the head of a slow or still racquet could stay on it until the racquet snapped back to your hand, and be thrown off at an impossible speed. Such a hit now ends as the mishit it is.
  - Display options, sound and haptics, and which stick moves you: the racquet hand's (the default) or the ball hand's. The other stick turns you 30° and tilts the racquet.
  - **Refresh rate:** **Max** (the default) uses the highest rate the browser offers and steps down if frames start dropping, retrying the higher rate later. **72**, **90** and **120** fix a rate. On Quest 3, **207** and **240** ask the browser for those rates; the info line underneath says what happened (offered, not offered, or set in developer mode). Turn on **FPS** under Show to see the real rate, the time each frame takes and the share of late frames.
- **Ball physics:**
  - **Values:** 22 ball and bounce settings, adjusted live. Changed values show in amber, and **Reset all** puts them back. **Bounce spin** and **Racquet spin** set how much of the spin from a bounce or a hit the ball keeps (0 % = no spin; **No spin** sets both). **Shell lag** and **Skin that grips** make the soft ball trade less spin with a wall in a hard bounce; **Rigid ball** (or a shell lag of 0) turns that off.
  - **Defaults:** a warm (50 °C) double yellow, rigid ball and no spin. Turn **No spin** or **Rigid ball** off to try spin or the soft shell.
  - **Drop test:** the official 254 cm drop.
  - **Replays and test shots:** **Replay my last hit**, plus test shots from where you stand (drive, crosscourt, boast, lob, drop shot, kill). They play at real speed, ½× or ¼× slow motion.

Settings are saved in the headset's browser, so they're still there the next time you open the page.
