# Tower of Cards

**Game Design Document — Version 1.2**
**Current design baseline • August 2026**

---

## 1. Purpose & Scope

This is the current design baseline for the **Tower of Cards** JavaScript RPG.

This is a living design document. Values and systems explicitly marked as tentative may change during playtesting.

The GDD describes what the game is, how its systems are intended to behave, and the relationships between those systems. It is primarily a development roadmap and design reference rather than a document that will necessarily survive unchanged into the finished game.

The project uses the Tower of Cards setting and player rules, excluding the later dungeon/core campaign material.

---

# 2. Core Concept & Loop

The player creates a protagonist, gathers a party, explores a Tower town, prepares for an expedition, enters a large hex-based Tower floor, discovers encounters and locations, collects cards, manages exhaustion, returns to town, recovers, and prepares another expedition.

The intended core loop is:

1. Create the protagonist and Soul Card.
2. Begin with a randomized/pre-made tutorial party on Floor 0.
3. Explore the Tower town and recruit/replace named NPCs or use mercenaries.
4. Prepare the party and optionally use the last-minute Tower shop.
5. Choose an accessible Tower floor.
6. Explore the floor and resolve monsters, treasure, puzzles, and special locations.
7. Find the staircase/obelisk progression point.
8. Leave the Tower for downtime and recovery.
9. Manage town activities, rumors, party availability, and recruitment.
10. Prepare for the next expedition.

---

# 3. Character Creation & Stats

Every character has a Soul Card representing their persistent identity.

### Soul manifestation

Current manifestation categories:

* Item
* Plant
* Animal
* Elemental

The player may choose their manifestation, although random selection is the intended/default way to play.

Family/faction and other player-specific creation choices contribute to starting identity and abilities.

### Current stats

* STR
* DEX
* CON
* MND
* CHA

### Stat roles

**STR**

* Larger/heavier weapons
* Physical strength

**DEX**

* Light weapons
* Ranged attacks
* Agility
* Initiative

**CON**

* Defense/stamina
* Tower Tired checks

**MND**

* Mental mechanics
* Arcane-style mechanics
* Divine-style mechanics
* Replaces the older INT/WIS split

**CHA**

* Social checks
* Distinct category of socially themed magic/effects

---

# 4. Soul Cards & Character Progression

Every character has a Soul Card.

The Soul Card is not merely equipment. It is the persistent container for the character's identity and permanently incorporated cards.

* Characters begin at Soul Card Level 0.
* At an obelisk/progression point, a qualifying card can be merged into the Soul Card.
* Merging a card levels the Soul Card by +1.
* A merged card becomes permanently attached and cannot be unequipped.
* Once attached, a card's level is locked to the Soul Card's level.
* When the Soul Card levels, all cards attached to it level with it.
* When the soul card gets a new card attached, the players sprite will change in some way (not important until working on graphics and sprites)

This prevents an early favorite, such as a Goblin Hammer acquired on Floor 1, from becoming permanently obsolete merely because it was merged early.

---

# 5. Card Structure

Anything that is not a mundane action is card-based.

Cards can represent:

* Weapons
* Attacks
* Armor
* Summons
* Transformations
* Stat boosts
* Passive abilities
* Active abilities
* Utility effects
* Crafting materials
* Nearly anything else the player can meaningfully do or create

### Card storage

| Storage   |                   Current Capacity | Purpose                                                                       |
| --------- | ---------------------------------: | ----------------------------------------------------------------------------- |
| Main Deck | Equal to character/Soul Card level | Fully prepared cards usable normally in combat                                |
| Side Deck |                           2 × Main | Backup/prepared cards; some cards retain a weaker or altered unslotted effect |
| Inventory |                           2 × Side | General card storage; not intended for practical combat use                   |

The Main Deck capacity is currently intended to equal the actual level, but this is explicitly a tuning variable if early-game constraints become unreasonable.

---

# 6. Card Level & Drop Rarity

Card Level and rarity serve different purposes.

Card Level is a progression mechanism designed to prevent a player from finding a favorite set early and never moving on.

Rarity is primarily a drop-frequency/presentation system rather than a strict power ranking.

