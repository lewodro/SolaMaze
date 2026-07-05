<div align="center">

# SolaMaze

**A competitive 3D web maze game with Solana-based rewards.**

![TypeScript](https://img.shields.io/badge/typescript-%23007ACC.svg?style=for-the-badge\&logo=typescript\&logoColor=white) ![GitHub Actions](https://img.shields.io/badge/github%20actions-%232671E5.svg?style=for-the-badge\&logo=githubactions\&logoColor=white) ![Solana](https://img.shields.io/badge/solana-%239945FF.svg?style=for-the-badge\&logo=solana\&logoColor=white) [![Gem Version](https://badge.fury.io/rb/x402-payments.svg)](https://badge.fury.io/rb/x402-payments) ![Vivaldi](https://img.shields.io/badge/Vivaldi-EF3939?style=for-the-badge\&logo=Vivaldi\&logoColor=white)

<br />

Players race through procedurally generated 3D mazes directly in the browser.
The x402 payment architecture enables pay-per-play entry in SOL, while winners compete for prize pool rewards.

**SolaMaze is a competitive real-time 3D maze racing platform built for browser gameplay, Solana micropayments, and reward-based competition.**

</div>

---

## ░░ OVERVIEW

SolaMaze combines deterministic game logic, real-time multiplayer synchronization, and Solana-based payments into one competitive web game.

Each match uses a reproducible maze seed, allowing every player to compete in the same environment under fair conditions. Players connect a wallet, pay to enter, race to the exit, and compete for rewards based on performance.

---

## ░░ TECHNOLOGY STACK

| Layer      | Technologies                                                  |
| ---------- | ------------------------------------------------------------- |
| Frontend   | React, Three.js, React Three Fiber, Zustand, WebSocket client |
| Backend    | Node.js, Fastify or Express, WebSocket server, PostgreSQL     |
| Blockchain | Solana, x402 micropayments, Phantom, Solflare                 |

---

## ░░ CORE FEATURES

| Area        | Features                                                         |
| ----------- | ---------------------------------------------------------------- |
| Gameplay    | Procedural 3D mazes, deterministic seeds, first-to-finish racing |
| Multiplayer | Real-time synchronization, game rooms, race state broadcasting   |
| Payments    | Pay-per-entry in SOL, x402 verification, prize pool rewards      |
| Data        | Player profiles, match history, global and match leaderboards    |

---

## ░░ GAME FLOW

```txt
Wallet Connect → Entry Request → Payment Request → SOL Transaction → Payment Verification → Game Room Join → Maze Race → Results Stored → Rewards Distributed
```

---

## ░░ API DESIGN

Base path:

```txt
/api/v1
```

| Category     | Endpoints                                               |
| ------------ | ------------------------------------------------------- |
| Games        | POST /games/create · POST /games/join · GET /games/{id} |
| Payments     | POST /payments/verify                                   |
| Leaderboards | GET /leaderboard/global · GET /leaderboard/{gameId}     |
| Players      | GET /players/{id}                                       |

---

## ░░ GAME ENGINE

The `game-core` package handles deterministic gameplay logic shared between the client and server.

| System          | Responsibility                                      |
| --------------- | --------------------------------------------------- |
| Maze Generation | DFS, Prim’s Algorithm, seed-based reproducibility   |
| Movement        | Collision detection, movement limits, validation    |
| Scoring         | Time tracking, finish detection, result calculation |

---

## ░░ REAL-TIME LAYER

The WebSocket layer manages player connections, room creation, matchmaking, position updates, countdown events, race progress, completion events, and final result broadcasting.

The client receives game state transitions, live player updates, maze data, progress events, and final leaderboard results.

---

## ░░ DATABASE MODEL

Primary tables:

```txt
players
games
sessions
leaderboards
transactions
```

---

## ░░ COMPETITIVE INTEGRITY

SolaMaze is designed around fair, reproducible competition. Critical gameplay logic is shared between client and server, while the server validates movement, race progress, finish events, payments, and final results.

---

## ░░ PROJECT STATUS

SolaMaze is currently an experimental multiplayer Web3 gaming project focused on competitive browser-based maze racing, Solana payments, and reward distribution.

---

<div align="center">

**SolaMaze — race the maze, win the pool.**

</div>
