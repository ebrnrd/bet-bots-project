Governs how the player places bets on fights and how bets resolve into payouts. Odds are calculated by [odds_calculation_system](odds_calculation_system.md); the bet card deck and reward loop are handled by [bet_cards_system](bet_cards_system.md).
# Dependencies
* [time_system](01_gdd/systems/time_system.md)
* [economy_system](01_gdd/systems/economy_system.md)
* [bots_simulation_system](01_gdd/systems/bots_simulation_system.md)
* [bots_fighting_system](01_gdd/systems/bots_fighting_system.md)
* [odds_calculation_system](01_gdd/systems/odds_calculation_system.md)
* [bet_cards_system](01_gdd/systems/bet_cards_system.md)
* [passive_items_system](01_gdd/systems/passive_items_system.md)
# Variables
## max_bets_per_bot
* default value: 1
* description: the total number of different bets the player can place on a single bot in a particular match.
# Placing bets
The player can place bets only on planned matches that are yet to happen.
The player places bets on bots in the [betting_scene](01_gdd/scenes/betting_scene.md) by [placing a bet](01_gdd/mechanics/place_bet.md).
The player can place multiple bets on the same bot in the same match, limited by [max_bets_per_bot](#max_bets_per_bot).
A [placed bet](placed_bet.md)'s odds are locked to the bot's current odds — see [odds_calculation_system](01_gdd/systems/odds_calculation_system.md) — at the moment the bet is placed.
# Resolving bets
When a bot match is resolved:
* If the player bet on the winning bot, they receive an amount of money equal to the bet value multiplied by the [placed_bet](01_gdd/elements/placed_bet.md)'s locked odds.
* If the player bet on the losing bot, they gain no money.
* If the match results in a draw, the player gets back the money they bet.
* All of the outcomes above can be modified by [placed_bet](01_gdd/elements/placed_bet.md) effects or [passive_items_system](01_gdd/systems/passive_items_system.md).
# Open questions
* Betting cutoff — can a bet be placed right up to the fight's chunk, or does the window close earlier?
	* When a time chunk is occupied by a fight it isn't possible to bet on any fights.
* Withdrawing a bet — can a placed bet be cancelled before the match resolves?
	* No, unless a [placed_bet](placed_bet.md) effect or [passive_item](passive_item.md) says otherwise.
* [bet card](bet card.md) cost vs. bet value — is the card's cost always equal to its payable bet value, or can they differ (leverage/discount cards)? Needs defining in [bet card](bet card.md).
* [placed bet](placed bet.md) effects and [passive_item](passive_item.md) — referenced here as payout modifiers but neither is defined anywhere yet.
* Terminology check — confirm "the bot's rank" here and "standings_weight" in [odds_calculation_system](odds_calculation_system.md) refer to the same thing, and use one term consistently.
* [00_overview](00_overview.md) contradiction — the overview states the card constraint system was removed in favor of world-based constraints, but this system and [bet_cards_system](bet_cards_system.md) describe an active card economy. Needs reconciling before this is build-ready: did the design move back toward cards, or is the overview out of date?