* Using a card above the appropriate Tower/Card Level normally halves its damage.
* Cards have a 20% chance to drop from any monster.
* Status effects used on targets above the card's level have approximately a 50% chance to work.
* Pure utility effects generally remain usable without this combat penalty.
* Level 0 cards are treated as level 1 for effectiveness calculations.
* Each monster has a finite card pool: approximately 5 Common material cards, 4 Uncommon, 3 Rare, 2 Epic, and 1 Legendary.
* Each individual card is roughly equally likely within that pool; the apparent rarity comes primarily from there being fewer cards in the rarer groups.
* Legendary cards are intended to be one level higher than the other cards from the same monster.
* Rarity should not automatically mean "much stronger."

---

# 7. Monster Card Pools

Monster families have their own themed card pools.
A monster's cards should naturally derive from what the monster does or represents.
The intended relationship is:
**monster behavior → monster card pool → player capabilities**

---

# 8. Party & Town

* The player controls a party of approximately 3–5 characters.
* Floor 0 is the tutorial in both gameplay and lore; death is not a possibility there.
* Named NPCs have fixed loadouts and fixed progression routes rather than player-swappable builds.
* Mercenaries provide customizable party construction but are intentionally somewhat weaker than named NPCs.
* Named NPC recruitment is discovered through dialogue and actions rather than an obvious quest list.
* Some NPCs are easy to recruit; others require payment or completing a request.
* Some NPCs become angry if the player enters the Tower with another particular NPC.
* Some especially powerful NPCs can be permanently lost if replaced. The game must warn the player clearly before an irreversible choice.
* NPC difficulty/annoyance is intended to correlate with potential strength.

The town should be decently large and explorable, but party recruitment and relationships are the main intended town arc so that scope creep does not overwhelm the project.

---

# 9. Tower Levels & Randomized Floors

Each Tower level contains five floors.
Their order is randomized per playthrough, but once a floor is discovered its identity is permanent for that playthrough.
* At the beginning of a Tower-level run, there is a pool of five possible floor types.
* When a previously unknown floor is reached/explored, one unused type is selected from the remaining pool.
* The selected type is removed from the pool.
* That floor remains that type for the rest of the playthrough.

Therefore Floor 4 can be a very different environment in different playthroughs while remaining fixed once discovered during a particular run.

---

# 10. Hex Map: Two Layers

Each floor is a large hex map.
The player is expected to explore only a relatively small subset rather than exhaustively clearing every hex.

### Terrain layer

Persistent physical features such as:

* Roads
* Rivers
* Forests
* Cliffs
* Bridges
* Similar geography

The map is covered in fog of war.
The party reveals approximately one hex radius around itself.

### Discovery layer

Hidden information exposed by Explore, such as:

* Secure camps
* Healing springs
* Monsters
* Treasure
* Puzzles
* Other special locations

Discovery results persist once revealed.

Discoveries can be:

* Reusable
* One-time
* Depleted
* Defeated
* Otherwise resolved

Example:
A hex can have Forest terrain and reveal a Healing Spring.
Another can have Road terrain and reveal four Slimes and two Goblins, which remain recorded as defeated after the encounter.

---

# 11. Daily Overland Loop

A Tower day is the core overland time unit.
The player first decides whether the party will Explore, then spends remaining actions character-by-character.

* Choosing Explore consumes one available action from every party member.
* Everyone participates in whatever the Explore action reveals.
* After that party-wide decision, the player spends each character's remaining choices individually.
* Stealth, Forage, Set Up Camp, Rest, and similar actions are intentionally simple enough for the computer to resolve almost instantly.
* Travel can consume a day or partial day.
* When traveling, the UI should show a clear day/travel meter rather than forcing the player to understand fractional calculations. (Current thoughts. a solid yellow bar for total daylight, a thatched bar of blue? showing what a travel option will 'cost', and then when accepted will fill in the thatched part with a solid color)
* The existing TTRPG action categories remain the conceptual baseline, but the video game may streamline them.

---

# 12. Tired / Exhaustion

Tired is tracked independently for every character.
Each day in the Tower, every character makes a CON check against the current floor difficulty.
A failure adds one Tired level.

