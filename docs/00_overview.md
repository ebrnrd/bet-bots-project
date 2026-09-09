## 1. Game Overview

Bet Bots is a linear narrative simulation game about a person addicted to betting on robot fights. The player manages their character's finances by placing bets on bots in a championship, while navigating the slow, quiet consequences of that addiction on their family life.

The tone is ironic but sad — rooted in the absurdity of hyper-individualistic, hyper-capitalistic society. The game never lectures the player. It makes the betting feel great, and lets everything else do the moral work.

A crucial detail about the game's world: the bots are not repurposed machines or gladiators with lives outside the ring — they are a manufactured spectacle. A fake sport created entirely to give people something to bet on. The championship treats itself with complete seriousness — complete with scandals, rivalries, aging careers, contract disputes, and arrests — despite being a product designed purely for consumption. This is the core absurdity the game lives in. The hyper-capitalistic world has commodified even the addiction itself.

The game opens with a single line that sets the tone immediately:

> _"You 'found' $20 in your child's piggy bank."_

## 2. The Central Metaphor — The Screen

Everything in the game happens on one screen: a website. The betting, the bot roster, the family events, the life simulation — all of it arrives through the same interface. The character never looks away.

This is not a UI compromise. It is the game's core statement. The world outside the screen is being filtered through the screen. The family only exists to this person as notifications interrupting their session. The screen is the addiction made visible.

Key sections of the website:

- Live betting — the active fight, shifting odds, and bet placement
- Standings — the championship leaderboard and upcoming matchups
- Notifications — where family events and life simulation choices interrupt the session

## 3. Reference Titles

- Papers, Please — tone, moral pressure, systemic irony, consequence-driven endings
- Don't Feed the Monkeys — voyeuristic simulation, passive observation of a living world

## 4. Design Pillars

These three pillars are the design filter for all decisions. When evaluating a feature, system, or mechanic, ask: does this serve at least one pillar? If not, it probably doesn't belong.

### Pillar 1 — "The Pull Is Real"

The betting is genuinely, unironically fun. The math always makes sense, and every bad decision feels financially justified in the moment. The game never winks at the player about the betting being bad. It makes the betting feel great — and lets the family system do the moral work quietly in the background. The player has to want to place one more bet.

### Pillar 2 — "The World Runs Without You"

The bots evolve, the championship has its own momentum, the family has its own needs. The player is not the main character of any of these systems. They are an observer trying to read and exploit a world that doesn't care about them. The player's role is to understand patterns and exploit them — not to control outcomes.

### Pillar 3 — "Everything Has a Cost"

Within a run, nothing is free. Money, family trust, a child's mood — everything shifts with every decision. The run ends when the cost becomes too high. There is no clean slate mid-run. A missed recital, a stolen $20, an unpaid loan — these leave marks that change how the family behaves, what they say, and what they stop saying.

## 5. Game Structure

### Format

Bet Bots is a linear, authored experience, with some roguelike elements. One playthrough tells one complete story across three months. Replayability comes from exploring different outcomes and discovering the consequences of different key decisions, and by trying to defy the randomness that the bots encounters generate. Winning bets must be possible, but not too obvious/easy.

### Scope

- Target playtime: 3 hours per run
- Three months, each functioning as a distinct chapter with its own emotional arc
- Solo developer scope — small enough to actually finish
- Each month is approximately one hour of gameplay
- Rent day closes each chapter — a moment of reckoning, not a game over

### The Three-Month Arc

The run follows a deliberate emotional escalation. The numbers get bigger in both directions each month — larger bets, larger winnings, but also larger costs and higher stakes family consequences. The player should always feel like they are operating close to the edge regardless of how much they have accumulated.

**Month 1 — Learning the Language.** Calm, recovering from the game's opening. Small bets, forgiving life events, the player finds their footing. The championship is ticking quietly. Safety nets are available but have future costs. Fragile optimism. The bots have short move sequences and few traits, making them somewhat predictable.

