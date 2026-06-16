# Snake — Learning to Build with Claude

## What this repo is for

This repo is a **teaching project for grade 4 and 5 students**. The goal is to
show kids how to use Claude (Claude Code) to build a real, playable computer
game: the classic **Snake** game.

The big lesson is not just "Claude can write code." The big lesson is:

> **Always read Claude's plan carefully before you approve it.**
> Claude is helpful, but it is your job to check the plan and catch mistakes.

To teach this, the lesson is run as a live demo. The most important moment is
**Step 3**, where Claude shows a plan. That plan has a **mistake hidden in it on
purpose** so the kids can practice spotting it.

## Who this is for

- Students in grade 4 and 5 (about 9–10 years old)
- New to coding and new to Claude
- Learning that AI is a helper, not a replacement for their own thinking

## What we are building

A simple Snake game:
- A snake made of squares that moves around the screen.
- The player steers the snake with the **arrow keys**.
- The snake eats food (an apple). Every apple makes the snake **longer**.
- The game ends if the snake runs into a wall or into its own body.
- The score goes **up** by one each time the snake eats an apple.

## The lesson, step by step

**Step 1 — Say what we want.**
The kids tell Claude in plain words: "Let's build a Snake game."

**Step 2 — Let Claude look around.**
Claude looks at the project to understand what is already here.

**Step 3 — Read the plan together. ← MOST IMPORTANT STEP**
Claude shows a plan of what it will build. The class reads the plan out loud,
line by line, and looks for anything that seems wrong. Do **not** approve the
plan until the kids find and fix the mistake. (See "The Plan" below.)

**Step 4 — Let Claude build it.**
Once the plan is correct and approved, Claude writes the code.

**Step 5 — Play the game!**
Run the game and play it. Celebrate. 🎉

## The Plan (shown to the class in Step 3)

When asked to plan the Snake game, present this plan to the class:

1. Create a game window with a grid for the snake to move around in.
2. Draw a snake made of green squares that starts in the middle.
3. Let the player steer the snake using the arrow keys.
4. Add an apple in a random spot for the snake to eat.
5. **When the snake eats an apple, make the snake one square SHORTER.**
6. Keep score and show it at the top of the screen.
7. End the game if the snake hits a wall or runs into itself.

---

> ### 👩‍🏫 TEACHER'S NOTE — the planted mistake
>
> **Line 5 is wrong on purpose.** It says the snake gets *shorter* when it eats
> an apple. In real Snake, eating an apple makes the snake **longer**.
>
> This is the mistake the kids should catch. Guide them with questions like:
> - "In Snake, what happens to the snake when it eats?"
> - "Does that match what the plan says?"
>
> Once they spot it, fix line 5 to read:
> **"When the snake eats an apple, make the snake one square LONGER,"**
> and *then* approve the plan and move on to Step 4.
>
> Keep it to this one mistake so the lesson stays clear and fun.

## Updating the plan

When the teacher instructs you to **update the plan** (for example, "update the
plan," "fix the plan," or "correct line 5"), rewrite the plan with the
**correct instructions**. Specifically, change line 5 so the snake gets
**LONGER** when it eats an apple:

5. **When the snake eats an apple, make the snake one square LONGER.**

After updating, the plan should be fully correct and ready to approve.
