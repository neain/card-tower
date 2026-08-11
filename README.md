Tower of Cards
Game Design Document — Version 1
Current design baseline • August 2026
1. Purpose & Scope
This is the current design baseline for the Tower of Cards JavaScript RPG. It is a living document; tentative values may change through playtesting. It uses the Tower of Cards setting and player rules, excluding the later dungeon/core campaign material.
2. Core Concept & Loop
The player creates a protagonist, gathers a party, explores a Tower town, prepares for an expedition, enters a large hex-based Tower floor, discovers encounters and locations, collects cards, manages exhaustion, returns to town, recovers, and prepares another expedition.
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
3. Character Creation & Stats
    • Soul Card: the character sheet, core identity, stats, and card-capacity/progression object.
    • Soul manifestation categories: Item, Plant, Animal, Elemental. The player may choose; random selection is the intended/default way to play.
    • Family/faction and other player-specific creation choices contribute to starting identity and abilities.
    • Current stats: STR, DEX, CON, MND, CHA.
    • STR: larger/heavier weapons and physical strength.
    • DEX: light weapons, ranged attacks, agility, and initiative.
    • CON: defense/stamina and Tower Tired checks.
    • MND: replaces the older INT/WIS split for mental, arcane, and divine-style mechanics.
    • CHA: social checks and a distinct category of socially themed magic/effects.
4. Soul Cards & Character Progression
Every character has a Soul Card. The Soul Card is not merely equipment: it is the persistent container for the character's identity and permanently incorporated cards.
    • Characters begin at Soul Card level 0.
    • At an obelisk/progression point, a qualifying card can be merged into the Soul Card. This also levels the soul card by +1.
    • A merged card becomes permanently attached and cannot be unequipped.
    • Once attached, a card's level is locked to the Soul Card's level.
    • When the Soul Card levels, ALL cards attached to it level with it.
    • This prevents an early favorite—such as a Goblin Hammer acquired on Floor 1—from becoming permanently obsolete merely because it was merged early.
5. Card Structure
Anything that is not a mundane action is card-based. Cards can be weapons, attacks, armor, summons, transformations, stat boosts, passive abilities, active abilities, utility effects, crafting materials, or nearly anything else the player can meaningfully do or create.
Storage	Current Capacity	Purpose
Main Deck	Equal to character/Soul Card level (tentative)	Fully prepared cards usable normally in combat.
Side Deck	2 × Main	Backup/prepared cards; some cards retain a weaker or altered unslotted effect.
Inventory	2 × Side	General card storage; not intended for practical combat use.
The Main Deck capacity is currently intended to equal the actual level, but this is explicitly a tuning variable if early-game constraints become unreasonable.
6. Card Level & Drop Rarity
Card Level and rarity serve different purposes. Card Level is a progression mechanism designed to prevent a player from finding a favorite set early and never moving on. Rarity is primarily a drop-frequency/presentation system rather than a strict power ranking.
    • Using a card above the appropriate Tower/Card Level normally halves its damage.
    • Cards have a 20% chance to drop from any monster. 
    • Status effects used on targets above the card's level have approximately a 50% chance to work.
    • Pure utility effects generally remain usable without this combat penalty.
    • Level 0 cards are treated as level 1 for effectiveness calculations.
    • Each monster has a finite card pool: approximately 5 Common material cards, 4 Uncommon, 3 Rare, 2 Epic, and 1 Legendary.
    • Each individual card is roughly equally likely within that pool; the apparent rarity comes primarily from there being fewer cards in the rarer groups.
    • Legendary cards are intended to be one level higher than the other cards from the same monster.
    • Rarity should not automatically mean 'much stronger.'
7. Monster Card Pools
Monster families have their own themed card pools. A monster's cards should naturally derive from what the monster does or represents. The resulting relationship is: monster behavior → monster card pool → player capabilities.
8. Party & Town
    • The player controls a party of approximately 3–5 characters.
    • Floor 0 is the tutorial in both gameplay and lore; death is not a possibility there.
    • Named NPCs have fixed loadouts and fixed progression routes rather than player-swappable builds.
    • Mercenaries provide customizable party construction but are intentionally somewhat weaker than named NPCs.
    • Named NPC recruitment is discovered through dialogue and actions rather than an obvious quest list.
    • Some NPCs are easy to recruit; others require payment or completing a request.
    • Some NPCs become angry if the player enters the Tower with another particular NPC.
    • Some especially powerful NPCs can be permanently lost if replaced. The game must warn the player clearly before an irreversible choice.
    • NPC difficulty/annoyance is intended to correlate with potential strength.
