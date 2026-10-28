# Guildmaster

[Version française](README.fr.md)

**Manage your guild from anywhere. Join them in Azeroth when you come home.**

### [See the game on the website: guildmaster-game.pages.dev](https://guildmaster-game.pages.dev)

**[⬇ Download the installer (Windows, 197 MB)](https://github.com/Victor-Hanon/guildmaster/releases/download/v0.5.1-alpha.1/Guildmaster-Setup-0.5.1-alpha.1.exe)** · **[Website](https://guildmaster-game.pages.dev)** · **[Discord](https://discord.gg/tGQMVByaH7)** · **[Support on Ko-fi](https://ko-fi.com/ragolk)**

Guildmaster brings to life, on your computer, an offline World of Warcraft 3.3.5a world populated by autonomous adventurers. They
are born, level up and die; you recruit them into your guild, send them exploring, gathering and hunting from the Guildmaster app
(on your PC or your phone), and log into the game whenever you want to fight beside them.

Free. One world per player, on their own PC. No online server, no Guildmaster account.

> Guildmaster is an unofficial fan project. It is not affiliated with or endorsed by Blizzard Entertainment.
> A World of Warcraft 3.3.5a client that you own is required; it is not provided.

## Download

Latest version: the [Releases](https://github.com/Victor-Hanon/guildmaster/releases) page. Download `Guildmaster-Setup-<version>.exe` and check its SHA-256 (the
`.sha256` file next to it, or `certutil -hashfile Guildmaster-Setup-<version>.exe SHA256`).

Windows may show "Windows protected your PC": the installer is not signed yet. Click "More info", then "Run anyway", after checking
the checksum.

## Requirements

| | |
|---|---|
| System | Windows 10 or 11, 64-bit (tried on Windows 11). |
| Game client | World of Warcraft 3.3.5a (build 12340), French (frFR) or English (enUS), that you own (tested with the French client; English client not tested yet). Guildmaster reads its files on your PC to prepare the server data and the icons; it does not change it, apart from `realmlist.wtf` (restored on request) and the Guildmaster addons in `Interface\AddOns`. |
| Disk space | Allow about 10 GB free: program about 0.4 GB, world data after creation about 8.4 GB, plus room for your backups. |
| Memory | 16 GB recommended, with about 6 GB free for the first start; in game, the server uses about 5 GB. |
| Internet | To download the installer and the updates. The world then runs offline. |

## Install and play

1. Run the installer and choose the installation folder.
2. In the launcher, point to your WoW 3.3.5a client folder.
3. Create your world: faction, race, guild name, death mode (normal or hardcore).
4. Wait while your world is created, the first time only: about 25 to 50 minutes depending on the PC. Guildmaster prepares the
   maps, the scenery and the creatures' paths from your own client. Later starts take about 1 minute.
5. Click PLAY, or open the Guildmaster app.

Known issues: [KNOWN-ISSUES.md](KNOWN-ISSUES.md). What comes next: [ROADMAP.md](ROADMAP.md).

## Updates

The launcher offers new versions; you may decline and keep playing yours. Before an update your world is backed up; it is restored
automatically if anything fails.

## Source

- The game server (AzerothCore, mod-playerbots modified by Guildmaster, mod-wowquarium) is distributed under the GNU GPL v2 or later
  and the GNU AGPL v3 or later. Its complete source, at the exact revisions of each version, is attached to every release
  (`Guildmaster-<version>-server-source.tar.gz`).
- Guildmaster's own code (API, app, launcher, installer, runtime tools) is distributed under the GNU AGPL v3 or later ([LICENSE](LICENSE));
  the in-game addons under the MIT licence. Its source, at the exact revision of each version, is also attached to every release
  (`Guildmaster-<version>-source.tar.gz`).
- Components and their licences: [THIRD-PARTY-NOTICES.md](THIRD-PARTY-NOTICES.md); thanks: [CREDITS.md](CREDITS.md).

## Warnings

Alpha: expect defects, make backups. In hardcore mode, death is permanent, for adventurers and for your own characters. Please read
[DISCLAIMER.md](DISCLAIMER.md).

## Contact

Discord: https://discord.gg/tGQMVByaH7 · Website: https://guildmaster-game.pages.dev · Report a defect: [Issues](https://github.com/Victor-Hanon/guildmaster/issues).

World of Warcraft, Warcraft and Blizzard Entertainment are trademarks or registered trademarks of Blizzard Entertainment, Inc.
