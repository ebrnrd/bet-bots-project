# dependencies
- [bots_simulation_system](01_gdd/systems/bots_simulation_system.md)
# variables
## match_timer
- default value: 0
- description: the running timer of the match
## max_match_timer
- default value: 120
- description: the max length of a match in ticks.
## match_tick_interval
- default value: 500
- description: how much time (in milliseconds) passes between ticks
# overview
Bot matches are always 1v1.
Bots fight on a 2D field composed by 5 horizontal tiles on which they can move.
At the start of the match one bot gets placed to the left of the ring, the other on the right of the ring. 
Bots fight by performing [bot_moves](#bot_moves), looping their [moves_sequence](01_gdd/elements/bot.md#moves_sequence) at a fixed interval (ticks). Bots perform moves at the same time.
# bot_moves
## Overview
Moves are the actions the [bots](01_gdd/elements/bot.md) perform during the match.
Each bot has a certain amount of [stamina](01_gdd/elements/bot.md#stamina) that each move can consume or recover. When the bot's stamina reaches 0 an [Empty move](#Empty) gets inserted between the current and the next move in the bot's moves sequence for that loop.
## Attack
Deals 1 damage if the opponent is in the adjacent tile and they are not using a Defend move. Consumes 1 Stamina.
## Defend
Prevents damage.
Doesn't consume Stamina.
## Dash
If the opponent is not in the adjacent tile moves closer by 1, if the opponent is in the adjacent tile moves further by 1. If both bots perform a move closer on the same tile, they hit each other, take 1 damage and move back to the tile they came from.
Recovers 1 Stamina.
## Random
Randomly performs an Attack, a Defend or a Dash, it changes at each loop.
## Empty
Recovers 1 Stamina.
# bot_traits
Passive modifiers that change how the bot behaves during the matches.
They can be:
- Positive: Influencing in a positive way the bots behaviour
- Negative: Influencing in a negative way the bots behaviour
The assignment of traits is controlled by the [bots_simulation_system](01_gdd/systems/bots_simulation_system.md).
# match_time
The match time is controlled by a regular signal that fires every [match_tick_interval](#match_tick_interval) seconds.
When the tick signal is fired, both bots perform their moves and the [match_timer](#match_timer) progresses by 1 tick.
When the [match_timer](#match_timer) reaches the [max_match_timer](#max_match_timer) and all the bots are still fighting, the match ends.
# match_rules
The fight ends when one of these conditions is true:
- One or both bots reach 0 [health](01_gdd/elements/bot.md#health)
	- If one both is KO the winner is the bot still standing
	- If both bots gets KO the match results in a draw.
- The match timer reaches [max_match_timer](#max_match_timer).
	- If bots have different healths the winner is the bot with more health
	- If bots bots have the same health the match results in a draw.