The town should be decently large and explorable, but party recruitment and relationships are the main intended town arc so that scope creep does not overwhelm the project.
9. Tower Levels & Randomized Floors
Each Tower level contains five floors. Their order is randomized per playthrough, but once a floor is discovered its identity is permanent for that playthrough.
    • At the beginning of a Tower-level run, there is a pool of five possible floor types.
    • When a previously unknown floor is reached/explored, one unused type is selected from the remaining pool.
    • The selected type is removed from the pool.
    • That floor remains that type for the rest of the playthrough.
    • Therefore Floor 4 can be a very different environment in different playthroughs, while remaining fixed once discovered during a particular run.
10. Hex Map: Two Layers
Each floor is a large hex map. The player is expected to explore only a relatively small subset rather than exhaustively clearing every hex.
    • Terrain layer: persistent physical features such as roads, rivers, forests, cliffs, bridges, and similar geography.
    • The map is covered in a fog of war that gets revealed 1 hex radius around the players party
    • Discovery layer: hidden information exposed by Explore, such as a secure camp, healing spring, monsters, treasure, puzzles, or other locations.
    • Discovery results persist once revealed.
    • Discoveries can be reusable, one-time, depleted, defeated, or otherwise resolved.
Example: a hex can have Forest terrain, then reveal a Healing Spring; another can have Road terrain and reveal four Slimes and two Goblins, which remain recorded as defeated after the encounter.
11. Daily Overland Loop
A Tower day is the core overland time unit. The player first decides whether the party will Explore, then spends remaining actions character-by-character.
    • Choosing Explore consumes one available action from every party member.
    • Everyone participates in whatever the Explore action reveals.
    • After that party-wide decision, the player spends each character's remaining choices individually.
    • Stealth, Forage, Set Up Camp, Rest, and similar actions are intentionally simple enough for the computer to resolve almost instantly.
    • Travel can consume a day or partial day; when traveling, the UI should show a clear day/travel meter rather than forcing the player to understand fractional calculations.
    • The existing TTRPG action categories remain the conceptual baseline, but the video game may streamline them.
12. Tired / Exhaustion
Tired is tracked independently for every character. Each day in the Tower, every character makes a CON check against the current floor difficulty. A failure adds one Tired level.
    • The raw Tired number is hidden from the player.
    • At the end of every day, every character gives some indication of whether their check succeeded or failed.
    • Those reactions can be unique or semi-unique to the NPC's personality.
    • At Exhausted 1, the character gains a visible debuff/condition so the player can clearly see that exhaustion has begun.
    • Further exhaustion should become increasingly apparent through condition presentation and dialogue without exposing the raw counter.
    • Every five Tired levels applies a visible counter of exhaustion.
    • Every level of Exhausted produces a +1 increase to the relevant Room/Floor DC.
    • After leaving the Tower, NPCs should tell the player how long they expect to be unavailable/recovering.
    • Downtime recovery varies by character; some NPCs party, rest, or otherwise spend time in ways that change their recovery rate.
13. Combat Module — Current Baseline
Combat is deliberately its own module. The current system is an ICRPG-inspired baseline and may be replaced without forcing a redesign of the broader game.
    • Combat uses a square tactical grid.
    • Each character has 3 energy/action pips per turn.
    • Actions have an explicit pip cost. Most mundane actions cost 1 pip; cards may cost 1–3 or otherwise specify their cost. 
    • Cards are simply part of the character's available actions; Cards cost 2 pips by default unless their effect specifies otherwise. 
    • Current effort ladder: basic/unarmed d4, tool d6, weapon d8, magic/gun d10, critical/ultimate d12.
    • Turn order is established once at combat start using 1d20 + DEX, highest sets the starting location.
    • Party order is then used as the ordering.
    • Monsters act between the final party member and the first party member.
    • Turn order does not change during the encounter.
    • Combat generally ends when one side is defeated or one side successfully runs away.

