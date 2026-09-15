# dependencies
- [time_system](01_gdd/systems/time_system.md)
- [bots_fighting_system](/01_gdd/systems/bots_fighting_system.md)
# variables
## bots_number_on_new_game
- default: 8
- description: the number of bots already in the championship at the start of a new game.
# overview
This system describes how the bots in the game are generated, what can happen to them during the season, how they can change and how it affects the player.

At the start of a new game, [a number](#bots_number_on_new_game) of [bots](01_gdd/elements/bot.md) are [generated](#generation). These bots are competing in a fighting championship that lasts 1 season. The bot ranked 1 at the end of the season is crowned Grand Champion and a new season starts.
# generation
[bots](01_gdd/elements/bot.md) are generated following predetermined [archetypes](01_gdd/content/bot_archetypes_database.base), different recipes that influence the different stats of the bots. These archetypes have different values:
- health range: how much [health](01_gdd/elements/bot.md#health) the generated bot can have. It is a random value in the range specified.
- stamina range: how much [stamina](01_gdd/elements/bot.md#stamina) the generated bot can have. It is a random value in the range specified.
- attacks: how many [attack moves](01_gdd/systems/bots_fighting_system.md#Attack) the bot has in their [moves sequence](01_gdd/elements/bot.md#moves_sequence). It is a random value in the range specified.
- defends: how many [defend moves](01_gdd/systems/bots_fighting_system.md#Defend) the bot has in their [moves sequence](01_gdd/elements/bot.md#moves_sequence). It is a random value in the range specified.
- dashes: how many [dash moves](01_gdd/systems/bots_fighting_system.md#Dash) the bot has in their [moves sequence](01_gdd/elements/bot.md#moves_sequence). It is a random value in the range specified.
- randoms: how many [random moves](01_gdd/systems/bots_fighting_system.md#Random) the bot has in their [moves sequence](01_gdd/elements/bot.md#moves_sequence). It is a random value in the range specified.
- possible traits: a list of possible [traits](01_gdd/systems/bots_fighting_system.md#bot_traits) the bot can have. Only 1 trait is selected when generating a new bot.
When generating a new bot, a random archetype is chosen and the stats of that bot are generated following the archetype recipe.
## generating_bot_info
Each generated bot has also a unique [name](elements/01_gdd/elements/bot.md#name)
# mutation
# matchmaking