* The raw Tired number is hidden from the player.
* At the end of every day, every character gives some indication of whether their check succeeded or failed.
* Those reactions can be unique or semi-unique to the NPC's personality.
* Every five Tired levels applies a visible counter of exhaustion.
* At Exhausted 1, the character gains a visible debuff/condition so the player can clearly see that exhaustion has begun.
* Further exhaustion should become increasingly apparent through condition presentation and dialogue without exposing the raw counter.
* Every level of Exhausted produces a +1 increase to the relevant Room/Floor DC.
* After leaving the Tower, NPCs should tell the player how long they expect to be unavailable/recovering.
* Downtime recovery varies by character; some NPCs party, rest, or otherwise spend time in ways that change their recovery rate.

---

# 13. Equipment & Item System

Items are distinct game objects that may be:

* Conjured
* Acquired
* Carried
* Equipped
* Consumed
* Placed
* Otherwise interacted with

Not every Item is equipment.

Examples include:

* Equipment
* Monster materials
* Crafting materials
* Consumables
* Traps
* Placed objects
* Other world objects

The Item database therefore represents things that can exist in the game, not merely things that can be worn.

## Item Data

The current item schema is:

```text
item_id
name
tags
slot
slots_used
flavor_text
notes
```

`notes` are primarily human-readable design/development data and are not necessarily consumed by the game engine.

## Item Tags

Items may have multiple tags.

Tags serve two purposes:

1. Human-readable classification and description.
2. Machine-readable hooks that other systems and effects can query.

Tags are intentionally not mutually exclusive.

Examples:

```text
weapon
ranged
boots
armor
potion
material
crafting
```

An item may have any combination of appropriate tags.

Effects can query tags rather than requiring knowledge of specific item names.

For example, a check for:

```text
wearing:boots
```

should succeed for any equipped item carrying the `boots` tag.

This allows future items to automatically interact with existing mechanics without requiring item-specific code.

## Equipment Slots

Equipment slots define the physical categories in which items may be equipped.

The current slot reference is:

| Slot     | Maximum Amount |
| -------- | -------------: |
| head     |              1 |
| face     |              1 |
| neck     |              1 |
| body     |              1 |
| back     |              1 |
| shoulder |              2 |
| waist    |              2 |
| hands    |              2 |
| held     |              2 |
| ring     |             10 |
| legs     |              2 |
| feet     |              2 |
| arms     |              2 |
| wrists   |              2 |
| extra    |              0 |

The slot reference's `max_amount` defines how much capacity exists in that slot.

An item's `slots_used` defines how much of its assigned slot the item consumes.

For example:

```text
Sneaky Dagger
slot = held
slots_used = 1
```

versus:

```text
Boss Goblin Bow
slot = held
slots_used = 2
```

### Hands

`hands` represents worn hand equipment.

It has a capacity of 2.

The game does not distinguish left and right hands for equipment purposes.

A single glove can therefore use:

```text
slot = hands
slots_used = 1
```

while a paired set of gloves can use:

```text
slot = hands
slots_used = 2
```

### Held

`held` represents objects currently being physically held.
It has a capacity of 2.
A two-handed object simply uses:

```text
slot = held
slots_used = 2
```
There is no separate `two_hand`, `main_hand`, `off_hand`, `left_hand`, or `right_hand` slot.
The system only cares how much `held` capacity the item consumes.
This also means a character carrying a mundane object such as a branch can have less available capacity for another held object such as a shield.

### Extra
`extra` is a valid equipment category with a maximum capacity of 0.
Items assigned to `extra` can therefore exist as equipped/active items without occupying normal physical equipment capacity.
Items may also have `slots_used = 0` where appropriate.
Zero capacity is the mechanism that prevents an item from consuming slot capacity; `extra` is not a special-case rule.

## Soul Capacity
Soul Capacity is the thematic limit on how many conjured item instances a character can maintain simultaneously.
It is separate from physical equipment-slot capacity.
The current tentative progression is:

```text
Soul Level 0 → 8 items
Each additional Soul Level → +1 item
```

Current formula:
```text
Soul Capacity = 8 + Soul Level
```

This progression is explicitly tentative and is expected to be adjusted during playtesting.
Soul Capacity counts item instances rather than occupied equipment slots.

For example:
* A greatsword uses 2 `held` capacity but counts as 1 item.
* A ring uses 1 `ring` capacity and counts as 1 item.
* A zero-capacity conjured item still counts as an item being maintained.