**Month 2 — The Sweet Spot.** The addiction fantasy peaks. The player has accumulated knowledge about the bots and starts betting with genuine confidence. Money is flowing. But costs are scaling — rent is higher, family events are more demanding, new bots are entering the roster. The player feels powerful but slightly out of control. The family is showing early cracks that are easy to ignore because the betting is going well.

**Month 3 — The Gap Opens.** The player is bigger, the numbers are bigger, but something is off. Family consequences from months 1 and 2 begin surfacing in unexpected ways. The championship reaches its climax. The player faces genuinely hard choices between financial gain and family stability. Everything converges on an ending.

### The Monthly Shape — A Template

Each month follows a consistent internal structure. The content changes across months — harder bots, heavier family events, bigger numbers — but the shape stays constant so the player can internalise the rhythm and plan against it.

- Days 1-7: Breathing room. Calm opening, small bets, forgiving events. The player orients.
- Days 8-14: Pressure builds. Family events get heavier, odds get harder to read as the bot roster evolves.
- Day ~14: The mid-month hit. A mandatory cost lands. The player now has a target to recover before rent.
- Days 15-21: The recovery arc. The player is chasing a number. The most interesting betting decisions happen here.
- Days 22-28: Final stretch. Rent is visible on the calendar. Fight opportunities are running out. An unscheduled fight may appear as a last high-stakes opportunity. Rent day closes the chapter.

### Fight Schedule

Fights occur roughly every other day as the backbone of the month. The schedule is not rigidly fixed — it has two layers:

- Scheduled fights — the regular backbone, visible on the calendar in advance, giving the player information to plan against
- Unscheduled fights — occasional surprise bouts triggered by tabloid drama, makeup matches, or championship emergencies. Not on the calendar until they appear. Often come with unusual odds or stakes.

Unscheduled fights are a natural delivery mechanism for collision points — a surprise high-stakes fight appearing on the same day as a family event is more dramatically compelling than a predictable scheduled one.

### Non-Match Days

On days with no fights, the chunk system does not apply. Non-match days are purely narrative — a text event or two advances the family story and the day passes. The game does not pretend to be a betting game when there is nothing to bet on.

### Feedback Timing

Player actions must produce feedback at two distinct speeds, strongly weighted toward immediacy:

- Immediate — something visible happens within the same session, often the same day. Steal the $20, the child is visibly sad that evening.
- Delayed — consequences that compound quietly and surface later as revelations rather than punishments. A relationship neglected for weeks that suddenly breaks in an unexpected moment.

Never let a player action go more than a few minutes without some kind of reaction from the world.

### Collision Points

A collision point is a moment where the family world and the championship world crash into each other, forcing a single decision with consequences in both systems simultaneously. These are the dramatic peaks of each month — the moments where Pillar 1 and Pillar 3 are in direct conflict.

Mechanically a collision point needs two ingredients: a time limit and a forced choice. The simplest implementation is a day where both a significant fight and a significant family event compete for the same chunks of time. The player can attend fully to one, not both.

For a fight to be worth sacrificing something for, it needs visible significance:

- Championship relevance — a fight with standings implications
- Odds opportunity — a high public attention fight where the player has an informational edge
- Unscheduled urgency — a surprise fight that won't recur

### Endings

The ending is shaped by the accumulated state of the run across two macro axes and a set of key narrative decisions:

- Financial axis — did the player sustain themselves across all three months?
- Family axis — what is the overall state of the family by month 3?
- Key decisions — specific moments that left permanent marks on the narrative state (e.g. the shady loan, the missing TV, the stolen $20)

Two players who both paid rent every month could arrive at meaningfully different endings based on the texture of their choices. Endings share structural similarities but differ in details, dialogue, and silences.

_⚠ The specific key narrative decisions and ending states are to be defined in a dedicated narrative design session._