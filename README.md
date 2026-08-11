# YDWS (Yet Different World Simulator)

A terraforming world simulator built in Godot 4 (3D). Shape terrain, water,
and weather from a god's-eye view, then drop into a third-person character
to walk the world you've built. Designed from the ground up for a shared,
persistent multiplayer world.

## Status: Pre-development — project setup

No gameplay code yet. Currently laying the legal/licensing and contribution
groundwork before development starts.

- [x] Project concept and scope defined
- [x] Engine chosen: Godot 4
- [x] License chosen: AGPLv3 (open core — see below)
- [x] `LICENSE` (AGPLv3) added
- [x] `CLA.md` (Contributor License Agreement) added
- [x] CLA enforcement bot (`contributor-assistant/github-action`) configured
- [x] CLA bot tested end-to-end
- [ ] Branch protection requiring CLA + CI checks
- [ ] First engineering milestone: terrain sculpt tool + god-view camera

## License model

YDWS is open source under AGPLv3 — see [`LICENSE`](./LICENSE). The client
and reference server are open; the production/managed server (hosting
optimizations, scaling, ops) is proprietary and closed-source, communicating
with clients only over the same open protocol.

Contributors sign a CLA (see [`CLA.md`](./CLA.md)) before their first
contribution is merged, granting the maintainer rights to use contributions
in both the open (AGPLv3) codebase and the closed managed server.

## Roadmap (high level)

1. Terrain sculpt tool + god-view camera (single-player prototype)
2. Third-person character controller + mode switch, with live terrain collision
3. Core "bridge" mechanic linking terraforming to on-ground gameplay
4. First simulated ecosystem layer (vegetation reacting to terrain/water)
5. Networked architecture: authoritative server, chunked terrain sync
6. Session-based multiplayer (Valheim-style) as an intermediate milestone
7. Persistent shared-world server, scaling, and live-ops

## Contributing

Contributions are welcome once the codebase is further along. All
contributors must sign the CLA before a pull request can be merged — see
[`CLA.md`](./CLA.md) for details.