Soul Capacity is not an inventory-size limit.
Its purpose is to represent the character's ability to handle and maintain the magic of conjured equipment.

### Carried Items

There is currently no separate physical inventory/bulk limit.
If a character is physically carrying an item, it may consume `held` capacity.
The Tower's floor-transition rules clear carried/worn equipment as currently designed, so physical hauling between floors is not intended to be a major inventory-management system.
`bulk` is therefore not currently part of the Item schema.
It should only be introduced if playtesting identifies a specific mechanic that requires it.
---
# 14. Item Behavior: Trigger → Condition → Effect
Items can have an arbitrary number of behaviors.
Item behavior should not be represented by a fixed number of columns such as:

```text
effect_1
effect_2
effect_3
```

Instead, item behavior is represented through a separate relationship between an Item, a Trigger, an optional Condition, and an Effect.

Conceptually:

```text
Item
 ↓
Trigger
 ↓
Condition check
 ↓
Effect
```

The relationship data is expected to contain at least:

```text
item_id
trigger_id
effect_id
condition
```

The exact final filename and implementation schema may change as the system is tested against real content.

## Trigger

A Trigger defines **when an item's effect should be evaluated**.

Examples include:

```text
on_attack
on_turn_start
on_equipped
on_placement
on_enter_space
```

A single item may have any number of trigger/effect relationships.

## Ability Refresh

Abilities are rebuilt at the start of combat and at the start of each turn.
Equipment, statuses, and other current-state effects determine which abilities are available when the ability list is rebuilt.
Changes made during a turn do not alter that turn's existing abilities. An ability gained or lost through such a change becomes available or unavailable at the next ability refresh.
Character stat modifiers and other effects caused by equipment changes take effect immediately and are not delayed until the next ability refresh.

For example, if a character begins a turn with a bow, their Bow Attack is available. If they equip a sword during that turn, the Sword's stat modifiers apply immediately, but the Bow Attack remains available until the next refresh. The next turn's ability list will reflect the sword instead.

## Condition Checks

A Condition Check determines whether the effect should execute when its Trigger fires.

Condition Checks query the current game state.

Examples:

```text
wearing:boots
in:forest
flanking
target:undead
```

Condition Checks are distinct from persistent status effects.



### Boolean Conditions
Conditions use a small expression syntax similar to Java/JavaScript.
Operators:

```text
!   NOT
&   AND
|   OR
( ) grouping
```

Examples:

```text
!wearing:boots
```

```text
wearing:boots & in:forest
```

```text
flanking | surprised
```

```text
(wearing:boots & in:forest) | magical
```

The condition language is intentionally small and is not intended to become a general-purpose programming language.
This avoids hardcoding boolean combinations into columns such as `and_id`, `or_id`, `and_id_2`, etc.
### Example
A hypothetical effect that pokes a character's feet with sharp sticks could be represented conceptually as:

```text
Trigger: on_turn
Condition: !wearing:boots
Effect: slow
```

The effect does not need to know the names of individual boots.
Any equipped item with the `boots` tag satisfies the check.
---

# 15. Status Effects
Status effects are standardized conditions that can be applied by cards, abilities, or universal actions.
Each status defines its own mechanical behavior, including how it is applied, how it ends, and what its numeric value represents.
Status effects are distinct from the boolean Condition Checks used by item triggers.

## General Status Rules

### Application

* A status effect does not inherently require a save.
* The effect applying the status determines whether a check or save is required.
* If the target has immunity to the status, the status has no effect.

### Fractional Status
A status effect may be applied in fractional values.
A total of 0.5 or more counts as 1 stack when determining the effect, while values above 0.5 are rounded down to the nearest whole stack.

### Stacking
* Normally, repeated applications of the same status from the same card do not stack.
* Use whichever application has the greater remaining value.
* Applications of the same status from different cards stack.
 * Poison is an exception: all Poison applications stack, including repeated applications from the same card.

### Recovery

Recoverable statuses define their own recovery method.

Unless otherwise specified, successful recovery produces Basic effort.

When a status's remaining value reaches 0, the status ends.

### Permanent Values
For statuses that use `-1`, this represents an indefinite effect that does not expire naturally.
The individual status defines whether `-1` is meaningful.

