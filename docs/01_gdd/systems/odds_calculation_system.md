
# TO UNSLOP!!!!

At the passing of each [time_chunk](time_system#time_chunk), the odds of all bots fighting that week are recalculated by blending two components: the bot's true skill probability and the public's perceived probability.
## Skill probability

Each bot has an elo rating that updates after every fight based on the outcome and the opponent's rating, following the standard elo formula. A bot's [trait](bots_fighting_system.md#bot_traits) each carry a fixed point value, positive or negative, and a bot's [moves_sequence](elements/bot.md#moves_sequence) is converted into a Moves Score. Both are added to the elo rating to produce an effective rating used only for odds calculation — not displayed on the leaderboard.

```
effective_rating(bot) = elo_rating(bot) + trait_points(bot) + moves_score(bot)
P_skill(A) = 1 / (1 + 10^((effective_rating(B) - effective_rating(A)) / 400))
```

Because [matchmaking](bots_simulation_system.md#matchmaking) pairs bots of similar elo, two bots can look nearly identical on the leaderboard while their effective ratings — and therefore the true skill probability — diverge meaningfully because of traits and moveset. This gap is intentional: it's what rewards a player who has learned a bot's traits and tendencies over one who only reads standings.
### Moves Score
The odds calculation never simulates an actual fight. It approximates a bot's threat the way a human oddsmaker would size up a matchup — from tendencies, not from playing it out. The real outcome is decided separately by the [[bots_fighting_system|Fight System]] when the fight happens, which is what allows genuine upsets against the predicted odds.

A bot's sequence is made of `attack`, `defend`, `move`, and `random` moves. Combined with the bot's health and stamina, these produce four sub-scores:

- **Damage Potential** — proportion of the sequence that is `attack` moves. How often this bot tries to hit.
- **Survivability** — the bot's health, normalized against the roster average. How much punishment it can absorb.
- **Endurance** — the bot's stamina relative to how often it attacks. Whether it can sustain its own aggression or risks running dry into an empty move.
- **Defensive Discipline** — proportion of the sequence that is `defend` moves. How often it blocks incoming damage.

A wildcard discount applies for unpredictability:

- **Unpredictability Discount** — proportion of the sequence that is `random` moves. An oddsmaker trusts a bot less when its behavior can't be read in advance, so this lowers the Moves Score slightly regardless of the bot's other stats.

```
moves_score(bot) = wA×DamagePotential + wS×Survivability + wE×Endurance + wD×DefensiveDiscipline − wR×UnpredictabilityDiscount
```

`wA, wS, wE, wD, wR` are tunable weights, balanced by feel rather than derived — same spirit as trait point values.

## Crowd probability

The crowd doesn't see effective rating — only standings and recent results. A bot's crowd weight is its standings weight, multiplied by a streak bonus that grows with consecutive wins (capped, to avoid runaway feedback), multiplied by any tabloid modifier from recent [[news_system|news]] events.

```
crowd_weight(bot) = standings_weight(bot) × (1 + streak_bonus(bot)) × tabloid_modifier(bot)
P_crowd(bot) = crowd_weight(bot) / (crowd_weight(bot) + crowd_weight(opponent))
```

The streak bonus exists so the crowd overreacts to a flashy recent run regardless of who it was against — the same win streak that barely moves a bot's true elo (if the opponents were weak) can still swing public money hard.

## Final odds

Each chunk, P_skill and P_crowd are blended into a single probability, and the displayed odds are the inverse of that probability.

```
P_final(bot) = blend(P_skill(bot), P_crowd(bot))
odds(bot) = 1 / P_final(bot)
```

## Open questions

- Blend weight between P_skill and P_crowd — not yet defined
- Standings weight formula (how leaderboard position converts to a number) — not yet defined
- Streak reset conditions — does a draw reset the streak, or only a loss?
- Streak bonus rate and cap — 8% per win / 40% cap used earlier as a placeholder, not tuned
- Moves Score weights (wA, wS, wE, wD, wR) and the scaling factor that brings Moves Score onto the same point range as elo — not yet tuned
- HP normalization baseline — roster average at time of calculation, or a fixed reference value?
- Endurance formula detail — needs a stamina cost per attack and a regeneration rate, both still undefined in [[bots_fighting_system]]
- Trait point values — to be authored per trait once the trait list exists
- Elo K-factor and starting rating for new roster replacements — not yet defined