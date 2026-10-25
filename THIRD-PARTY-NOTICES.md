# Third-party notices

This file lists the third-party software shipped in the Guildmaster Windows installer, **Guildmaster-Setup-0.5.0-alpha.1.exe** (alpha), with its licence and the file that holds the licence text. Paths are relative to the installation folder. Licence texts are in the [licenses](licenses/) folder of this repository.

Composition of 0.5.0-alpha.1: engine = mod-playerbots modified by Guildmaster, revision `af5143d9` (the SHA-256 of worldserver.exe is written in `runtime\version.json` when the installer is built), mod-wowquarium revision `6980d0c`, AzerothCore revision `06234df3d5ab`; API, app and launcher: revision `4396f59` of Guildmaster. The exact references of each build are written in `runtime\version.json`.

## Guildmaster's own code

Guildmaster's own code (the API under `runtime\api`, the app under `runtime\app`, the launcher `Guildmaster.exe`, the installer and the tools under `runtime\tools`) is Copyright 2026 The Guildmaster authors and is licensed under the **GNU Affero General Public License, version 3 or (at your option) any later version** (SPDX: `AGPL-3.0-or-later`). The full text is in `licenses/AGPL-3.0.txt`. It comes with ABSOLUTELY NO WARRANTY, to the extent permitted by law (sections 15 and 16 of the licence). The API and the tools are shipped as readable source code; the app is shipped as a built bundle, and its source is attached to the same release as `Guildmaster-0.5.0-alpha.1-source.tar.gz` (section 1 below).

The changes made by Guildmaster to mod-playerbots are part of that module and are distributed under its licence (GNU GPL v2 or later, section 1). The in-game addons are under the MIT licence (section 5 ter).

## 1. Game server: `runtime\server\worldserver.exe`, `runtime\server\authserver.exe`, and the data extractors

These programs are compiled by the Guildmaster team from the following sources. The data extractors of AzerothCore, `runtime\server\extracteurs\map_extractor.exe`, `runtime\server\extracteurs\vmap4_extractor.exe`, `runtime\server\extracteurs\vmap4_assembler.exe` and `runtime\server\extracteurs\mmaps_generator.exe` (with `mmaps-config.yaml`), are compiled from the same AzerothCore revision; their revision and checksums are written in `runtime\version.json` (`extracteurs`). They run on your computer to build the server data from your own client (section 6).

| Component | Version | Licence | Licence text |
|---|---|---|---|
| AzerothCore, `Playerbot` branch of https://github.com/mod-playerbots/azerothcore-wotlk | revision `06234df3d5ab` (11 September 2026), unmodified | GNU GPL v2 or later for most files; **GNU AGPL v3 or later** for some files (see below) | `licenses/GPL-2.0.txt`, `licenses/AGPL-3.0.txt` |
| mod-playerbots, https://github.com/mod-playerbots/mod-playerbots, modified by Guildmaster | revision `af5143d9`, based on upstream revision `b6696bdb` | GNU GPL v2 or later | `licenses/GPL-2.0.txt` |
| mod-wowquarium, module written alongside Guildmaster | revision `6980d0c` (23 October 2026) | GNU GPL v2 or later (it is linked into the server) | `licenses/GPL-2.0.txt` |

Files under the GNU AGPL v3 or later in AzerothCore revision `06234df3d5ab` include `src/server/game/Entities/Creature/Trainer.cpp`, `src/server/game/Server/Packets/NPCPackets.cpp` and the files of `src/server/game/TC9Sidecar/` (15 compiled files carry an AGPL header in that revision: 9 in `TC9Sidecar`, 2 in `Entities/Creature`, 2 in `Server/Packets`, 1 in `scripts/EasternKingdoms`, 1 in `scripts/Kalimdor`; one more AGPL file, `deps/acore/joiner`, is a build helper). Both licence texts are therefore provided with the server.

Libraries compiled into the server by the AzerothCore build:

| Library | Version | Licence | Licence text |
|---|---|---|---|
| Boost | 1.81.0 | Boost Software License 1.0 | `licenses/BSL-1.0.txt` |
| {fmt} | 12.1.0 | MIT-style ({fmt} licence) | `licenses/fmt-LICENSE.txt` |
| SFMT (SIMD-oriented Fast Mersenne Twister) | copy in AzerothCore `deps/SFMT` | BSD 3-Clause | `licenses/SFMT-LICENSE.txt` |
| Argon2 reference implementation | copy in AzerothCore `deps/argon2` | CC0 1.0 or Apache 2.0, at your option | `licenses/Argon2-LICENSE.txt` |
| G3D (reduced copy "g3dlite") | copy in AzerothCore `deps/g3dlite` | Modified BSD | `licenses/G3D-LICENSE.txt` |
| Recast/Detour | copy in AzerothCore `deps/recastnavigation` | zlib licence | `licenses/RecastNavigation-LICENSE.txt` |
| zlib | 1.3.1 | zlib licence | `licenses/zlib-LICENSE.txt` |
| UTF8-CPP | copy in AzerothCore `deps/utf8cpp` | Boost Software License 1.0 | `licenses/UTF8-CPP-LICENSE.txt` |
| gSOAP runtime | 2.8.105 | GNU GPL v2 or later, or gSOAP public license 1.3 | `licenses/gSOAP-LICENSE.txt` |