## Slowed X
The target's movement is reduced by half for X rounds, rounded down to the nearest whole square.
A target's movement cannot be reduced below 1 square by Slowed.

* Recovery uses the highest of STR, DEX, CON, or MND.
* CHA cannot be used for Slow recovery.
* A successful recovery check produces the normal recovery effort.
* Recovery effort reduces the Slow value.
* Slow -1 represents a permanent Slow effect until specifically removed.

## Rooted X

A Rooted creature cannot move using Move actions until it breaks free.

* X represents the amount of recovery effort required to break free.
* Recovery uses the highest of STR, DEX, CON, or MND.
* At the start of its turn, the creature may make a recovery check.
* A successful recovery check produces the normal recovery effort.
* Recovery effort reduces the Rooted value.
* When the Rooted value reaches 0, the creature breaks free and can move normally again.
* Rooted -1 represents an indefinite Rooted effect until specifically removed.
* Rooted does not prevent the creature from taking other actions unless an effect specifically says otherwise.

## Withered X

The target's maximum HP is reduced by X.

This reduction does not cause current HP to change; if the target's current HP exceeds its new maximum, current HP is reduced to match.

Withered has an infinite duration by default and cannot be removed through normal Effort or ordinary healing.

It may be removed by effects that specifically remove Withered.

## Wounded X

The target suffers X Wounded.

Wounded does not immediately reduce HP. Instead, at the start of each combat, the target takes damage equal to its current Wounded value.

Wounded has an infinite duration by default and cannot be removed through normal Effort or ordinary healing.

Magical healing may be used to remove Wounded, but only after the target has been healed to its normal maximum HP.

Each additional point of magical healing beyond the target's normal maximum HP reduces Wounded by 1.

Wounded may also be removed through appropriate specialized treatment while resting outside the Tower.

Effects that specifically remove Wounded may remove it regardless of the normal recovery rules.

Such effects are exceptionally rare and generally limited to end-game card effects.

## Stunned X

The target is impaired and loses actions while Stunned.

* When Stunned is applied, the target makes the specified save if the applying effect requires one.
* On a successful save, Stunned does not apply.
* A Stunned creature loses at least 1 pip at the start of its turn.
* For every 2 points of Stunned beyond the first, the target loses an additional pip.
* At the end of its turn, the target may make the specified recovery check.
* A successful recovery check produces the normal recovery effort.
* Recovery effort reduces the Stunned value.
* Cards may specify a different recovery stat or effort type.

| Stunned | Pips Lost |
| ------: | --------: |
|     1–3 |         1 |
|     4–5 |         2 |
|     6–7 |         3 |
|     8–9 |         4 |

Pip loss cannot reduce a turn below 0 pips.

## Prone

A Prone creature has been knocked down.

* A creature may voluntarily become Prone as a 1-pip action with no check.
* A creature may attempt to Trip an adjacent target as a 1-pip action. The default Trip check is Hard.
* Cards may provide alternate methods of applying Prone, including ranged attacks or effects that bypass the normal Hard check.
* Melee attacks against a Prone target are Easy.
* Ranged attacks against a Prone target are Hard.
* Attacks made by a Prone creature are Hard.
* A Prone creature may spend a Move action to either move 1 square or stand up.
* Prone is binary and does not stack.

## Blinded X

The target cannot see.

* When Blinded is applied, the target makes the specified save if the applying effect requires one.
* On a successful save, Blinded does not apply.
* Normal attacks made by a Blinded creature automatically miss.
* All attacks against a Blinded creature are Easy.
* At the end of its turn, the target may make the specified recovery check.
* A successful recovery check produces the normal recovery effort.
* Recovery effort reduces the Blinded value.
* When the value reaches 0, the creature can see normally again.
* Blinded -1 represents indefinite blindness until specifically removed.
* Creatures with appropriate immunity are unaffected.
* Special senses and unusual methods of perception are handled by the creature or effect providing the special interaction rather than by adding exceptions to the Blinded status itself.

## Invisible X

The target cannot normally be seen by other creatures.

* X represents the number of rounds the effect remains active.
* While Invisible, the target cannot normally be attacked by non-autohit attacks.
* The Invisible creature's attacks against other creatures are Easy.
* Making an attack does not prevent that attack from benefiting from Invisible; Invisible ends after the attack resolves.
* Autohit effects can affect an Invisible target normally unless the effect specifies otherwise.
* Invisible -1 represents indefinite invisibility until specifically removed.
* Special senses and effects that interact with Invisible are defined by the creature, card, or effect providing the interaction.

