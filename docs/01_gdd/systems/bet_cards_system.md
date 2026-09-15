Governs the bet card deck: how cards are drawn, shuffled, and added to the player's deck as end-of-day rewards.
# Dependencies
- [time_system](01_gdd/systems/time_system.md)
- [betting_system](01_gdd/systems/betting_system.md)
- [economy_system](01_gdd/systems/economy_system.md)
# Variables
## player_hand_size
- default value: 3
- description: the number of [bet cards](01_gdd/elements/bet_card.md) the player draws at the start of each day.
## max_bet_cards_reward
- default value: 3
- description: the total number of [bet cards](01_gdd/elements/bet_card.md) the player can choose from in the bet_cards_reward_scene at the end of each day.
# Deck and hand
Bets are represented by [bet card](bet card.md)s. At the beginning of each day, the player's deck is shuffled and a hand is drawn equal to [player_hand_size](#player_hand_size). The player cannot draw new cards during the day. Bet cards are only shown and interactable in the [betting_scene](betting_scene.md).
# Adding cards to the deck
When each day ends, the player can add 1 [bet card](bet card.md) to their deck ([add bet card to deck](add bet card to deck.md)) by choosing from [max_bet_cards_reward](#max_bet_cards_reward) options in the [bet_cards_reward_scene](bet_cards_reward_scene.md).
# Open questions
- What happens to unplayed cards left in hand at day's end — discarded, returned to the deck, or carried into tomorrow's hand?
	- At the start of each day all the cards of the player are shuffled, this means also the one that were in their hand the previous day.
- Is there a maximum deck size, or does it grow indefinitely across the 3-month run?
	- No maximum deck size.