# Known issues

[Version française](KNOWN-ISSUES.fr.md) · [Back to the README](README.md)

Guildmaster 0.6.0-alpha.6. Defects and limitations we know of in this version. If you hit something that is not listed, please
report it in the bug forum of the [Discord](https://discord.gg/tGQMVByaH7) (the launcher's "Report a bug" button prepares the
report) or open an [issue](https://github.com/Victor-Hanon/guildmaster/issues).

## Installation and launcher

- **Windows only.** 64-bit Windows 10 or 11 (tried on Windows 11). No Mac or Linux version.
- **English client not tested yet.** 0.6.0-alpha.6 is tested with the French client (frFR); the English client (enUS) is planned
  but has not been tried.
- **The first world creation is long**: about 25 to 50 minutes depending on the PC, more than an hour on a slower PC, once only; later starts take
  about 1 minute (up to about 10 minutes on a slower PC). Do not close the launcher during the creation.
  Keep the PC on, not asleep. Allow about 10 GB free and 16 GB of memory, with about 6 GB free for the first start: close heavy
  programs before you start the creation.
- **Unsigned installer.** Windows may show "Windows protected your PC": click "More info", then "Run anyway", only after checking
  the SHA-256 checksum published with the release.
- **No restore button yet.** The launcher backs up your world, but you cannot restore a backup yourself from the launcher yet.

## In game

- **"Sur moi" (On me)** works only in five-player dungeons; not in raids, battlegrounds or arenas.
- **One of your characters in another settlement.** Since 0.5.1, one of your characters belongs to the settlement whose tavern
  holds its hearthstone, and "Settle here" on its card in the app attaches it to the settlement whose tavern it is in. If the app
  still shows it as "far from its settlement", it tells you why; otherwise, bring it back to the tavern of its own settlement and
  log out there.

## Squads

- **A squad leader may wait forever** for a member left behind. During a squad gathering round, the round's progress says who the
  leader is waiting for.

## Death, resurrection and dungeons

- **A dead member who reconnects comes back as a ghost.** In hardcore mode, a fallen member waits 10 minutes for a member of their
  group to raise them. If they are disconnected during the wait (or the world restarts), they come back as a ghost, which the other
  adventurers do not raise: their death becomes final after the 10 minutes.
- **Druid Rebirth on cooldown.** A druid in the group whose Rebirth is on cooldown still counts as a healer able to raise: the death
  only becomes final at the end of the 10 minutes, not at once.
- **"Release Spirit" is not refused** for a fallen member.
- **One dungeon for expeditions**: Ragefire Chasm. For every campaign dungeon, Ragefire included, the step counts once your guild
  has killed every boss of the dungeon, in an expedition launched from the app or in a group you lead; bosses already killed by your
  guild count.
- **Group level not checked in dungeons yet.** The bosses may fall over several runs, and a group above the dungeon's level
  validates it too. A later version will require every boss in the same run, with nobody above the dungeon finder's maximum level
  (21 for Ragefire Chasm).
- **A danger seen is not forgotten.** A square where a squad retreated from a danger stays marked "danger" on the map and is no
  longer offered to missions. Since 0.6.0-alpha.3, only hostile creatures trigger the retreat (not neutral guards, as in Ratchet).

## Fleet (new in 0.6.0-alpha.6)

- **One ship and one port.** The fleet of this version has one ship, bought at the Ratchet trading post. It leaves Ratchet and comes
  back after one hour.
- **Raw materials only.** Only the raw materials deposited in the guild chest are shipped (253 goods). Tools, equipment and quest
  items stay in the chest.

## The new app

- **The new interface** (home, adventurer cards, map, Memorial, Crafting, Management, chest and stewardship) was proven on the
  development worlds. Tell us what looks wrong.
- **The fleet, squad gathering rounds and the new chapters of the orc campaign** were proven on the development worlds, not yet in
  a game installed by the public installer.

## Not available yet

Other dungeons than Ragefire Chasm for expeditions, other ships and ports, boats without you. See the [roadmap](ROADMAP.md).