## Bleeding X

The target is suffering an active wound.

* At the end of the affected creature's turn, it suffers X damage.
* Bleeding has no automatic duration or natural recovery.
* A creature may spend 1 pip to Bandage, removing 5 Bleeding.
* Any healing immediately removes all Bleeding.
* Bleeding can reduce a creature to 0 Hearts and cause death under the normal death rules.
* Bleeding does not normally require a save when applied unless the applying effect specifically calls for one.
* Bleeding -1 has no special meaning; Bleeding is already indefinite until treated.
* Bleeding from different cards stacks according to the normal status stacking rules.

Bleeding values should generally remain low, as multiple sources can quickly create a dangerous amount of ongoing damage.

## Poison X

The target has been poisoned.

* Poison does not normally require a save when applied unless the applying effect specifically calls for one.
* All Poison applications stack, including repeated applications from the same card.
* At the end of each round, after all player turns and before the enemy phase, the target suffers X poison damage.
* After the damage is applied, the Poison value is halved, rounded down.
* Poison naturally ends when its value reaches 0.
* Normal healing does not remove Poison unless the healing effect specifically says that it does.
* Poison can be removed early by effects that specifically cure or remove Poison.
* Poison can reduce a creature to 0 Hearts and cause death under the normal death rules.

Example:

```text
Poison 10
→ End of round: suffer 10 damage → Poison 5
→ End of round: suffer 5 damage → Poison 2
→ End of round: suffer 2 damage → Poison 1
→ End of round: suffer 1 damage → Poison 0; Poison ends
```

---

# 16. Effect System

Effects are named game behaviors.

The effect registry contains the names and human-readable descriptions of available effects.

The actual mechanical behavior of an effect is implemented in code.

For example:

```text
slow
wait
enfeeble
heal
milk
basic
tool
weapon
magic
ultimate
```

may correspond to individual Effect classes.

The data file does not attempt to encode the complete behavior of each effect.

Instead, runtime resolves an effect identifier to the corresponding implementation.

For example:

```text
slow 5 / burning 3
```

is parsed into separate effect instances:

```text
Slow(5)
Burning(3)
```

The `/` separates one effect from the next.

Each Effect class may define its own parameter structure and behavior.

This intentionally allows unusual effects to have custom code rather than forcing every effect into a universal generic parameter system.

The Effect data file is therefore primarily a registry/reference layer and should remain relatively stable even as individual effect implementations evolve.

---

# 17. Combat Module — Current Baseline

Combat is deliberately its own module.

The current system is an ICRPG-inspired baseline and may be replaced without forcing a redesign of the broader game.

## Core Combat

* Combat uses a square tactical grid.
* Each character has 3 energy/action pips per turn.
* Actions have an explicit pip cost.
* Most mundane actions cost 1 pip.
* Cards may cost 1–3 or otherwise specify their cost.
* Cards cost 2 pips by default unless their effect specifies otherwise.
* Current effort ladder:

  * Basic/unarmed d4
  * Tool d6
  * Weapon d8
  * Magic/gun d10
  * Critical/ultimate d12
* Turn order is established once at combat start using 1d20 + DEX.
* Highest result sets the starting location in the order.
* Party order is then used as the ordering.
* Monsters act between the final party member and the first party member.
* Turn order does not change during the encounter.
* Combat generally ends when one side is defeated or one side successfully runs away.

## Turn Structure

* Characters begin their turn with 3 pips.
* Actions consume pips.
* When a character reaches 0 pips, their turn ends immediately.
* There is no separate action/bonus-action/movement economy.

## Default 1-Pip Actions

* Move
* Attack
* Interact
* Stand
* Defend (once per turn)

## Movement

* 30 ft. default movement per Move action.
* Combat squares are 3×3 ft.
* Diagonal movement alternates 3/6/3/6...
* Enemies block movement.
* Allies can be moved through.
* Cards/abilities can modify movement.
* Normal D&D/Pathfinder-style terrain adjustments apply.

## Attacks

