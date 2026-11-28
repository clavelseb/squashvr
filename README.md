# Squash VR Trainer

A solo squash training game that runs in a VR headset's web browser (WebXR). You don't install anything: it's one HTML file, served by GitHub Pages. `index.html` and `squash-vr.html` are the same game; `index.html` just gives it the shorter address.

You get a regulation 9.75 × 6.40 m court, a ball that behaves like a warm double-yellow, a coach who feeds you in the drills, and targets for nicks, boasts, drives, drops, kills and lobs. Four main drills (nick shots, straight length, the front court and the back court) are scored, and every one you finish is kept in the history.

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
5. **Play.** The **Nick shot drill** starts by itself. Press **B** (or **Y**) for the menu: it opens on the main drills, where you can pick the **Straight length drill**, the **Front court drill** or the **Back court drill** and see your history. The solo drills are on the **Solo & options** tab. In **Free play** you feed yourself: hold the trigger on your ball hand to hold the ball, release to toss, then hit.

Tip: bookmark the page in the headset's browser so you don't have to type the address again.

> **Use the github.io link, not the github.com one.** The link
> `github.com/clavelseb/squashvr/blob/main/squash-vr.html` only shows the file's source code. The game itself runs from
> **clavelseb.github.io/squashvr**.

---

## What you see on the front wall

Five boxes hang in a row above the out line:

- **Drill** (far left): what you're playing and how far along you are. In a main drill: the block, the shot, what the block asks for, the block's points and the total. In a solo drill: the side, the target and your running averages. In free play: your shots, nicks and best speed, and the ball's temperature.
- **Speed:** the speed of your last shot. It stays up until your next shot, with the drill's average (or your best) under it. It's amber for a hit off the frame and light blue for a hit the hit assist helped. Show: Speed in the menu takes the box down.
- **Last shot** (in the middle): the result of your last shot (NICK!, a drive's, drop's or lob's rating, TIN, OUT, Not hit…), the **points it earned** in a badge, and the details under it: accuracy and pace, how far from the target, where a drive died. With no target, it says how far above the tin the ball met the front wall and where it first bounced. The same box announces each new block and shows the result at the end of a drill.
- **Back to the T:** how well you went back to the T after your last shot (next section). In free play it counts the shots of your rally instead, and keeps your best.
- **Debug** (far right, only with Show: FPS on): the real refresh rate, the time a frame takes and the share of late frames.

**The last three shots.** The Speed, Last shot and Back to the T boxes keep the two shots before the last one, so you can compare: the last shot is the largest, the one before is smaller under it (in the Last shot box: beside it, under "Before"), and the one before that is smaller and fainter still. For each you see its speed, its result with the points it earned, and how well you went back to the T. A new drill starts the three afresh, and the result at the end of a drill is shown on its own.

## The coach who feeds you

Since v1.35 the balls aren't fired by an invisible machine: a coach plays them to you with her racquet. She moves with real motion capture (a standing idle and two swings, right to left and left to right), and her voice is the one that reads out the blocks and results.

- **Every feed is her hit.** Her swing starts about 1.2 s before the feed is due, and the ball leaves her racquet at the moment of contact.
- **Her ball** (v1.36): while she waits to feed she holds the next ball in her left hand, in front of her chest. As she swings she throws it up, about 0.25 s before the hit, at the top of her capture's own toss, and it flies onto her racquet where the feed starts, at the moment of the hit. There the game's ball takes over: one ball, from her hand to the front wall. During the rally her hand is empty; she has the next ball again once the rally is over. The feeds themselves are unchanged: same place, same speed, same targets. She stands so that her racquet meets the ball where the feed starts, turned so that it swings the way the ball goes. She plays whichever of the two swings keeps her clear of the walls and of you, and meets the ball a little earlier or later in the swing to match its height (0.6 m for the drop feed, 1.2 m for the hard serve).
- **Where she stands:** where the drill's feeds come from: behind you for the volley feeds, on the T or beside it for the back court drill, in the back corner for the boast and drop feeds. Between blocks she glides to the next spot, or appears there if it's far.
- **Where she looks:** at you when she talks (a new block, a result, what to work on), and she turns towards you between feeds if she has her back to you. While she feeds she looks at the front wall where her ball is going. She watches the ball come back to you and you hit it, then looks at your shot's target on the front wall, then back at you.
- **Her looks**, on the Racquet & settings tab under **Coach**: **Cartoon** (the default: two flat tones and an ink outline), **Comic** (printed colours and halftone dots), **Chrome** (a moving mirror of the court), **Glass**, **Neon** (a dark figure drawn by glowing edges) and **Hologram**. **Off** brings back the blue mark on the floor where the feeds come from.
- **Cost:** she is one model of about 3,400 triangles (1,400 for Neon), drawn in one or two passes per eye. Working out her pose takes under 0.2 ms a frame, so the 240 Hz target isn't at risk.
- Her hair is in a chignon, so nothing swings when she moves.

## What you hear: the voice

In a main drill or a custom sequence a voice reads out what the front wall shows, so you don't have to look up at it between shots:

- **Each block as it starts.** Before the first one, the drill's name. Then "Next block" (or "Last block") and what the block asks for, as the wall names it: "Backhand straight drives. Off a length feed." The kind of feed is added when it isn't the normal one ("A wider feed", "Behind you", "Faster feed"…). The block's first ball waits until that has been said, 2 to 4 seconds.
- **Each shot's result:** "Great drive!", "Too loose.", "Tin." It's the headline of the Last shot box without the details, and "Near nick" is "Almost a nick!".
- **A nick shot that missed, by how much** (v1.34): within the distance that scores 3 points (10 cm by default) "So close!"; beyond the one that scores 1 (70 cm) "Missed."; in between, the distance from the Last shot box, rounded to 5 cm (to 10 cm above 50): "Twenty centimetres short." when the ball bounced before the side wall, "Forty centimetres too high." when it hit the side wall above the nick. No points are said with these: the distance tells them. The limits follow the nick points set in the menu. A new result cuts off an older one that is still being said.
- **The points only when the result doesn't tell them.** A nick, a great shot and a tight boast are always 3 points, a good shot 2, a tin, an out or a ball not hit 0, so nothing more is said. A result that names what was wrong ("Too loose", "A bit short", a boast "Too high") can still score, and then the points follow: "Too loose. One point." With no points it stops at "Too loose." The points are also said when a result scores other than its usual (a nick off the wrong side wall: "Nick! One point.").
- **What to work on, at the end of a block only.** If over the block you covered less than half the way back to the T on average, the voice says "Make more effort to go back to the T!" before it announces the next block. If you watched the ball less than 50 % on average, it says "Make more effort to watch the ball!", and if both, one sentence for the two. The same sentence is added to the Next block box on the wall. It takes at least two rated shots in the block, and it is never said during play: only between two blocks, and before "Drill done" after the last one. Nothing is said about the T with back to the T off, or about watching the ball where it isn't rated (the feeder in front of you, as in the whole Back court drill).
- In a **solo drill** with a target, the voice reads each shot's result, without points (solo drills aren't scored). In free play it says nothing.

**The setting** is on the Racquet & settings tab: **Blocks and every shot** (the default), **Blocks only** (the blocks and what to work on, no results) or **Off** (and then no feed waits for it). It's as loud as the Sound setting makes the rest.

**The voice itself.** As far as I could find, the Quest's browser has no text-to-speech to offer a web page, so the phrases come with the game, in one recording. Since v1.33 they are spoken by Kokoro, an open-source neural text-to-speech model, in its voice "Bella" (American English), which sounds far more natural than the synthesiser of v1.32. Of six voices tried it was the one a speech recogniser understood best: 109 of the 114 phrases as written, against 63 for the old voice; the five it gets wrong are near misses, like "tin" heard as "ten" and "nick" as "neck". Because the phrases are recorded in advance, the voice only says things from a fixed list (blocks, results, points, nick distances in steps of 5 or 10 cm): 147 phrases, about 540 KB.

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

## Watching the ball

In the drills the ball is fed from behind you, as an opponent would hit it, so you should be looking back at the feeder when the ball leaves, not at the front wall. The game rates that at every feed, from how far your head is turned:

