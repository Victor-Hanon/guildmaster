# Credits

Guildmaster is a small layer built on top of the work of many open-source projects. **Guildmaster did not create AzerothCore, mod-playerbots or the Playerbots AI.** It runs them, modifies one module, and adds its own API, phone app and launcher.

Licence details, versions and full licence texts are in [THIRD-PARTY-NOTICES.md](THIRD-PARTY-NOTICES.md) and in the [licenses](licenses/) folder.

## The game server

- **AzerothCore** (https://www.azerothcore.org, https://github.com/azerothcore/azerothcore-wotlk): the World of Warcraft 3.3.5a server emulator that Guildmaster runs. Guildmaster uses the `Playerbot` branch maintained by the mod-playerbots project (https://github.com/mod-playerbots/azerothcore-wotlk). Thanks to the AzerothCore developers and to the MaNGOS, TrinityCore and SunwellCore projects it descends from.
- **mod-playerbots** (https://github.com/mod-playerbots/mod-playerbots): the AzerothCore module that adds player-like bots. It is based on **IKE3's Playerbots** (https://github.com/ike3/mangosbot), on ZhengPeiRu21/mod-playerbots and on celguar/mangosbot-bots, and continues the Playerbot AI lineage started by ike3 for the MaNGOS and TrinityCore family, then carried on by CMaNGOS playerbots. Guildmaster's engine (wild adventurers, recruitment, settlements, expeditions, guild representative) is a series of modifications to this module; everything else in it is the work of the mod-playerbots authors.
- **mod-wowquarium**: an AzerothCore module written alongside Guildmaster, which records the life of the bots (deaths, levels, zones).
- Libraries compiled into the server through AzerothCore: Boost, {fmt}, SFMT, Argon2, G3D (g3dlite), Recast/Detour, zlib, UTF8-CPP and gSOAP.

## Data and runtime

- The server data (maps, vmaps, mmaps, dbc) are extracted on your computer from your own World of Warcraft client by the extractors of AzerothCore. Guildmaster does not host, download or redistribute these files. Thanks to the **wowgaming/client-data** project, whose packaged data served the private test versions.
- **MySQL Community Server** (https://www.mysql.com), by Oracle: the local database.
- **Node.js** (https://nodejs.org): runs the Guildmaster API and serves the app.
- **OpenSSL** (https://www.openssl.org): cryptography used by the server.
- **Microsoft Visual C++ runtime**: needed by the server and the database.
- **Figtree** (Erik Kennedy and The Figtree Project Authors, SIL Open Font License 1.1): the font of the launcher, the installer, the app and the in-game addons.
- The map background of the app is drawn on your computer by Guildmaster from the terrain files extracted from your client (no tile is shipped), and the item icons, like the Horde and Alliance emblems shown by the launcher, are extracted on your computer from your own World of Warcraft client: no Blizzard image is shipped for them.

## The API and the app

- **mysql2** (https://github.com/sidorares/node-mysql2) by Andrey Sidorov and contributors, with its dependencies aws-ssl-profiles, denque, generate-function, iconv-lite, is-property, long, lru.min, named-placeholders, safer-buffer, seq-queue and sqlstring.
- **React** and **React DOM** (https://react.dev), with **scheduler**, by Meta Platforms, Inc. and affiliates.
- **Vite** (https://vite.dev), which builds the app and adds a small loading helper to it.

## In-game addons

- **Guildmaster** (formerly GuildmasterRoF) and **GuildmasterCommand**: the in-game addons that the launcher installs in your client's `Interface\AddOns`. Written for Guildmaster, MIT licence (the `LICENSE` file of each addon folder). No code was taken from other addons: the existing Playerbots addons (MultiBot and others, GPL) were only studied for their public behaviour.

## World of Warcraft

World of Warcraft, Warcraft and Blizzard Entertainment are trademarks or registered trademarks of Blizzard Entertainment, Inc. Guildmaster is a fan project. It is not affiliated with, endorsed or sponsored by Blizzard Entertainment, and it does not include any World of Warcraft client files: you need your own World of Warcraft 3.3.5a client.

## Guildmaster

The Guildmaster API, phone app, launcher, installer and engine changes are written by the Guildmaster team. Guildmaster's own code is licensed under the GNU Affero General Public License v3.0 or later; the engine changes follow the licence of mod-playerbots (GNU GPL v2 or later); the addons are under the MIT licence (see [THIRD-PARTY-NOTICES.md](THIRD-PARTY-NOTICES.md)).

The illustrations of the app and of the launcher are fan art set in the Warcraft universe, generated for Guildmaster with an image generator (ChatGPT). They are not Blizzard artwork. The Horde and Alliance emblems shown by the app and the launcher are read from your own World of Warcraft client and are never shipped.