* d20 + appropriate stat vs Room DC for players.
* Enemies attack against player Defense.
* Melee normally targets adjacent squares.
* Ranged attacks have an explicitly stated range.
* Ranged attacks default to DEX unless otherwise specified.
* A conjured item functions as that type of item, including its normal attack-stat rules.

## Defense

* 10 + CON + modifiers.
* Maximum 20.
* Once per turn, spend 1 pip to add DEX to Defense, subject to the cap.

## Effort

* Successful attacks/checks that call for effort roll the specified effort.
* Checks are 1d20 + the appropriate stat against the relevant target number.
* A successful check that calls for effort rolls the specified effort.
* Effort is the general "work done" mechanic, not exclusively damage.
* Excess effort has no effect unless explicitly specified.

## Difficulty

Difficulty is a sliding scale. Effects, conditions, and event chains may move the current difficulty up or down the scale. The final position on the scale determines how the relevant roll is resolved.

* **Auto** = automatically produces the maximum possible result of the roll, without adding any bonus beyond the normal roll.
* **Easy_Advantage** = roll twice at Easy difficulty (-3) and take the better result.
* **Advantage** = roll twice and take the better result.
* **Easy** = -3 to the roll.
* **Default** = no modifier.
* **Hard** = +3 to the roll.
* **Disadvantage** = roll twice and take the worse result.
* **Hard_Disadvantage** = roll twice at Hard difficulty (+3) and take the worse result.
* **Auto_Fail** = automatically produces the minimum possible result of the roll, without adding any penalty beyond the normal roll.

## Criticals

* Natural 1 has no special effect.
* Natural 20 automatically succeeds.
* If the check produces effort, a Natural 20 adds Ultimate effort to the normal effort.
* No confirmation roll.

## Automatic Effects

Effects marked `(autohit)` bypass the attack roll.

---

# 18. Data & Technical Architecture

The game will be written in JavaScript.

Content data should remain separate from game logic.

The repository is the development source of truth for structured content.

## Data Flow

The intended general flow is:

```text
Human-editable CSV
        ↓
Validation / conversion
        ↓
Runtime JSON
        ↓
JavaScript game systems
```

CSV is currently preferred for structured game data because it is easy to edit in spreadsheets, and easy for GPD to read.
JSON is expected to be the game-facing runtime format once schemas stabilize.
The GDD describes game rules and architecture rather than serving as the runtime data source.
A Technical Design Document may eventually contain detailed JavaScript modules, data structures, rendering architecture, save data, and implementation details.

## Major Data Categories

The repository should conceptually separate:

```text
cards
effects
items
slots
triggers
conditions/checks
```

### Cards

Card definitions describe what cards exist and their player-facing/card-specific information.

### Effects

Effects provide the registry of named behaviors that are implemented by code.

### Items

Items describe physical/game objects and their equipment properties.

### Slots

Slots define available equipment categories and their maximum capacities.

### Triggers

Triggers define events that can cause item behavior to be evaluated.

### Conditions / Checks

Conditions provide boolean queries against the current game state and can be combined using the condition expression syntax.

### Item/Effect Relationships

Item behavior is stored separately from the Item master record so that an item may have an arbitrary number of triggers and effects.

This prevents the Item schema from requiring fixed columns such as `effect_1`, `effect_2`, or `effect_3`.

## Human-Readable Fields

Some CSV fields exist primarily for development convenience.

Examples:

* `notes`

These fields may be excluded from runtime data when they have no gameplay purpose.

The presence of such fields does not imply that the game engine should consume them.

## Combat Modularity

Combat should expose a clean interface so its resolution system can be replaced later.

## Persistence

Tower run state should persist:

* Floor assignments
* Discovered hex information
* Resolved/discovered locations
* Other appropriate run-specific progression

---

# 19. Current Card Data

The current working card data includes fields such as:

* Card ID
* Name
* Type
* Rarity
* Consumable
* Dropped From
* Cost
* Flavor Text
* Soul Card
* Notes

The exact CSV schema may continue to evolve.
The spreadsheet is a human-editable master source during development rather than a final implementation contract.
A conversion/export step can later produce the machine-readable card data consumed by the game.
Cards that represent conjured equipment may reference Items.
Every object created through a conjuration effect records the source invocation that created it.
Objects created by conjuration record the specific invocation that created them, allowing the creating effect/card to identify and manage its own summoned objects.
Cards that perform actions may reference Effects.
Items may independently reference Effects through their Trigger/Condition/Effect relationships.
This means a card does not need to contain the complete implementation of every item or effect it creates.

