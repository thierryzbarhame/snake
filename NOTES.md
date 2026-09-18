# Snake — Development Notes

This file documents what was found while playing the game and what was
requested from the coding agent, in the order it actually happened.

## Initial Implementation

The first version of the game was a complete, playable Snake built as a
single self-contained `index.html` (HTML + CSS + JS inline, no dependencies,
no build step, no server, works via a `file://` URL). It included:

- A 20x20 game board rendered on an HTML5 `<canvas>`.
- A 3-segment snake starting in the middle of the board, moving continuously.
- Arrow-key controls, with instant 180-degree reversal blocked.
- Random food placement, snake growth, and score tracking (+10 per food).
- Wall and self-collision detection, ending the game.
- A Game Over overlay with the final score and a Restart button that fully
  reset the snake, food, score, and game state.
- A best-score display persisted via `localStorage`.

This initial version used plain square segments for the snake and food, a
fixed-size board, and a single constant game speed (no levels).

## Issue 1 — Snake Appearance

**Observation:** After playing the initial version, the snake looked like a
plain row of identical squares — it didn't look like an actual snake.

**Request:** Redesign the snake so it looks like a real snake: a clear head,
visible eyes, a distinct body, a tail that tapers toward the end, and a head
that points in the direction of movement, while staying easy to see against
the board.

**Change made:** The rendering was rewritten so the body is drawn as smooth,
rounded, tapering segments (thick near the head, narrowing to a point at the
tail) with a green gradient from head to tail. The head is a distinct,
direction-aware shape (rotated to face the current movement direction) with
two eyes and a small tongue. The food was also redesigned to look like a
shaded apple instead of a flat square, and the board received a cleaner
background/grid for better contrast.

## Issue 2 — Screen Scrolling

**Observation:** The game page did not fill the browser window and could
scroll, which made it feel like a normal webpage rather than a standalone
game.

**Request:** Make the game occupy the full browser viewport, with no
vertical or horizontal scrolling, while staying centered and responsive at
different window sizes.

**Change made:** The layout was rebuilt as a fixed, non-scrolling full-screen
layout (`html`/`body` locked to the viewport, `overflow: hidden`), with the
title/score bar on top, the board centered in the middle, and the controls
hint at the bottom. The canvas size is now computed in JavaScript from the
available space and recalculated on every window resize, so the board always
fits on screen without producing scrollbars.

## Issue 3 — Progressive Speed

**Observation:** The game ran at a single constant speed for the entire
session, with no increasing challenge as the score grew.

**Request:** Add a progressive difficulty system where the level is based on
the score (a new level every 500 points, `Level = floor(score / 500) + 1`),
with the speed increasing gradually and consistently at each level, and the
score/level clearly displayed alongside each other.

**Change made:** A level system was added, driven entirely by the current
score. The current score and level are shown together in the status bar, and
the game speed increases by a fixed step at each new 500-point threshold,
taking effect immediately.

## Issue 4 — Incorrect Starting Level and Speed

**Observation:** During testing of the progressive speed system, two
problems were found:

- The snake was still moving much too fast at the very start of the game.
- The displayed level incorrectly started at 50 instead of 1.

**Request:** Fix the speed and level system completely so that a new game
always starts at Score 0, Level 1, with a genuinely very slow starting
speed, and so that speed increases gradually and predictably at each
500-point threshold; also investigate why the starting level was wrong
instead of only patching the symptom.

**Change made:** The level value was changed so it is never set or stored
independently — it is always computed directly from the current score using
one single formula (`Level = floor(score / 500) + 1`), both at game start
and during play, removing any possibility of the displayed level and the
actual score disagreeing. The starting speed was substantially slowed down,
and the speed-per-level curve was reworked to ease gradually from that slow
starting speed toward a capped maximum, so it never becomes impossibly fast.
The fix was verified by running the game and confirming a fresh start shows
Score 0 and Level 1, and that the snake's on-screen movement matched the
intended slow starting speed.

## Final Testing

After the fixes above, the game was tested again by playing it directly,
covering: game startup, keyboard controls, food collection, snake growth,
score updates, level progression, speed progression, wall collision,
self-collision, Game Over, restart, the full-screen layout, the absence of
page scrolling, and the final visual appearance. The final version was
confirmed to be satisfactory.
