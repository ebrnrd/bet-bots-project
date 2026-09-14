# dependencies
- [time_system](time_system.md)
# variables
## bots_number_on_new_game
- default: 8
- description: the number of bots already in the championship at the start of a new game.
# overview
This system describes how the bots in the game are generated, what can happen to them during the season, how they can change and how it affects the player.

At the start of a new game, [bots_number_on_new_game](#bots_number_on_new_game) bots are [generated](#generation). These bots are competing in a fighting championship that lasts 1 season. The bot ranked 1 at the end of the season is crowned Grand Champion and a new season starts.
# generation
# matchmaking