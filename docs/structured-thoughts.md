# Structured thoughts

Organizes the raw notes from [`scattered-thoughts.md`](./scattered-thoughts.md)
into a clearer shape. Still a working design doc, not final — gaps are
marked `(?)` and get filled in as answers come in.

---

## World

- Shape: a sphere, real planet size.
- The player can travel all over it (no artificial map boundary).

## Modes

Two named modes (aliases from the raw notes: "god mode" → **Genesis Mode**;
"player mode" / "interactive mode" → **Mortal Mode**).

### Genesis Mode
- Active at game start, for an initial 10-minute window.
- Free, unlimited terraforming/world design — change anything, anywhere, no lag.
- Regained later after 100 years of game time (placeholder number, tunable —
  only the year count is expected to change).
- Decisions the player can make in Genesis Mode:
  1. Size of the planet.
  2. Star/stars present in the solar system.
  3. Location of the planet within the solar system.
  4. Planet's tilt, and magic system(s) on the planet (or no magic system).
  5. Moon/moons located on the planet.
  6. Planet terrain (desert/water/etc.) — also depends on the planet's
     position (from #3).
  7. Day length / year length (rotation speed / orbital period).
  8. Gravity strength.
  9. Water coverage % (ocean vs land ratio).
  10. Continent/tectonic layout (number of continents, mountain range placement).
  11. Natural hazards (volcanism, storms, seismic activity) as an ambient
      risk setting.
  12. Ring system around the planet (world-flavor option).

### Mortal Mode
- Starts once the initial Genesis Mode window closes.
- Two internal sub-modes:
  - **Wanderer Mode** — roams the world on foot, hands-on terrain shaping
    with tools (e.g. a shovel).
  - **Steward Mode** — places buildings for builders to construct
    (construction limited by builder time, not instant) and governs
    society (see Society).
- Player leads/governs all societies they still control (see Society).
- Player is ageless but not immortal.
- Death condition: if a society's resentment grows out of control, it riots
  and kills the player → game over.
- As the player's agelessness becomes noticed, people outside the societies
  the player controls may become obsessed with it and try to murder the
  player to learn their secret. People within the player's own controlled
  societies consider it natural and don't react this way.
- If the player gives up (see Society) or loses every society they control,
  they lose governance/building ability entirely. The only way back in: kill
  the leader of a monarchy or dictatorship (an assassination, not an army
  conquest, since the player controls no society to attack with) — this
  restores a foothold and governance access.

## UI / architecture

- Game logic and UI are kept separate.
- Multiple different UIs (different styles) can drive the same underlying game.
- The core game must run with a bare-bones, asset-less UI, or even a pure
  terminal (text-only) interface — the strongest form of the separation
  requirement: game logic can never assume any particular rendering/UI
  exists at all. Terminal (ASCII) art is an acceptable presentation for
  the terminal interface — the requirement is no dependency on graphical
  assets, not literally no visuals at all.

**Feasibility:** high, and cheap if adopted from the start.
- Godot supports this natively: core game state lives in UI-agnostic
  autoloads/Resources that emit signals; any UI (a `Control` scene tree)
  only ever listens to signals / calls a defined API — never reaches into
  game internals directly. Swapping a whole UI is then just loading a
  different scene against the same API. Simple restyling (fonts/colors)
  is handled by Godot `Theme` resources on top of that.
- The real cost is upfront discipline: defining and sticking to a
  signals-in/calls-out API surface between game and UI. Cheap if done from
  the first line of game-logic code, expensive to retrofit later.
- Synergy: since UI never touches authoritative state directly, moving
  that state to a server later (multiplayer) is a much shorter hop —
  same architectural decision serves both goals.
- Scope note: the separation makes adding a second/third UI *possible and
  cheap*, not free — each additional UI style is still real work to build.
  No need to build an actual UI-swapping framework until there's a second
  UI to swap to; milestone 1 has no need for it yet.

## Beings

- Game settings control which being types can appear in the world.
- Types: humanoid, animals, spirits of things, hive-mind beings.
- Intelligence levels: human, baby, animal, single instinct/rule.

## Society

- Settings define a society type per area: capitalist, communist, slave
  economy, etc.
- Rule-adherence spectrum per society:
  1. Robots — rules always followed exactly.
  2. Real — most follow rules, some break them.
  3. Chaotic — most don't follow rules.
- Every society harbours resentment, driven by both world events (famine,
  disasters, being behavior, etc.) and the player's own decisions/decrees.
  If it grows out of control, that society riots and kills the player
  (see Player mode above).
- Societies progress through ages (e.g. stone age onward). Every new society
  starts at stone age, capped at the max age reached by any existing society
  in the game.
- The planet can have multiple societies across different areas; the player
  leads/controls all of them, not just one.
- The player can give up part or full control of a society by installing a
  parliament or a different leader. Once given up, that society becomes
  independent and makes its own decisions.
- A given-up society can only be reclaimed by conquering it with force,
  attacking it using another society the player still controls. (If the
  player controls no societies at all, the recovery path is different —
  see Mortal Mode above.)

---