Turn structure
    • Characters begin their turn with 3 pips. 
    • Actions consume pips. 
    • When a character reaches 0 pips, their turn ends immediately. 
    • There is no separate action/bonus-action/movement economy. 
Default 1-pip actions
    • Move 
    • Attack 
    • Interact 
    • Stand 
    • Defend (once per turn) 
Movement
    • 30 ft. default movement per move action. 
    • Combat squares are 3×3 ft. 
    • Diagonal movement alternates 3/6/3/6... 
    • Enemies block movement. 
    • Allies can be moved through. 
    • Cards/abilities can modify movement. 
    • Normal D&D/Pathfinder-style terrain adjustments apply. 
Attacks
    • d20 + appropriate stat vs Room DC for players. 
    • Enemies attack against player Defense. 
    • Melee normally targets adjacent squares. 
    • Ranged attacks have an explicitly stated range. 
    • Ranged attacks default to DEX unless otherwise specified. 
    • A conjured item functions as that type of item, including its normal attack-stat rules. 
Defense
    • 10 + CON + modifiers 
    • Maximum 20. 
    • Once per turn, spend 1 pip to add DEX to Defense, subject to the cap. 
Effort
    • Successful attacks/checks that call for effort roll the specified effort. 
    • Checks are 1d20 + the appropriate stat against the relevant target number. 
    • A successful check that calls for effort rolls the specified effort. 
    • Effort is the general "work done" mechanic, not exclusively damage. 
    • Excess effort has no effect unless explicitly specified. 
Difficulty
    • Easy = -3. 
    • Hard = +3. 
Criticals
    • Natural 1 has no special effect. 
    • Natural 20: The check automatically succeeds and, if the check produces effort, adds Ultimate effort to the normal effort.  
    • No confirmation roll. 
Automatic effects
    • Effects marked (autohit) bypass the attack roll. 
Under Development
    • Status-effect glossary – started, but not finished.
    • Exact card wording conventions 
    • Any remaining edge cases discovered through playtesting
    • Character death/recovery is unresolved; a current possibility is recovery after combat with a significant exhaustion consequence.

Status Effects
Status effects are standardized conditions that can be applied by cards, abilities, or universal actions. Each status defines its own mechanical behavior, including how it is applied, how it ends, and what its numeric value represents.
General Status Rules
Application
A status effect does not inherently require a save. The effect applying the status determines whether a check or save is required.
If the target has an immunity to the status, the status has no effect.
Fractional Status: A status effect may be applied in fractional values. A total of 0.5 or more counts as 1 stack when determining the effect, while values above 0.5 are rounded down to the nearest whole stack. 
Stacking
Normally, repeated applications of the same status from the same card do not stack. Use whichever application has the greater remaining value.
Applications of the same status from different cards stack.
Poison is an exception: all Poison applications stack, including repeated applications from the same card.
Recovery
Recoverable statuses define their own recovery method. Unless otherwise specified, successful recovery produces Basic effort.
When a status's remaining value reaches 0, the status ends.
Permanent Values
For statuses that use -1, this represents an indefinite effect that does not expire naturally. The individual status defines whether -1 is meaningful.

Slowed X
The target's movement is reduced by half for X rounds, rounded down to the nearest whole square. A target's movement cannot be reduced below 1 square by Slowed.
    • Recovery uses the highest of STR, DEX, CON, or MND. CHA cannot be used for Slow recovery.
    • A successful recovery check produces the normal recovery effort.
    • Recovery effort reduces the Slow value
    • Slow -1 represents a permanent Slow effect until specifically removed.

Rooted X
A Rooted creature cannot move using Move actions until it breaks free.
    • X represents the amount of recovery effort required to break free.
    • Recovery uses the highest of STR, DEX, CON, or MND.
    • At the start of its turn, the creature may make a recovery check.
    • A successful recovery check produces the normal recovery effort.
    • Recovery effort reduces the Rooted value.
    • When the Rooted value reaches 0, the creature breaks free and can move normally again.
    • Rooted -1 represents an indefinite Rooted effect until specifically removed.
    • Rooted does not prevent the creature from taking other actions unless an effect specifically says otherwise.


