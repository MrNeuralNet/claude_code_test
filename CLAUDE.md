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
- Commit every meaningful change with a concise imperative subject line, then push: `git push`
- Keep commits focused — one logical change per commit so history stays easy to revert