- **0 %:** your head faces the front wall as the ball leaves.
- **100 %:** your head is turned to where the ball comes from. Within 30° of the feeder counts as all of it: the feeder is then well inside the headset's view.
- In between, it goes with the angle: half way round is about two thirds in the main drills, where the feeder is some 135° behind you.
- The best moment from 0.3 s before the ball leaves to 0.15 s after it is the one that counts, and only the turn of your head left or right, not up or down. Every feed counts, whether you hit the ball or not.

Nothing is shown shot by shot. **At the end of a main drill** (or a custom sequence) the result on the front wall gives your watching-the-ball score, as a percentage beside the back-to-the-T score, and it's kept in the history. Boast practice and Drive practice feed from in front of you, so there is nothing to rate there; the same goes for the whole Back court drill.

**Fitting the court to your room.** A web page can't make the headset show its boundary, but there are three ways to put the court where your room has space, at any time, in the middle of a drill too. Open the menu (the game is paused while it's open), then:

- **Move with the stick.** The stick that moves you works with the menu open as well, and the menu comes along. Walk to where you want to play from, then slide the court under you.
- **Hitting spot here** (Solo & options, in the Move me row): puts the drill's hitting spot under your feet, wherever you stand.
- **Room outline:** if the headset's browser gives the page its play area, the game draws its outline in blue on the floor, so you can see where your room is in the court. It's shown while the menu is open; the button next to Hitting spot here sets it to always or off. On Quest this is the rectangle of your play area, not the exact boundary you drew, and with a stationary boundary there may be none: the line under the buttons says what the headset gave. A small mark on the floor shows the hitting spot while the menu is open.

**Where the game puts you.** With back to the T on, you're placed on the hitting spot once, when the drill starts: stand where you have room to walk about 1.2 m back to your left and to your right. For the later blocks the court is moved so that the hitting spot stays at the same place in your room, wherever you happen to be standing; in the main drills that only happens when the side changes, and the T is then on your other side. With back to the T off, you're put back on the hitting spot at the start of every block, as before.

**Both sides, when the two hitting spots are far apart** (Both sides in a solo drill played from the back or the front corners, or a block set to both sides in the block editor). The main drills never do this: each half keeps to one side. The two back corners are about 4 m apart, and nobody's room is that wide. So the court is set for one corner at a time: a moment after each rally is over it moves, with a low blip, to the corner the next ball goes to, and that ball comes a good second later.

- **With back to the T on,** the ring you walk back to stays where it is in your room. The forehand's hitting spot is behind it on one side and the backhand's on the other, as the two back corners are from the T, so the footwork is the real one in small: out to the corner, back to the ring, out to the other corner. With **Up to 1 m** the two hitting spots are about 1.5 m apart, with **Up to 0.5 m** about 1 m. They take no more floor than the two sides' rings do in the other blocks, but you now swing at both ends of it, so check that you have room to swing there. **To the T** leaves the court where it is: you walk the real distance.
- **With back to the T off,** the hitting spot comes to where you stand before every ball. You need not move at all.
- **With Auto-place me off,** nothing moves: you walk, or use the stick.
- The small mark on the floor shows the hitting spot of the next ball, on one side of the ring and then on the other. When such a block starts you stand between the two hitting spots, behind the ring: step out to the mark for the first ball.
- The menu says which it is under **Feed side** (or under the block being played), with the distance between the two hitting spots.
- The volley feed and the boast feed are different: their two hitting spots are about 2 m apart, so you stand between them and step to each ball, as before.

---

## What's in the menu

