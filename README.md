# SolaMaze

# development in process

![TypeScript](https://img.shields.io/badge/typescript-%23007ACC.svg?style=for-the-badge&logo=typescript&logoColor=white) ![GitHub Actions](https://img.shields.io/badge/github%20actions-%232671E5.svg?style=for-the-badge&logo=githubactions&logoColor=white) ![Solana](https://img.shields.io/badge/solana-%239945FF.svg?style=for-the-badge&logo=solana&logoColor=white) [![Gem Version](https://badge.fury.io/rb/x402-payments.svg)](https://badge.fury.io/rb/x402-payments) ![Vivaldi](https://img.shields.io/badge/Vivaldi-EF3939?style=for-the-badge&logo=Vivaldi&logoColor=white)

A competitive 3D web maze game with Solana-based rewards. 

Players navigate through procedurally generated 3D mazes in their browser, racing to reach the exit. The x402 payment architecture allows players to pay-per-play in SOL, with winners earning prize pool rewards. The backend manages game rooms, leaderboards, player scores, and payment verification.

# SOLAMAZE

A competitive, real-time 3D maze racing platform built for the browser, integrating Solana-based micropayments and reward distribution.

---

## ───────────────────────────────
## ░░ OVERVIEW
## ───────────────────────────────

SolaMaze is a multiplayer 3D maze racing system where players compete to reach the exit of procedurally generated environments. Each match is economically incentivized through a pay-per-play model, with rewards distributed to top performers.

The system is designed to combine:
- Deterministic game logic for fairness
- Real-time synchronization for competitive integrity
- Blockchain-based payments for trustless reward handling

---

## ───────────────────────────────
## ░░ CORE FEATURES
## ───────────────────────────────

[ GAMEPLAY ]
- Procedurally generated 3D mazes
- First-to-finish competitive structure
- Deterministic seeds for reproducibility

[ MULTIPLAYER ]
- Real-time player synchronization via WebSockets
- Server-authoritative movement validation
- Race state broadcasting (start, progress, finish)

[ PAYMENTS ]
- Pay-per-entry model using Solana
- Micropayment processing via x402 protocol
- Trust-minimized reward distribution

[ DATA ]
- Persistent player profiles
- Global and per-match leaderboards
- Historical match tracking



---

## ───────────────────────────────
## ░░ TECHNOLOGY STACK
## ───────────────────────────────

[ FRONTEND ]
- React
- Three.js
- React Three Fiber
- Zustand (state management)
- WebSocket client

[ BACKEND ]
- Node.js runtime
- Fastify or Express (API layer)
- WebSocket server (real-time engine)
- PostgreSQL (data persistence)

[ BLOCKCHAIN ]
- Solana network
- x402 micropayment protocol
- Wallet adapters (Phantom, Solflare)

---

## ───────────────────────────────
## ░░ GAME FLOW
## ───────────────────────────────

1. Player connects a Solana wallet
2. Client requests entry into a game session
3. Server generates a payment request
4. Player submits transaction
5. Server verifies payment via x402
6. Player joins active game room
7. Maze race begins
8. Results are computed and stored
9. Rewards are distributed

---

## ───────────────────────────────
## ░░ API DESIGN (OPENAPI)
## ───────────────────────────────

Base path:


[ GAME ENDPOINTS ]

/api/v1


[ GAME ENDPOINTS ]


POST /games/create
POST /games/join
GET /games/{id}


[ PAYMENT ENDPOINTS ]


POST /payments/verify


[ LEADERBOARD ENDPOINTS ]


GET /leaderboard/global
GET /leaderboard/{gameId}


[ PLAYER ENDPOINTS ]


GET /players/{id}


---

## ───────────────────────────────
## ░░ GAME ENGINE DETAILS
## ───────────────────────────────

The `game-core` package is responsible for deterministic gameplay logic:

- Maze generation algorithms:
  - Depth-First Search (DFS)
  - Prim’s Algorithm
- Seed-based reproducibility
- Collision detection
- Movement constraints
- Time tracking and scoring

All critical game logic is shared between client and server to ensure consistency.

---

## ───────────────────────────────
## ░░ REAL-TIME LAYER
## ───────────────────────────────

WebSocket server responsibilities:

- Player connection lifecycle
- Room creation and matchmaking
- Position synchronization
- State broadcasting:
  - Countdown
  - Race start
  - Player progress
  - Completion events

Client receives:
- Player position updates
- Game state transitions
- Final results

---

## ───────────────────────────────
## ░░ DATABASE MODEL
## ───────────────────────────────

Primary tables:


players
games
sessions
leaderboards
transactions
