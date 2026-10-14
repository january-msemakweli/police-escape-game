# 🚔 Police Escape — Outsmart the Kidnapper

A turn-based graph puzzle inspired by a mobile game ad: *avoid the kidnapper and get the girl to the police station.*

**▶ Play it live: https://january-msemakweli.github.io/police-escape-game/**

## How to play

- The board is a graph of nodes connected by paths.
- Tap a **glowing node** next to the girl (👧) to move her one step along a path.
- After every move, the kidnapper (🥷) moves **one node toward her** along the shortest path.
- If he lands on her node, she's caught. Reach the node under the **police station** (🏛️) to win.
- The trick is deception: lure him down the wrong branch, then sprint for the station.
- Stuck? Press **💡 Hint** — a built-in solver shows the next move of a guaranteed escape route (if one still exists from your position).

## Features

- 6 hand-designed levels, each **verified solvable** by the game's own BFS solver before shipping
- Deterministic kidnapper AI (breadth-first shortest path, ties broken by node id) — the same rule drives gameplay and hints
- Animated movement, win/lose detection (including walking straight into him), move counter
- Level select with progress saved in `localStorage`
- Single self-contained `index.html` — no build step, no dependencies, works on mobile and desktop

## Run locally

```sh
python3 -m http.server 8000
# open http://localhost:8000
```

Or just open `index.html` in a browser.

## Make your own levels

Levels are plain data at the top of the script in `index.html`:

```js
{ name: "Level 7 · Your Level",
  nodes: [[x, y], ...],        // % coordinates, x 0-100, y 0-118
  edges: [[a, b], ...],        // node index pairs
  girl: 0, kidnapper: 5, goal: 2 }
```

Tip: paste a candidate level into the in-game `solve(adj, girl, kidnapper, goal)` function in a JS console — if it returns `null`, the level is impossible and needs a loop or a decoy branch.

## License

Original code and artwork-by-emoji in this repo are free to reuse (MIT). The concept was inspired by a third-party game advertisement; no assets from that ad are used.
