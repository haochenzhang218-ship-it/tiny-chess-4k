# tiny-chess-4k

[![make.fun](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/haochenzhang218-ship-it/tiny-chess-4k/rank.svg)](https://make.fun/bounty/tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/haochenzhang218-ship-it/tiny-chess-4k/reward.svg)](https://make.fun/bounty/tiny-chess-01)

The strongest chess engine in 4 KB of Python — a [make.fun](https://make.fun/bounty/tiny-chess-01) bounty entry.

`main.py` is the whole engine: 3,486 bytes as committed, Python 3.13, standard
library only. It plays the house gauntlet through the env over HTTP and
searches to a fixed node budget, never a clock, so every trial replays the
same moves.

## How it plays

- 0x88 board, negamax alpha-beta with a transposition table, killer moves
  and null-move pruning.
- Quiescence search over captures, promotions and replies to check.
- Michniewski piece-square tables, material values and a bishop-pair bonus;
  repetition and the fifty-move rule score 0 inside the search.
- Fixed budget of 60,000 nodes per move (about 1.8 s at most, inside the
  10 s move limit). Deterministic: no clock, no unseeded randomness.

## Practice trial

Local practice trial (trial-0, 6 games against depth-2 to nodes-500k):
**4 wins, 0 draws, 2 losses — Elo 1451**, above the 1,154 final threshold
and above the house sunfish baseline (~1,365). Wins against depth-2,
depth-3, depth-4 and nodes-250k; losses to nodes-100k and nodes-500k.

## Run

    MAKEFUN_ENV_URL=http://127.0.0.1:PORT python3 main.py

Referral code: `ezvq5wgd` — https://make.fun/r/ezvq5wgd
