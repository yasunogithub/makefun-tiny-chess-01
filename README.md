# makefun-tiny-chess-01

An original chess engine in 4 KB of Python for make.fun's tiny-chess-01.

`main.py` (3,987 bytes) is the whole engine: an lzma-packed payload with
its unpacker, as the rules allow. The unpacked source is a 0x88-board
negamax engine written for this competition:

- alpha-beta search with a transposition table, iterative deepening to a
  fixed node budget (80k / 50k / 25k nodes by game ply), never a clock
- quiescence search over captures, promotions and check evasions
- null-move pruning, late-move reductions, check extensions
- move ordering: TT move, MVV-LVA captures, killers, history heuristic
- evaluation: material, piece-square tables (middlegame and endgame king
  tables), bishop pair, doubled-pawn penalty

Deterministic: the same position always gets the same move, so replays
match. No model calls. Python 3.13 standard library only.

Local practice results (kit practice trials, 6 games each):
trial-0 Elo 1451 (3W 2D 1L), trial-1 Elo 1279 (2W 2D 2L).

MIT licensed; not a fork of any existing engine.