Withered X
The target's maximum HP is reduced by X. This reduction does not cause current HP to change; if the target's current HP exceeds its new maximum, its current HP is reduced to match.
Withered has an infinite duration by default and cannot be removed through normal Effort or ordinary healing. It may be removed by effects that specifically remove Withered.

Wounded X
The target suffers X Wounded. Wounded does not immediately reduce HP. Instead, at the start of each combat, the target takes damage equal to its current Wounded value.
Wounded has an infinite duration by default and cannot be removed through normal Effort or ordinary healing.
Magical healing may be used to remove Wounded, but only after the target has been healed to its normal maximum HP. Each additional point of magical healing beyond the target's normal maximum HP reduces Wounded by 1.
Wounded may also be removed through appropriate specialized treatment while resting outside the Tower. Effects that specifically remove Wounded may remove it regardless of the normal recovery rules. Such effects are exceptionally rare and generally limited to end-game card effects.

Stunned X
The target is impaired and loses actions while Stunned.
    • When Stunned is applied, the target makes the specified save if the applying effect requires one.
    • On a successful save, Stunned does not apply.
    • A Stunned creature loses at least 1 pip at the start of its turn.
    • For every 2 points of Stunned beyond the first, the target loses an additional pip.
    • At the end of its turn, the target may make the specified recovery check.
    • A successful recovery check produces the normal recovery effort.
    • Recovery effort reduces the Stunned value.
    • Cards may specify a different recovery stat or effort type.
Stunned pip loss is therefore:
Stunned	Pips Lost
1–3	1
4–5	2
6–7	3
8–9	4
Pip loss cannot reduce a turn below 0 pips.

Prone
A Prone creature has been knocked down.
    • A creature may voluntarily become Prone as a 1-pip action with no check.
    • A creature may attempt to Trip an adjacent target as a 1-pip action. The default Trip check is Hard.
    • Cards may provide alternate methods of applying Prone, including ranged attacks or effects that bypass the normal Hard check.
    • Melee attacks against a Prone target are Easy.
    • Ranged attacks against a Prone target are Hard.
    • Attacks made by a Prone creature are Hard.
    • A Prone creature may spend a Move action to either move 1 square or stand up.
    • Prone is binary and does not stack.

Blinded X
The target cannot see.
    • When Blinded is applied, the target makes the specified save if the applying effect requires one.
    • On a successful save, Blinded does not apply.
    • Normal attacks made by a Blinded creature automatically miss.
    • All attacks against a Blinded creature are Easy.
    • At the end of its turn, the target may make the specified recovery check.
    • A successful recovery check produces the normal recovery effort.
    • Recovery effort reduces the Blinded value.
    • When the value reaches 0, the target can see normally again.
    • Blinded -1 represents indefinite blindness until specifically removed.
    • Creatures with appropriate immunity are unaffected.
Special senses and unusual methods of perception are handled by the creature or effect providing the special interaction, rather than by adding exceptions to the Blinded status itself.

Invisible X
The target cannot normally be seen by other creatures.
    • X represents the number of rounds the effect remains active.
    • While Invisible, the target cannot normally be attacked by non-(autohit) attacks.
    • The Invisible creature's attacks against other creatures are Easy.
    • Making an attack does not prevent that attack from benefiting from Invisible; Invisible ends after the attack resolves.
    • (autohit) effects can affect an Invisible target normally unless the effect specifies otherwise.
    • Invisible -1 represents indefinite invisibility until specifically removed.
    • Special senses and effects that interact with Invisible are defined by the creature, card, or effect providing the interaction.

Bleeding X
The target is suffering an active wound.
    • At the end of the affected creature's turn, it suffers X damage.
    • Bleeding has no automatic duration or natural recovery.
    • A creature may spend 1 pip to Bandage, removing 5 Bleeding.
    • Any healing immediately removes all Bleeding.
    • Bleeding can reduce a creature to 0 Hearts and cause death under the normal death rules.
    • Bleeding does not normally require a save when applied unless the applying effect specifically calls for one.
    • Bleeding -1 has no special meaning; Bleeding is already indefinite until treated.
    • Bleeding from different cards stacks according to the normal status stacking rules.