Libraries loaded by the server from the same folder:

| File | Component | Version | Licence | Licence text |
|---|---|---|---|---|
| `libcrypto-3-x64.dll`, `libssl-3-x64.dll`, `legacy.dll` | OpenSSL | 3.5.8 | Apache License 2.0 | `licenses/Apache-2.0.txt` |
| `libmysql.dll` | MySQL client library (Connector/C) | 8.0.45 | GNU GPL v2 with the Universal FOSS Exception 1.0 | `runtime\database\mysql\LICENSE` |
| `msvcp140.dll`, `vcruntime140.dll`, `vcruntime140_1.dll` | Microsoft Visual C++ runtime | | Microsoft Visual Studio "Distributable Code" terms | not included |

### Source code of the server (GNU GPL v2 section 3, GNU AGPL v3 sections 6 and 13)

`worldserver.exe` and `authserver.exe` are distributed in compiled form. Their complete corresponding source code is:

- AzerothCore, `Playerbot` branch of mod-playerbots/azerothcore-wotlk, revision `06234df3d5ab`;
- mod-playerbots as modified by Guildmaster, revision `af5143d9`;
- mod-wowquarium, revision `6980d0c`;
- the build configuration used for this release.

Where to get it: on the release page from which this installer is downloaded (the release of version `0.5.0-alpha.1` in the public Guildmaster distribution repository on GitHub), as the file `Guildmaster-0.5.0-alpha.1-server-source.tar.gz`, published at the same time as the installer and listed with its SHA-256 in the `checksums.sha256` file of the same release. That archive holds the three source trees above at their exact revisions (without version-control history) and the build configuration (`BUILD.md`). The source of Guildmaster's own programs (API, app, launcher, installer, runtime tools, in-game addons) at the revision of this build (`4396f59`) is the file `Guildmaster-0.5.0-alpha.1-source.tar.gz` of the same release, also listed in `checksums.sha256` (contents in its `SOURCE-REVISIONS.txt`). This is equivalent access to the source from the same place as the installer (GNU GPL v2 section 3; GNU AGPL v3 section 6 d). The source of MySQL 8.0.45 (section 2) is Oracle's official source archive of that version; it is available on request through the support channel, under the same conditions as below.

If you received this installer from anywhere else, or if the release page is no longer available, you may ask for the complete corresponding source through the support channel listed in the README of the distribution repository; it will be provided at no more than the cost of providing it, for at least three years after the last distribution of this version.

`authserver.exe` is compiled from the same AzerothCore revision `06234df3d5ab`. The tools that extract the server data from your own World of Warcraft client (map, vmap and mmap extractors of AzerothCore) are compiled from the same AzerothCore revision and are covered by the same offer.

## 2. Database: `runtime\database\mysql`

| Component | Version | Licence | Licence text |
|---|---|---|---|
| MySQL Community Server (portable files) | 8.0.45 | GNU GPL v2 with Oracle's additional permissions and the Universal FOSS Exception 1.0 | `runtime\database\mysql\LICENSE` (Oracle's licensing information, including the notices of the third-party software inside MySQL) |

`runtime\database\graine` is the seed of a new world. It holds database structure and reference data from AzerothCore and mod-playerbots (GNU GPL v2 or later, see above) and the Guildmaster tables. It contains no player data.

## 3. Node.js: `runtime\node\node.exe`

| Component | Version | Licence | Licence text |
|---|---|---|---|
| Node.js | 24.11.1 | MIT, plus the licences of the libraries built into Node.js | `licenses/Node.js-LICENSE.txt` (LICENSE file of the v24.11.1 tag) |

## 4. API: `runtime\api\node_modules`

| Package | Version | Licence | Licence text |
|---|---|---|---|
| mysql2 | 3.15.3 | MIT | `licenses/npm/mysql2-LICENSE.txt` |
| aws-ssl-profiles | 1.1.2 | MIT | `licenses/npm/aws-ssl-profiles-LICENSE.txt` |
| denque | 2.1.0 | Apache License 2.0 | `licenses/npm/denque-LICENSE.txt` |
| generate-function | 2.3.1 | MIT | `licenses/npm/generate-function-LICENSE.txt` |
| iconv-lite | 0.7.2 | MIT | `licenses/npm/iconv-lite-LICENSE.txt` |
| is-property | 1.0.2 | MIT | `licenses/npm/is-property-LICENSE.txt` |
| long | 5.3.2 | Apache License 2.0 | `licenses/npm/long-LICENSE.txt` |
| lru.min | 1.1.4 | MIT | `licenses/npm/lru.min-LICENSE.txt` |
| named-placeholders | 1.1.6 | MIT | `licenses/npm/named-placeholders-LICENSE.txt` |
| safer-buffer | 2.1.2 | MIT | `licenses/npm/safer-buffer-LICENSE.txt` |
| seq-queue | 0.0.5 | MIT (stated in its LICENSE file; its package.json declares none) | `licenses/npm/seq-queue-LICENSE.txt` |
| sqlstring | 2.3.3 | MIT | `licenses/npm/sqlstring-LICENSE.txt` |

