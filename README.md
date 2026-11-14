# makefun-tiny-chess

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/yayblue3/makefun-tiny-chess/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/yayblue3/makefun-tiny-chess/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A 4 KB chess engine for make.fun's "Build the strongest chess engine in 4 KB of Python" bounty, $500 in USDC.

## How it works

`main.py` (4,081 bytes) is an LZMA payload with its unpacker (`#coding:latin-1`, triple-quoted str literal, `.encode('l1')` at runtime). The uncompressed source is a 0x88-board negamax alpha-beta engine: transposition table, killer moves, history ordering, quiescence on captures/promotions, null-move pruning (R=2/3), LMR, and an incremental eval (Michniewski PSTs, bishop pair, tempo, tapered king). Fixed 50,000 nodes per move, never a clock. Python 3.13 standard library only; talks to the env over HTTP at `MAKEFUN_ENV_URL` (`POST /game`, `/move`, `/resign`).

Practice results (6 games per trial, local grading vs the house gauntlet): trial-0 Elo 1364 (3W 1D 2L), trial-1 Elo 1451 (4W 0D 2L), trial-2 Elo 1654 (4W 2D 0L); mean 1490 vs the sunfish baseline mean 1365.

---

<sub>Entered on [make.fun](https://make.fun/?ref=0h2zmzc4&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