- **Main drills** (the menu opens here):
  - Four drills, each a sequence of blocks, scored 0 to 3 points a shot, with the total at the end. The first two are played off the volley feed, the third off a drop, the fourth off drives to the back.
    - **Nick shot drill** (320 shots). Each of the four nicks (backhand crosscourt and straight, then forehand crosscourt and straight) gets 10 shots off the normal feed (about 61 km/h), 10 off a slightly wider crosscourt feed, 10 off a feed slightly behind you, 10 off one further behind, 20 off a faster feed (about 80 km/h) and 20 off an even faster one (about 92 km/h). Every shot scores 3 points for a nick or anything within 10 cm of it, 2 within 30 cm and 1 within 70 cm (measured as the height above the nick where it hits the side wall, or how far from the wall it bounces first; all three distances can be changed in the menu).
    - **Straight length drill** (160 shots). The same feeds on the backhand, then the forehand, and you drive the ball straight down the wall to a length. Each drive is rated on length (where it dies, a touch long beats short), how tight it stays to the side wall all the way back, and touching the side wall late or not at all: 3 points for a drive rated 85 or more, 2 for 70, 1 for 50.
    - **Front court drill** (120 shots). The ball machine plays a straight drop from the back corner on your side: about 50 km/h, onto the front wall 40 cm above the tin, first bounce 1.6 m from the front wall. It comes up to knee height at most, so you take it low, in the front court. You answer it six ways, 10 of each, on the backhand and then the forehand: **counter drop**, **straight drive**, **crosscourt drive** (hard and low), **straight lob**, **crosscourt lob** and **crosscourt nick**. A target on the front wall shows where to aim and at what pace, with the ideal path and where it lands. The nick and the straight drive are scored as in the other two drills. The other four are rated from 0 to 100 on where the ball goes, each on three things, and score 3 points for 85 or more, 2 for 70 and 1 for 50:
      - Counter drop: **short** (where it dies: full marks within 2.3 m of the front wall), **low** (within 15 cm above the tin) and **tight** (how far from the side wall it bounces).
      - Crosscourt drive: **length** (dying at the back wall, as for the straight drive), **width** (it should pass the T line 1.4 to 2.4 m from the middle: out of reach of a volley from the T, but not into the side wall before it) and **low** (no more than about 55 cm above the tin on the front wall; with the length, that only works when it's hit hard).
      - Straight lob: **height** (2.8 m or more over the T line is out of reach), **length** (a lob may come further off the back wall than a drive) and **tight** (first bounce within 80 cm of the side wall).
      - Crosscourt lob: **height**, **length** and **width** (first bounce within 80 cm of the far side wall, or off that wall behind the T line).
      - A lob leaves little room in its pace. The ideal one from the front corner is about 60 km/h: 10 % less and it passes the T line within reach, 25 % more and it hits the ceiling or goes out. The Last shot box gives the pace you used and the ideal one. A drop into the tin, or any shot that is out, scores 0.
    - **Back court drill** (160 shots). The ball machine stands on the T and drives straight down your side wall (for the overhit drive and the boast feed it stands beside the T, 1.3 m off the side wall, so that they are straight drives too); you play from the back of the court. Eight exercises, 10 of each, all on the backhand and then all on the forehand, so each half of the drill stays in one back corner. The feeds sit up: low balls are hard to get in a headset.
      - *Length and basics.* **Straight drive** off the length feed (about 60 km/h, high on the front wall, first bounce behind the short line; it comes up to about 85 cm at the back of the service box, where you take it). **Straight drive off the back wall:** the feed is overhit (about 120 km/h), hits the back wall on the full and comes out about 1.5 m before it bounces; you let it come out and bounce, and drive it straight, at about 70 cm. **Crosscourt length:** off the length feed, across the court to die in the far back corner.
      - *Attacking from the back.* **Boasts** off a deep drive (about 70 km/h): it bounces behind the service box and comes up to about 80 cm, where you take it, a metre off the back wall and a metre off the side wall. **Straight drop** off the length feed, and again off the overhit feed, after the back wall. **Straight kill** off a loose, short length (about 50 km/h, high on the front wall; it bounces just behind the short line and sits up to about 1.1 m at the back of the service box): low and hard, to die before the service box.
      - *Under pressure.* **Crosscourt lob** off a hard length (about 80 km/h, on you in about 1.45 s, taken about 60 cm up): lift it high across the court to the far back corner.
      - The drives and the boasts are scored as in the other drills. The others are rated from 0 to 100 on three things each, like the Front court drill's shots, and score 3 points for 85 or more, 2 for 70 and 1 for 50:
        - Crosscourt length: **length** (dying at the back wall), **width** (passing the T line at least 1.4 m from the middle; there is no "too wide" here) and **side wall** (touching it behind the service box, 7 m or more from the front wall, or not at all; earlier than that is "side wall too early").
        - Straight kill: **short** (the second bounce before the short line, 5.44 m from the front wall; a kill that carries further was hit too high), **hard** (110 km/h or more is full marks, 90 km/h still nearly) and **tight** (within 20 cm of the side wall on average is full marks).
        - Straight drop from the back: the same three things as the counter drop, with marks that ease off with the distance, since a drop from 7 m can't be as short or as low as one from the front court: full marks dying within about 2.9 m of the front wall and within 25 cm above the tin. The ideal one is about 48 km/h; 5 % harder is still great, 10 % harder still good, 10 % softer is in the tin.
        - Crosscourt lob from the back: as in the Front court drill, with the height asked for over the T line eased from 2.8 m to about 2.4 m.
      - Watching the ball is not rated in this drill (the feeder is in front of you); back to the T is.
    - In every drill a feed can't be played before it has reached the front wall, as in a game: until then your racquet goes through the ball. That matters for the drop, which comes down your own side wall past you.
    - In the first two drills the hitting spot is the normal feed's spot for every block, so you move to the ball; the far-behind feed passes over your shoulder unless you step back. The feeds are identical unless you turn on **Small variation**. **Edit the blocks** changes any block's feed, side, target, kind of feed and number of shots (six blocks a page, up to 30); **Back to the default drill** restores it. The first button of a block names what the ball machine plays: the feed of one of the solo drills (**Length feed** is Drive practice's, **Deep drive** is Boast practice's). So the Back court drill can be cut down to one side, or to the exercises you want. Press A or X to start again.
  - **History**, under the drills: every drill you played to the end (main drills or custom sequence), newest first, 10 to a page with **Newer** and **Older** buttons under them. It's no longer limited to the last 10; only if the browser's storage were ever full would the oldest be dropped. Each has the points, the score, the average speed of your shots, your back-to-the-T and watching-the-ball scores and how many shots scored 3, 2 and 1, and a star on your best of each drill. Tap one for its breakdown by shot and by kind of feed (score and average speed), and the ball it was played with; tap it again to close it. The star is for the best of all of them, on whichever page it is.
- **Solo & options:**
  - **Solo drills:** Free play, Lob serve, Hard serve, Volley feed, Loose ball, Boast feed, Drop feed (the Front court drill's feed), Boast practice (the deep drive for boasts), Drive practice (the length feed), and the Back court drill's three other feeds: **Off the back wall**, **Loose length** and **Hard length**. Each has its feed side (forehand, backhand or both sides, every other feed) and target: crosscourt nick, straight nick, boast, straight drive, straight drop (a counter drop off the drop feed), straight kill, crosscourt drive, crosscourt length, straight lob, crosscourt lob, or none. **Custom sequence** (the old Alternate) is a sequence of your own, by default 10 backhand crosscourt nicks, 10 backhand straight nicks, then the same on the forehand.
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
  - **Coach:** her look (Cartoon, Comic, Chrome, Glass, Neon, Hologram) or Off. See "The coach who feeds you" above.
  - **Voice:** blocks and every shot (the default), blocks only, or off. See "What you hear" above.
  - Display options, sound and haptics, and which stick moves you: the racquet hand's (the default) or the ball hand's. The other stick turns you 30° and tilts the racquet.
  - **Refresh rate:** **Max** (the default) uses the highest rate the browser offers and steps down if frames start dropping, retrying the higher rate later. **72**, **90** and **120** fix a rate. On Quest 3, **207** and **240** ask the browser for those rates; the info line underneath says what happened (offered, not offered, or set in developer mode). Turn on **FPS** under Show to see the real rate, the time each frame takes and the share of late frames.
- **Ball physics:**
  - **Values:** 22 ball and bounce settings, adjusted live. Changed values show in amber, and **Reset all** puts them back. **Bounce spin** and **Racquet spin** set how much of the spin from a bounce or a hit the ball keeps (0 % = no spin; **No spin** sets both). **Shell lag** and **Skin that grips** make the soft ball trade less spin with a wall in a hard bounce; **Rigid ball** (or a shell lag of 0) turns that off.
  - **Defaults:** a warm (50 °C) double yellow, rigid ball and no spin. Turn **No spin** or **Rigid ball** off to try spin or the soft shell.
  - **Drop test:** the official 254 cm drop.
  - **Replays and test shots:** **Replay my last hit**, plus test shots from where you stand (drive, crosscourt, boast, lob, drop shot, kill). They play at real speed, ½× or ¼× slow motion.

Settings are saved in the headset's browser, so they're still there the next time you open the page.
