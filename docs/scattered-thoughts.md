# Scattered thoughts

Informal running notes — half-formed ideas, questions, things to revisit.
Not polished, not authoritative. Promote anything that solidifies into
`README.md`, an ADR, or an issue once it's actually decided.

---

## World scale

- Want to build the world at real planet size, not a small bounded map.
- It's a sphere — the player can travel all over it.

## Game mechanics

- Keep game logic and UI separate.
- Want multiple separate UIs (different styles) able to work with the same game.
- Mainly a world builder, but the player can switch into another mode and interact with the actual world.

## Beings

- Settings to control what types of beings can be present in the game.
- Types:
  - Humanoid
  - Animals
  - Spirits of things
  - Beings with hive mind
- Intelligence levels:
  - Human level
  - Baby level
  - Animal level
  - Just a single instinct or rule

## Society

- Settings can have a society type per area.
  - Capitalist
  - Communist
  - Slave economy
  - etc.
- How much the society follows rules:
  1. Robots — all rules are followed exactly
  2. Real — most follow rules, some people can break them
  3. Chaotic — most people don't follow rules
- Every new society can only start at stone age, up to the max age of any existing society in the game.
- Player can give up part or complete control of a society by creating a parliament or a different leader.
- Once given up, the society becomes independent and makes its own decisions.
- Player can't regain it back unless they conquer it again by force, attacking it with another society the player controls.

## God mode / Player mode

- Two modes: god mode and player mode.
- At game start, player gets power to design the entire world, with a 10 minute timer.
- God mode: timer never ends, player can change the planet at any time, no time lag.
- Player mode:
  - Player uses settings to design the planet within the 10 minutes.
  - After 10 minutes, the world freezes and the player loses the design power.
  - Player becomes the leader, with authority.
  - Player is ageless but not immortal.
- Every society harbours resentment.
  - If resentment grows out of control, the society riots and kills the player.
  - Death of the player is game over.
- If the player gives up control of all societies in the world, he loses interactive mode — the ability to shape society and place buildings. The player only exists in interactive mode.
- More and more people might get obsessed with the player's agelessness and try to murder the player to find his secret.
- People of the society the player controls don't get obsessed with this — they consider it natural. People of other societies get obsessed.
- If the player kills a leader of a monarchy or dictatorship, only then can he get back access to another mode.
