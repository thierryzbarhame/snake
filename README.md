# Snake Game

## Overview

This is a browser-based Snake game, developed as an Advanced Programming
course project using a vibe-coding approach: the game was built and refined
entirely through natural-language prompts, iterative testing, problem
identification, and agent-assisted implementation, without manually writing
or editing source code.

## Features

### Gameplay

* Classic Snake gameplay.
* Continuous snake movement.
* Arrow-key controls.
* Random food generation.
* Snake growth after eating food.
* Score tracking.
* Wall collision detection.
* Self-collision detection.
* Game Over state.
* Restart functionality.

### Snake Design

* Redesigned the snake to look more like a real snake.
* Distinct snake head.
* Visible eyes.
* Recognizable snake body.
* Tapered/visually distinct tail.
* Direction-aware head that points toward the current movement direction.
* Improved visual distinction between the snake and the game board.

### Full-Screen Experience

* Full-screen game layout.
* Game designed to fit within the browser viewport.
* Removed unnecessary vertical scrolling.
* Removed unnecessary horizontal scrolling.
* Responsive layout for different browser window sizes.
* Game board and interface remain visible without requiring page scrolling.

### Difficulty and Speed System

The game uses a progressive difficulty system based entirely on the current
score:

* Level 1: Score 0–499
* Level 2: Score 500–999
* Level 3: Score 1000–1499
* Level 4: Score 1500–1999
* Level 5: Score 2000–2499
* The level continues to increase every additional 500 points.

Behavior of the system:

* The game starts at Level 1.
* The starting score is 0.
* The initial speed is deliberately very slow, giving the player time to
  learn the controls.
* Speed increases progressively as the player reaches higher levels.
* Speed remains consistent within each level and only changes when a new
  500-point threshold is crossed.
* Restarting the game resets the score, level, and speed back to their
  initial values.

### User Interface

* Clear score display.
* Clear level display, shown alongside the score.
* Redesigned Game Over screen.
* Clearly visible restart control.
* On-screen instructions for the controls.
* Overall polished visual presentation (board, food, and status panels).
* Improved typography, spacing, and layout throughout.

## Technical Characteristics

* The game runs directly from `index.html`.
* No backend is required.
* No database is required.
* No build process is required.
* No external server is required.
* The project is fully self-contained.
* The game uses standard browser technologies: HTML, CSS, and JavaScript.
* All project files are contained inside this repository.

## Testing

The game was tested through actual gameplay rather than automated test
suites. Testing covered:

* Starting the game.
* Keyboard controls.
* Food collection.
* Snake growth.
* Score updates.
* Level progression.
* Speed progression.
* Collision detection (walls and self).
* Game Over.
* Restart.
* Full-screen layout.
* Absence of page scrolling.
* Final visual appearance.

## Vibe Coding Development Process

The game was built through an iterative, prompt-driven process:

1. Initial game implementation.
2. Play-testing.
3. Identification of issues through gameplay.
4. Natural-language prompts describing the observed problems.
5. Agent implementation of requested changes.
6. Re-testing.
7. Further refinement.
8. Final validation.

The development process relied on natural-language instructions rather than
manually editing the source code.

## Project Structure

```
snake/
├── index.html
├── NOTES.md
├── README.md
└── .gitignore
```

## How to Run

1. Clone or download the repository.
2. Open `index.html` in a modern web browser.
3. Start playing using the arrow keys.

## Controls

* ↑ Up
* ↓ Down
* ← Left
* → Right

## Final Result

The final result is a complete, playable Snake game featuring progressive
difficulty, a responsive full-screen presentation, and an improved,
snake-like visual design.