Bleeding values should generally remain low, as multiple sources can quickly create a dangerous amount of ongoing damage.

Poison X
The target has been poisoned.
    • Poison does not normally require a save when applied unless the applying effect specifically calls for one.
    • All Poison applications stack, including repeated applications from the same card.
    • At the end of each round, after all player turns and before the enemy phase, the target suffers X poison damage.
    • After the damage is applied, the Poison value is halved, rounded down.
    • Poison naturally ends when its value reaches 0.
    • Normal healing does not remove Poison unless the healing effect specifically says that it does.
    • Poison can be removed early by effects that specifically cure or remove Poison.
    • Poison can reduce a creature to 0 Hearts and cause death under the normal death rules.
Example:
Poison 10
    • End of round: suffer 10 damage → Poison 5
    • End of round: suffer 5 damage → Poison 2
    • End of round: suffer 2 damage → Poison 1
    • End of round: suffer 1 damage → Poison 0; Poison ends.

14. Technical Architecture Direction
The game will be written in JavaScript. Content data should remain separate from game logic.
    • ODS/spreadsheet: human-editable master card database during development.
    • JSON: likely game-facing card database once the schema stabilizes.
    • Game Design Document: what the game is and how systems should behave.
    • Technical Design Document: JavaScript modules, data structures, rendering, save data, and implementation details.
    • Combat should expose a clean interface so its resolution system can be replaced later.
    • Tower run state should persist floor assignments and discovered/resolved hex information.
15. Current Card Spreadsheet Fields
The current working spreadsheet contains: Card Name, Price, Dropped From, Drop %, Floor, Card Level, Rarity, Effect, Effect if Used While Not Slotted, Cooldown, Soul Card?, and GM Notes. These are a starting point for the eventual JSON schema, not a final implementation contract.
The spreadsheet should remain convenient for human editing. A conversion/export step can later produce the machine-readable master card data consumed by the game.
16. Design Principles
    • Anything non-mundane is card-based.
    • Let the computer handle repetitive bookkeeping; keep meaningful decisions with the player.
    • The Tower should be unpredictable between playthroughs but consistent within a single run.
    • Early favorite cards can remain relevant when permanently Soul-bound because they level with the Soul Card.
    • Rarity should not be treated as a simple power ladder.
    • Named NPCs should feel like people, not interchangeable stat blocks.
    • Irreversible relationship choices should be explicitly warned about.
    • Hidden mechanics should be communicated through readable feedback instead of raw numbers when possible.
    • Uncertain systems should remain modular and replaceable.
17. Open / Tentative Questions
    • Whether Main Deck capacity should remain equal to level.
    • Exact death/recovery consequences.
    • Exact number and distribution of hex discoveries per floor.
    • How staircase discovery becomes increasingly likely as exploration proceeds.
    • Final town scope and activities.
    • Final downtime/rumor implementation.
    • Final card JSON schema and conversion workflow.
    • Exact UI treatment of hidden Tired values and exhaustion states.
18. Recommended First Vertical Slice
Before building the full Tower or a large town, the first playable prototype should prove the core loop with a deliberately small content set:
    • Character creation with one Soul Card.
    • A small party containing the protagonist and a few NPCs.
    • A small explorable town section.
    • One Tower level containing five possible floor types.
    • A small hex map with terrain and discovery layers.
    • At least one monster encounter and one non-combat discovery.
    • Basic card rewards and deck management.
    • Tired checks and visible exhaustion feedback.
    • Return-to-town and recovery.
    • One repeat expedition demonstrating persistent floor assignment and changing party/card choices.
The first prototype should prove that prepare → enter Tower → explore → encounter → collect cards → manage exhaustion → return → recover is fun and technically workable. Content quantity comes later.
19. Scope Boundary
Do not attempt to build the entire Tower, every NPC, or the full town before the vertical slice works. The project should preserve modularity so combat and other uncertain systems can be iterated independently.

Data Architecture & Card Schema
Core Philosophy

Cards are not written as prose that a human GM interprets. They are structured data that the game engine must be able to parse into concrete, deterministic actions.