---

# 20. Design Principles

* Anything non-mundane is card-based.
* Let the computer handle repetitive bookkeeping; keep meaningful decisions with the player.
* The Tower should be unpredictable between playthroughs but consistent within a single run.
* Early favorite cards can remain relevant when permanently Soul-bound because they level with the Soul Card.
* Rarity should not be treated as a simple power ladder.
* Named NPCs should feel like people, not interchangeable stat blocks.
* Irreversible relationship choices should be explicitly warned about.
* Hidden mechanics should be communicated through readable feedback instead of raw numbers when possible.
* Uncertain systems should remain modular and replaceable.
* Data should describe relationships and content; code should implement complex behavior.
* Avoid adding a field merely because another game or ruleset has one. A data field should exist because Tower of Cards has a concrete need for it.
* Prefer reusable systems over fixed numbers of special-purpose fields.
* Avoid encoding arbitrary limits into unrelated systems when a thematic game concept can represent the same limitation.
* When a system is still being discovered through playtesting, keep its implementation replaceable rather than prematurely locking down the schema.

---

# 21. Open / Tentative Questions

The following systems or values remain intentionally unsettled:

* Whether Main Deck capacity should remain equal to level.
* Exact Soul Capacity progression beyond the current tentative `8 + Soul Level`.
* Exact death/recovery consequences.
* Exact number and distribution of hex discoveries per floor.
* How staircase discovery becomes increasingly likely as exploration proceeds.
* Final town scope and activities.
* Final downtime/rumor implementation.
* Final card JSON schema and conversion workflow.
* Final Trigger schema.
* Final Condition/Check registry and expression parser implementation.
* Exact Item → Trigger → Condition → Effect relationship file schema.
* Exact UI treatment of hidden Tired values and exhaustion states.
* Remaining edge cases discovered through playtesting.

These should remain open until actual content and prototype implementation provide enough information to make a useful decision.

---

# 22. Recommended First Vertical Slice

Before building the full Tower or a large town, the first playable prototype should prove the core loop with a deliberately small content set.

The prototype should include:

* Character creation with one Soul Card.
* A small party containing the protagonist and a few NPCs.
* A small explorable town section.
* One Tower level containing five possible floor types.
* A small hex map with terrain and discovery layers.
* At least one monster encounter.
* At least one non-combat discovery.
* Basic card rewards and deck management.
* Tired checks and visible exhaustion feedback.
* Basic Item/equipment handling.
* Soul Capacity.
* At least a few Item → Trigger → Condition → Effect relationships.
* Return-to-town and recovery.
* One repeat expedition demonstrating persistent floor assignment and changing party/card choices.

The first prototype should prove that:

**prepare → enter Tower → explore → encounter → collect cards → manage exhaustion → return → recover**

is fun and technically workable.

Content quantity comes later.

---

# 23. Scope Boundary

Do not attempt to build the entire Tower, every NPC, or the full town before the vertical slice works.

The project should preserve modularity so combat and other uncertain systems can be iterated independently.

Likewise, do not prematurely finalize data schemas merely to accommodate hypothetical future content.

When an actual card, item, effect, trigger, or condition demonstrates that the current architecture is insufficient, update the architecture based on that concrete requirement.

---

# 24. Current Development Direction

The immediate development priority is to finish the foundational content architecture before beginning large-scale implementation.

Current content foundations include:

1. Card data
2. Effect registry
3. Item data
4. Equipment slot reference
5. Item tags
6. Soul Capacity
7. Trigger/Condition/Effect architecture

The next major design task is to test the Item behavior architecture against real content.

Particularly useful test cases include:

* An item with a passive effect while equipped.
* An item with an attack effect.
* An item with a conditional attack effect.
* An item with a periodic effect.
* An item with an activated effect.
* A placed trap.
* A placed persistent object such as a totem.
* A zero-capacity item.
* A multi-slot item.

The goal is not to prove that the current schema can represent hypothetical mechanics.

The goal is to make sure it can cleanly represent the actual cards and items already designed.
