# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project overview

A single-file, zero-dependency Tic-Tac-Toe game (`tictactoe.html`). Everything — HTML structure, CSS styles, and game logic — lives in that one file. Open it directly in a browser; no build step, no server, no package manager.

## Architecture

The game logic is split into three layers, all inside the `<script>` tag:

- **State** — `board` (9-element array, `null | 'X' | 'O'`), `current` (active player), `over` (boolean), `scores` object, and `mode` (`'human' | 'ai'`).
- **AI** — unbeatable minimax in `minimax(b, isMax)` + `bestMove()`. The AI always plays as `O`; positive score = O advantage, negative = X advantage.
- **DOM layer** — `applyMove(i)` is the single entry point for placing a mark; it mutates state, updates the DOM, and triggers the AI turn via `setTimeout(aiMove, 350)` when in AI mode.

Win detection uses the hard-coded `WINS` array of 8 triplets (rows, columns, diagonals). `checkWin(b)` returns the winning triplet or `null`.

## Git & GitHub

- Remote: `https://github.com/MrNeuralNet/claude_code_test` (branch `main`)
- **Commit and push after every meaningful unit of work** — a new feature, a bug fix, a refactor, or a significant edit all warrant their own commit. Never leave completed work uncommitted.
- Use a concise imperative subject line (e.g. `Add win animation`, `Fix AI move delay`). If the reason isn't obvious from the change itself, add a short body line explaining why.
- Keep commits focused — one logical change per commit so any individual change can be reverted cleanly.
- Push to `origin main` immediately after each commit: `git push`. The goal is that the remote always reflects the current state of the project so no work is ever at risk.
