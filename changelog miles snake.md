# Changelog — Miles' Snake Game

A record of every change made to the game file since it was first created.
(The file was originally named `snake.html` and is now `Miles snake game.html`.)

This project is a teaching tool for grade 4–5 students — see `CLAUDE.md` for the
lesson plan and the deliberately-planted mistake used during the demo.

---

## 1. Created the game
The first version of `snake.html` — a complete, playable Snake game in a single
HTML file (just double-click to open in a browser, no installing anything). It
followed the approved class plan:

- A **400 × 400** game window made of **20 px grid squares** (a 20 × 20 board).
- A **green** snake that starts in the middle.
- Steering with the **arrow keys**.
- One **red square apple** placed in a random empty spot.
- Eating an apple makes the snake **longer** (the corrected rule from the plan).
- A **score** shown at the top, going up by one per apple.
- **Game over** when the snake hits a wall or runs into itself; press **Space**
  to play again.
- The snake moved one square every **120 ms**.

## 2. Made the snake purple
Changed the snake colour from green (`#4caf50`) to **purple** (`#9c27b0`).

## 3. Turned the apple into a raspberry
Replaced the flat red square with a **drawn raspberry**: a cluster of little
round bumps (drupelets) in raspberry-pink with tiny shines, plus a small green
leafy top. Added the `drawRaspberry()` and `leaf()` drawing helpers.

## 4. Slowed the snake down (120 ms → 160 ms)
Increased the step time so the snake moved a little slower and was easier to
control.

## 5. Set the speed to 200 ms
Changed the step time again to **200 ms** for a relaxed pace.

## 6. Overhauled the snake graphics (detailed / shaded serpent)
Replaced the flat purple squares with a much more realistic snake:

- A smooth, **tapering 3D tube body** (fat head → thin tail) built from layered
  strokes (dark edges → bright spine) with a soft drop shadow for depth.
- **Chevron scale texture** running down the back.
- A real **head** that rotates to face the travel direction, with **yellow eyes
  and slit pupils** (plus a glint), **nostrils**, and a **flicking forked
  tongue**.

Added a `frame` counter (for the tongue animation) and the `drawSnake()`,
`drawScales()`, and `drawHead()` functions.

## 7. Added visible grid squares
Drew a faint grid over the board so the squares the snake and raspberries sit in
are visible.

## 8. Made the game area bigger (400 → 600)
Enlarged the canvas to **600 × 600**, turning the board into a **30 × 30** grid.
Everything (grid, walls, raspberry placement) scaled automatically because it is
all calculated from the canvas size.

## 9. Added 29 more raspberries (30 on the board at once)
Changed the single apple into a list of **30 raspberries**. They never overlap
each other or the snake, and when one is eaten a fresh one instantly appears
elsewhere so there are always 30 to chase. Added `placeApples()` and
`newRaspberrySpot()`, and updated the eating logic and the draw loop.

## 10. Fixed the laggy / choppy movement
The game had only been redrawing once per move (≈5 frames per second), which
looked choppy. Split the game into two beats:

- **Movement** still happens once every 200 ms (same difficulty).
- **Drawing** now runs continuously at ~60 fps using `requestAnimationFrame`,
  and the snake **glides smoothly** between squares.

Added `prevSnake`, `lastStep`, `renderT`, and a `MOVE_MS` constant; replaced the
old `tick()` / `setInterval` with a pure-logic `step()` and a smooth `loop()`;
interpolated the snake's drawn position; and slowed the tongue flick to match
the higher frame rate.

## 11. Made the snake explode when it hits a wall
When the head smacks a wall, the snake now **bursts into 80 colourful flying
particles** at the point of impact, which fly outward, fall under gravity, and
fade away before the *Game Over* screen. Added `particles`, `exploded`, and the
`explode()`, `updateParticles()`, and `drawParticles()` functions.
*(Running into its own body is still a plain game over — no explosion.)*

## 12. Made it a colour-changing rainbow snake
The snake's colour now comes from a **rainbow hue that flows down its body and
shifts over time** (a full colour cycle about every 3 seconds). Built with HSL
so the 3D shading, scales, and glossy spine still work on every colour. Added
the `snakeHue()` helper and switched the body layers and head to rainbow colours.
The eyes, tongue, and raspberries kept their fixed colours.

## 13. Renamed the file
Renamed `snake.html` → **`Miles snake game.html`** (kept the `.html` ending so it
still opens as a game).
*(Note: the browser tab title and on-screen heading still read "Snake 🐍".)*

## 14. Snake speeds up as it eats
The snake now gets **5 ms faster with every raspberry eaten**. It starts at
200 ms per step and speeds up with each bite, down to a top speed of **60 ms**
per step (so it can't become impossibly fast). The speed **resets to 200 ms**
when you restart. Added `START_MOVE_MS`, `MIN_MOVE_MS`, and a `moveMs` variable
that the eating logic decreases and the restart resets.

## 15. Added a special rainbow strawberry (worth 50 points)
Added **one** special strawberry to the board, worth **50 points** (versus 1
for a raspberry). There is only ever a single strawberry, and once it is eaten
it is **gone for the rest of the game** — it does not come back until you
restart. Like the raspberries, eating it makes the snake **longer** — but it
does **not** change the speed (only raspberries do that). It is drawn as a proper strawberry shape (rounded
shoulders, pointed bottom) with seeds and a green leafy crown, filled with a
shimmering **rainbow** so it stands out from the pink raspberries. Added the
`strawberry` variable, the `drawStrawberry()` function, and shared
`spotTaken()` / `randomFreeSpot()` helpers so the snake, raspberries, and
strawberry never overlap (this replaced the old `newRaspberrySpot()` helper).