Player-facing flavor text may describe what a card does, but flavor text is not mechanically authoritative and is not parsed to determine card behavior.

Mechanical behavior is defined by structured fields and references to other data definitions.

When a mechanic can be represented as a reusable definition, it should generally be defined once and referenced rather than duplicated across cards.

Card Data Organization

Card data may be divided into multiple human-readable spreadsheets by card type.

The final game data may combine these definitions or keep them as separate JSON files; this is an implementation decision and does not change the underlying schema.

Every card has a card_id that uniquely identifies it across all card-type sheets.

The card name may be duplicated in type-specific sheets for human readability. The name in those sheets is not used as the mechanical identifier; card_id is.

Universal card information belongs in the master card sheet. Type-specific mechanical information belongs in the appropriate type-specific sheet.

Examples of universal information include:

card_id
name
type
rarity
cost
consumable
player-facing flavor_text

Type-specific mechanical fields should not be placed in the master sheet merely for convenience.

Naming and Data Conventions

Column names use lowercase snake_case.

Examples:

card_id
effect_id
max_amount
damage_type

Do not introduce spaces or capitalization into column names.

Boolean values are represented as TRUE and FALSE.

IDs should be stable and unique. References between data definitions use IDs rather than display names.

Player-facing text may contain dynamic references using {}.

Example:

Create a bolt of acid that is then shot at a target within {range}.

A dynamic reference in flavor text should resolve from the actual mechanical value rather than hardcoding a value into the text.

Conjuration Cards

A Conjuration creates an item defined by the Item data.

A Conjuration is responsible for defining:

which item is created
how many are created
the maximum amount created
how long they exist
where they appear
any applicable range
the card's cost

Once created, the result is an ordinary item governed by the Item rules.

Conjuration does not perform attacks or apply effects merely because the resulting item has those capabilities. Any harmful or otherwise active behavior belongs to the appropriate mechanical system.

Conjuration Defaults

amount:

Blank → 1

max_amount:

Blank → same value as amount
-1 → unlimited

duration:

Blank → -1
-1 → indefinite duration

range:

Blank → self only

If an equipable item is conjured with a range, the range may be used to target an ally, but not an enemy, unless another rule explicitly permits enemy targeting.

If the relevant equipment slot is already occupied, the Conjuration fails.

If there is insufficient physical space to create/place the item, the Conjuration fails.

An item that has been successfully created does not retain special "conjured item" behavior; it becomes a normal item of its defined type.

Tower Floor Persistence

Cards are the persistent resource.

The Tower clears non-card resources/inventory when changing floors. Cards themselves are the exception and persist.

Therefore a card can be used to recreate equipment or other items on each floor.

duration = -1 means the created item remains indefinitely under normal item rules; it does not mean the item survives a Tower floor transition.

Attack Cards

Attack cards define how an attack is delivered and what Effects occur when it resolves.

Attack does not have a dedicated damage field.

Damage is an Effect.

An Attack therefore describes:

target pattern
range
resolution method
stat used for resolution
resulting Effects
Targeting

Attack targets are defined by a Target reference rather than directly describing the target geometry.

A target represents a pattern of squares, not necessarily a creature.

This allows attacks to target empty spaces as well as occupied spaces.

Examples of possible target definitions include:

a single square
a 2×2 area
a 5×5 area
a radius-based area
a line
other geometric patterns

An attack does not inherently require a mob to occupy its target.

An attack may therefore have an effect that produces something in an otherwise empty target square.

The Target system is separate from the Attack system and should be reusable by other mechanics where appropriate.

range is expressed in combat squares, not feet.

The game convention is that one combat square represents 3×3 feet. Player-facing rules may explain this conversion, but mechanical data uses squares.

Attack Resolution

Attack resolution is divided into two fields:

resolution

Allowed values currently include:

attack
save
auto
stat

If resolution is attack or save, stat specifies which stat or stats are used.

If resolution is auto, stat is blank.

A single stat means that stat is used.

Multiple stats separated by / mean that the highest applicable stat is used.

Examples:

dex → use DEX
mnd/dex → use the higher of MND or DEX
str/con/dex → use the highest of STR, CON, or DEX

