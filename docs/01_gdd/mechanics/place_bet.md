Bets are placed by dragging a [bet_card](bet_card.md) on a [bot](bot.md) in the [betting_scene](betting_scene.md).
Placing a bet consumes player's money equal to the cost of the [bet_card](bet_card.md).
The player can place a bet only if they have more or equal money than the cost of the [bet_card](bet_card.md).
When a bet is placed a [placed_bet](placed_bet.md) is created and assigned to the selected [bot](bot.md).
The value of the [placed_bet](placed_bet.md) is equal to the bet value of the [bet_card](bet_card.md).
The odds of the [placed_bet](placed_bet.md) are set to the odds of the [bot](bot.md) at the moment of placing the bet.