Each package also keeps its own licence file in its folder.

## 5. App: `runtime\app\dist`

The app is a single bundled web application. The bundle contains code from:

| Package | Version | Licence | Licence text |
|---|---|---|---|
| react | 19.2.8 | MIT | `licenses/npm/react-LICENSE.txt` |
| react-dom | 19.2.8 | MIT | `licenses/npm/react-dom-LICENSE.txt` |
| scheduler | 0.27.0 | MIT | `licenses/npm/scheduler-LICENSE.txt` |
| vite (loading helper added by the build) | 7.3.6 | MIT | `licenses/npm/vite-LICENSE.txt` |

The app icons were made for Guildmaster. Item icons shown by the app are not shipped: the launcher extracts them on your computer from your own World of Warcraft client (`runtime\tools\icones.mjs`).

## 5 bis. Fonts: `Guildmaster.exe`, installer, `runtime\app\dist`

| Font | Licence | Licence text |
|---|---|---|
| Figtree (The Figtree Project Authors), embedded in the launcher and the installer as static instances renamed « Figtree GM » (400, 600, 700), in the app, and in the two in-game addons (`runtime\addons\<addon>\Media\Figtree-GM*.ttf`, same renamed instances) | SIL Open Font License 1.1 | `licenses/OFL-Figtree.txt`; for the addons, also `runtime\addons\<addon>\Media\OFL-Figtree.txt` |

## 5 ter. In-game addons: `runtime\addons`

| Component | Version | Licence | Licence text |
|---|---|---|---|
| Guildmaster (guild management in game, Guildmaster protocol V1; formerly named GuildmasterRoF) | 1.3.0 | MIT | `runtime\addons\Guildmaster\LICENSE` |
| GuildmasterCommand (order bar for companions; its "Sur moi" summon order works only inside a five-player dungeon) | 0.4.0 | MIT | `runtime\addons\GuildmasterCommand\LICENSE` |

These two addons are written by the Guildmaster team and contain no third-party code. Their `Media` folders hold textures drawn for the project (circle, rings, shadow, an icon sheet made from the project's own symbols) and the Figtree GM font with its licence (section 5 bis). The launcher removes the old `GuildmasterRoF` folder (after a backup) when it installs the renamed addon. The launcher copies them into `Interface\AddOns` of the player's own WoW client; `runtime\addons\SOURCE.json` records their origin and the SHA-256 of every file.

## 6. Data extracted on your computer from your own client (not shipped)

No server data is downloaded. When a world is created, the launcher runs the extractors of AzerothCore (`map_extractor.exe`, `vmap4_extractor.exe`, `vmap4_assembler.exe`, `mmaps_generator.exe`, section 1) on the World of Warcraft 3.3.5a client that you chose, to build the server data (dbc, maps, vmaps, mmaps). These files are derived from your own client; they are written in your installation folder and are never shipped, hosted or downloaded by Guildmaster. In the same way, the launcher reads the item icons and the Horde and Alliance emblems from your client (`runtime\tools\icones.mjs`, `runtime\tools\emblemes.mjs`); no Blizzard image is shipped for them.

## 6 bis. Map background

The map background of the app (atlas tiles, written in `user-data\world\atlas` by `runtime\tools\atlas-joueur.mjs`) is drawn on your computer by Guildmaster's own code from the terrain files extracted above (`maps/*.map`, `dbc/AreaTable.dbc`): land tinted by zone, soft relief, water and borders. No Blizzard image or texture is read or copied, and no tile is shipped.

## 6 ter. Reference tables derived from the game client: `runtime\api\contrat\donnees`, `runtime\api\cartographie`

For this first public version, the API ships a few factual tables that were generated from the database files of a World of Warcraft 3.3.5a client (French and English zone and sub-zone names, talent trees, recipe and enchantment lists, region grids): identifiers, names and coordinates, of the same kind as the `*_dbc` and `locales_*` tables that AzerothCore publishes. They contain no image, model, sound or client file. Later versions are planned to build them on your computer from your own client, like the server data.

## 6 quater. Illustrations of the app and of the launcher

The illustrations of the app (screen headers, workshops, settlements, race portraits) and of the launcher banner are fan art set in the Warcraft universe, generated for Guildmaster with an image generator (ChatGPT). They are not Blizzard artwork and contain no Blizzard image. Each one was reviewed before publication and is listed with its origin in the publication records of the project.

## 7. Trademarks

World of Warcraft, Warcraft and Blizzard Entertainment are trademarks or registered trademarks of Blizzard Entertainment, Inc. Guildmaster is not affiliated with, endorsed or sponsored by Blizzard Entertainment and includes no World of Warcraft client files.