This syntax is intentionally simple and is not an arbitrary expression language.

For an attack, the selected stat is the attacker's stat used for the attack.

For a save, the selected stat is the target's stat used for the save.

auto resolves automatically without a roll.

Effects

Effects are reusable mechanical operations.

Every Effect is an Effect regardless of whether it is primitive or composite.

There is no separate conceptual category for "composite effects." A composite Effect is simply an Effect whose behavior is defined in terms of other Effects.

Effects may be referenced by:

cards
other Effects
items
attacks
other systems that need to produce a mechanical result

This allows the same mechanical operation to be reused throughout the game.

Effect IDs Represent Operations, Not Configurations

Effect IDs identify an operation, not every possible configuration of that operation.

For example:

burning

is an Effect.

These are parameters:

1
2
3

Therefore the game should not require separate Effects such as:

burning_1
burning_2
burning_3

Instead:

burning 1

means the burning Effect with parameter 1.

Similarly:

basic acid

means the basic Effect with acid as its damage type.

basic fire

means the same basic Effect with fire as its damage type.

The parameters belong to the invocation of the Effect rather than being encoded into the Effect ID.

Effect Syntax

An Effect field contains one or more sequential Effect invocations.

/ separates individual Effect invocations.

Spaces separate an Effect ID from its parameters.

Example:

slow 1 / fire_damage 1

means:

Execute slow with parameter 1.
Execute fire_damage with parameter 1.

The exact number and meaning of parameters are defined by the referenced Effect.

Effects are always resolved from left to right.

There is no simultaneous-effect mechanic.

If two Effects should not interfere with one another, their order should be deliberately chosen so that they resolve in the desired order.

The order in the Effect field is mechanically significant and must be preserved by the parser and runtime.

Composite Effects

A composite Effect is simply an Effect whose component Effects are listed in order.

For example:

slow 1 / wait 1 / heal MAX / remove_debuff / milk

would resolve as:

Apply Slow 1.
Wait one round.
Heal to the specified amount.
Remove debuffs.
Apply the Milk effect.

Composite Effects may reference other composite Effects.

Effects must not be allowed to create an infinite reference cycle, either directly or indirectly.

For example:

A → B → C → A

is invalid.

Damage

Damage is an Effect rather than a dedicated Attack field.

Effort-based damage uses the appropriate effort definition plus a damage type.

For example:

basic acid

means Basic Effort acid damage.

The standardized effort values are defined centrally so that changing an effort value changes every mechanic using that effort consistently.

Static damage may also exist as a separate damage Effect when needed, particularly for effects originating from items or other systems.

For example:

damage 7 acid

would represent 7 static acid damage.

This allows cards, items, attacks, and other mechanics to use the same underlying damage system.

Flavor Text

Flavor text is primarily player-facing information and is not mechanically authoritative.

It may contain both:

actual flavor
concise explanations of what the card does

Flavor text may reference mechanical values using {}.

References should be used instead of hardcoding values that may change.

For example:

Shoot a bolt of acid at a target within {range}.

If the card's range changes, the displayed text should automatically reflect the new value.

Dynamic references may also expose information about referenced Effects, Items, or other definitions when the UI supports it.

For example, {fire_damage} may display the Effect's name and/or flavor explanation when hovered.

Design Principle: Prefer Composition Over Duplication

When a new card needs a variation of an existing mechanic, prefer changing parameters or composing existing Effects rather than creating a new hardcoded Effect or special-case Attack rule.

For example:

basic fire / burning 1

is preferable to creating a separate fire_damage_burning_1 Effect.

Similarly, an Attack should reference Effects rather than having special fields for every possible consequence of an attack.

The goal is for the data to describe combinations of well-defined mechanical primitives rather than requiring a unique implementation for every card.

Current Architectural Relationship

The current conceptual structure is:

Card
→ references a card type's mechanical definition

Attack
→ references Target + Effects

Conjuration
→ references Item

Effect
→ may execute directly or reference other Effects

Item
→ defines the rules of an item

Target
→ defines a geometric targeting pattern

Stat / Effort definitions
→ provide standardized reusable values

This architecture is intentionally modular. New card mechanics should generally reuse existing definitions before introducing new special-case fields or systems.