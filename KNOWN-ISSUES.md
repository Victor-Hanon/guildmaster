# Known issues

[Version française](KNOWN-ISSUES.fr.md) · [Back to the README](README.md)

Guildmaster 0.6.0-alpha.15. Defects and limitations we know of in this version. If you hit something that is not listed, please
report it in the bug forum of the [Discord](https://discord.gg/tGQMVByaH7) (the launcher's "Report a bug" button prepares the
report) or open an [issue](https://github.com/Victor-Hanon/guildmaster/issues).

## Installation and launcher

- **Windows only.** 64-bit Windows 10 or 11 (tried on Windows 11). No Mac or Linux version.
- **English client not tested yet.** 0.6.0-alpha.15 is tested with the French client (frFR); the English client (enUS) is planned
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

## Creating a new world, adventurers stuck in combat mode (0.6.0-alpha.15)

- **Creating a new world.** In 0.6.0-alpha.14, creating a new world stopped at the *Founding site* step: the launcher waited for the guild representative, who only comes with the guild, and the guild is founded at your first login. The launcher now waits for the HQ to be open and the guild chest to be placed, and requires the representative only once the guild exists. 0.6.0-alpha.6 created new worlds normally; judging by the code, the defect goes back to 0.6.0-alpha.8. A world created with an earlier version and then updated does not go through this step again. Proven in a test world on 8 November: a new installation of 0.6.0-alpha.15 created its world to the end, and the guild representative was in place once the guild was founded.
- **Adventurers stuck in combat mode.** An adventurer could stay in combat mode without fighting, standing still in a fighting stance far from any creature, and never come out of it. Outside dungeons and groups, an adventurer that stays 30 seconds in combat mode without being in combat, without moving and without casting now goes back out of combat, and a COMBAT_IDLE line in the server log Playerbots.log names the target it was keeping, its distance and the path to it (at most once every 10 minutes per adventurer). A first version of this safety net, without the path in the log line, ran for 16 minutes in a test world on 8 November with no regression and no false trigger; the defect did not occur there, so the safety net has not yet been seen at work on a real case. If your adventurers stay stuck anyway, *Report a bug* includes this log.

## Dungeon loops, groups left by a run, crash reports (0.6.0-alpha.14)

- **Dungeon loops.** When you send a group to a dungeon, you can now choose how many times: once, three times, a number of your choice, or endlessly. Between two runs, the group goes back to the guild vault, deposits its loot, repairs and takes its kit again. The loop waits for a missing member or an incomplete kit, and stops on a permanent death, a member above the dungeon's maximum level, two failed runs in a row, or when you choose *Stop after this run*. If the world restarts during a loop, the loop ends and does not resume. A two-run loop of Ragefire Chasm was proven in a test world with 0.6.0-alpha.14 on the night of 7 to 8 November: one run won, the stop at the vault, one run lost, the last stop of the survivors, then the end of the loop. After the last run, the loop waits up to 15 minutes for a dead member to come back to the vault, then ends. *Stop after this run* has not been tried in a test world yet.
- **Two failed runs in a row.** The number of failed runs in a row that stops a loop (two) is provisional.
- **Gold and vendor value.** The summary of a run and of a loop now gives the gold looted, the items that matter (green and better) and the vendor value of the grey and white items. A run made with an earlier version shows its gold as not recorded. Proven in a test world with 0.6.0-alpha.14 on the night of 7 to 8 November.
- **A group left behind by a run.** When a run ended while its leader was no longer in the world (for example after a permanent death), the other members stayed grouped and the next run could not form. The group is now disbanded even without its leader, and a dungeon finder group of your adventurers left with no run is disbanded within about a minute. Proven by automated tests only: a test world gives no way to remove an adventurer in the middle of a run. In a test world, such a group did not survive a restart of the world: on logging back in, the adventurers of a group without its leader left it on their own. If one of your adventurers stays "already in a group", restarting the world should therefore break up that group.
- **Sending a squad to a dungeon.** On a squad's card (Squads tab), *Send to a dungeon* opens the dungeon screen with the five places filled by its members. A missing place stays empty and the screen says so; a member busy elsewhere is shown as such and blocks the departure while it is. Checked by automated tests only, not yet in a game.
- **Crash reports in "Report a bug".** *Report a bug* in the launcher now adds the last three crash reports of the server (call stacks and registers only, never the values held in memory, never memory dumps) and the errors Windows recorded over the last 14 days for Guildmaster's programs, with a few signals from the PC (memory, disk, power). Reading them can add up to 30 seconds. Checked by automated tests and tried on one PC.

## Two dungeon runs, the HQ for your characters, ammunition, guild chest tabs (0.6.0-alpha.13)

- **Two dungeon runs at the same time.** Two dungeon runs can now go at once in the world, each group in its own instance, and a member can only be in one run. A third order waits its turn. Two runs of Ragefire Chasm at once, and a third order waiting, were proven in a test world with 0.6.0-alpha.13 on 7 November. The cap of two runs applies to the whole world, all guilds together. Four runs at once, for two guilds, held in a test world of 0.6.0-alpha.14 on 8 November, with a test setting the game does not offer.
- **Dungeons tab.** The app has a Dungeons tab (runs in progress, waiting and finished, loot per member, resurrections) and role icons. It was checked by automated tests and screenshots, not yet in a game.
- **Your characters at the general HQ of Orgrimmar.** One of your characters now enters the general HQ through a hearthstone bound there, or through "Settle here" when logged out within 10 yards of the waiting point. It takes one of the 5 places, shared with the recruits, and no outing leaves from the HQ for it, even when it is played by the AI. After "Settle here", Management can still show "On the way". Proven in a test world on 7 November: entry through the hearthstone, "Settle here", and an outing from the HQ refused.
- **Hunters' ammunition.** Below 1000 arrows or bullets, a hunter is topped up to 1000, now also in a group and so in dungeons, out of combat, at most every 30 seconds. One of your own characters played by the AI in a group is not covered. Proven in a test world on 7 November, during a dungeon run.
- **Handed back where it stands.** When you log in to one of your characters played by the AI and the AI cannot bring it back (inside an instance, on another continent), it is handed back to you where it stands, out of combat. The app then says "Handed back where it stood: log in to take it back." A far teleport of the group (dungeon finder) is no longer taken for an absence. Proven in a test world on 7 November, at world start and after a refused login.
- **Guild chest tabs are yours to set.** For each tab of the guild chest, you choose what it receives (crafting materials, consumables, equipment, recipes, tools, bags, quest items, miscellaneous). Tab 1 stays the default. A deposit goes to the tab of its category, then to another tab with room, instead of stopping when a tab is full, and crafting, missions and enchanting now read every tab: crafting can use materials from any tab. Without a setting, nothing moves. Proven in a test world on 7 November: setting a tab, sorting, a deposit that overflows when tab 1 is full, crafting with materials taken outside tab 1.

## Fixes, farm clarity and trade tools (0.6.0-alpha.12)

- **Brill to the Sepulcher transfer works again.** The Brill zeppelin no longer blocks a trip on the same map; Auberdine stays refused, and the refusal now names the real transport (boat or zeppelin). The way out was proven in a test world; the way back from the Sepulcher to Brill reached the tavern in the test but is not counted as proven.
- **A refused mission names the tier.** A refusal for an insufficient tier now carries the tier asked, your reputation and the gap.
- **A player character at an outpost is shown there everywhere.** The list, the sheet, "Settle here" and the place count agree.
- **Where, Farm and the report.** "Where" is named or hidden, the ledger has a Farm category, the FARM step is shown, a return through a forbidden square is said in the report (the return is never refused), and a solo shows its list of squares. The nature of each figure (recorded, estimated) is shown.
- **Tirisfal section t043 is now used.** A new migration (0066) marks the north-west Deathknell section as proven: 22 sections are used instead of 21. It was walked in both directions in a test world.
- **Small display fixes.** The Home reward is folded, filter chips wrap at 360 px width instead of being cut, and the missions test was brought up to date.
- **Trade tools are bought by the guild.** When a craftsman lacks a tool a recipe needs and the tool can be bought, the guild buys it once with its bank gold and keeps it in the chest; the API no longer answers "tool missing" for such a tool. This was proven by one test in a test world only, with one recipe.
- **Not seen for real.** The red alert and the loss screen of the new interface were checked by automated tests and screenshots only, never in a game. "New RPG" draws (D-018) were not observed in a test world: they are proven by automated tests only.

## New interface and guild tools (0.6.0-alpha.11)

- **The app has a new interface, built to need fewer taps.** Every screen lights its tab; Settings and Help are new; the Home screen keeps only what needs you now; Guild has three parts (Members, Squads, Recruits) and the old Commander screen is inside Squads; sending a squad out is one summary page (from 11 taps to 5); a member's card shows its actions under its name. Every function of the previous app is still reachable. The new screens were checked by automated tests and screenshots at phone width, not yet by players: tell us if something is hard to find.
- **A squad with an unresolved loss cannot leave without your explicit order.** From any button (Home, Squads, a report, "Again"), sending such a squad stays disabled until you tick "order after a loss". Members of that squad sent alone are not blocked yet.
- **Guild ledger statement.** The ledger now lists paid recruitments (also those that failed on the way), training, repairs, craftsmen's hiring price and gold paid in by members, with totals per category and per day. A line whose amount was never recorded says so; nothing is estimated. The price of a gathering tool bought at training is not recorded by the game yet.
- **Guild events feed.** Deaths, returns, levels, new recruits, healers and hunters seen in the wild pool, missions ready or paid, orders finished or refused. Zone names in it are in French only.
- **Hardcore: 40-yard margin around forbidden squares.** In a hardcore world, hunting targets and off-road legs keep 40 yards from a forbidden square, and the check warns when a farm zone touches one. This margin was not yet tested in a game world; a farm too close to a forbidden square is warned about, not refused.
- **Gathering rounds stay on your allowed squares.** A round only works on the squares you allowed; walks between two spots can still cross other squares, and the check names them.
- **A locked people cannot be recruited.** While the campaign reward of a people is not earned, new members of that people cannot be recruited; members already in the guild stay. This was checked by automated tests only.
- **Small bags.** Before a farm or a hunt, the check warns when a member has fewer than 24 bag slots: the squad will come back early, bags full.

## Roads of Tirisfal, forbidden squares, deaths on the way and the map (0.6.0-alpha.10)

- **The roads of Tirisfal Glades are now followed, but only the part walked in a test is used.** Undead recruits now follow the roads of Tirisfal Glades to Brill, as Orc recruits follow the roads of Durotar. The network has 45 sections (about 9,170 yards); 21 of them (about 6,230 yards) were walked in both directions in a test world and are the only ones used. The other 24 are not used yet. In the night test, two wild recruits placed in Tirisfal Glades walked to Brill by the roads and both arrived (in 100 and 272 seconds), without a death.
- **A recruit can still die on the way, mostly before reaching a road.** Recruits that start inside a camp of hostile creatures, or that must cross one to reach the first road section (a camp near the entrance of one section in the west of the Glades is known), can still be killed. On the road itself no death was seen in the test, which was small (two recruits).
- **Places far from the proven roads stay refused.** In Durotar and in Tirisfal Glades, a trip that starts or ends in the same region more than 650 yards from the proven roads is still refused: the member stays where it is and the plan ends "no route" (trajet-impossible). The Echo Isles in Durotar are such a place. Both ways were seen in a test world: the plan from the tavern to the isles, and the return from the isles, ended "no route" and the member stayed where it was.
- **Trips between a road region and the rest of the world.** A trip that leaves Tirisfal Glades (for example from Brill to the Sepulcher in Silverpine Forest), or comes back, now takes the road as far as it serves and walks the rest as before, instead of being refused. The same applies to Durotar. Proven in a test world on the way out, from Brill to the Sepulcher; the way back reached Brill by the same road but is not proven.
- **New RPG draws.** The automatic choice of a hunting or camp spot made by the bots is now dropped when the route refuses it, without ending the plan, and it is no longer made during the outward leg, the deposit and the return of a plan in a region with roads. Not seen in a test world: the test bot (level 60) made no such draw, so this is proven by automated tests only.
- **The trips of a plan avoid the squares you forbid.** The squares you forbid in a region are now passed to the game with each farm or exploration plan. The way into and out of the road network is chosen so that the walk off the roads does not cross a forbidden square; if no way exists, the outward trip is refused before departure (the plan is rejected with "the way to this zone crosses a forbidden square") and the member stays at the tavern. The way back is never refused: it goes as before, with an alert in the game log. Seen in a test world: with two forbidden squares placed on the usual outward path, the member took another way in and out of the roads, never entered those squares and reached its work; with the avoidance switched off, the same squares were crossed as before. A plan refused for "forbidden square", and the writing of the squares by the application itself, were not seen in the test world: they are proven by automated tests only.
- **What the guard on forbidden squares does not cover.** The roads themselves are not judged (a proven road that crosses a forbidden square is followed); free walking between two squares of the plan while it works avoids a forbidden square if it can but never refuses; a square forbidden after a plan has left does not apply to that plan; a margin of 20 yards around a forbidden square counts as crossing it. The check before departure only warns when the straight line from the tavern to the first target square crosses a forbidden square; it never refuses. Before this version the forbidden squares were not passed to the game at all, and an outward trip could cross one.
- **A recruit that dies on the way now appears in the Memorial.** In 0.6.0-alpha.9, two recruits that died on the way left no trace: they were missing from the Memorial, their sheet still said alive and their order gave no hint. Now the order says "died on the way", the adventurer sheet says dead, and the guild logs go back to the date asked for. Proven by automated tests only: no recruit died on the way during the test.
- **The map hatches the unexplored.** Squares of a region you have not explored are now hatched, and the legend says "Hatched: unexplored", instead of one large grey void. The sea inside an unexplored region is still shown under the grey veil, not as water: painting it would reveal the coast before you have explored it. This is a design choice that may change; a mock-up is waiting for a decision.
- **One road section is not proven.** The section at the north-west end of Deathknell (about 290 yards, a slope of 41 %) is not yet used. It was walked in both directions in a test (no blocked passage) but is still not used.

## Outing kits, plan squares and cooldown (0.6.0-alpha.9)

- **Potion sharing is proven in a test world only.** Before an outing and when the squad comes back, the potions in the guild chest are shared in the group: the next one goes to the member with the fewest, ties broken in the order tank (otherwise the squad leader), healer, damage dealers. Mana potions keep the setting of your guild. This was proven with squads of three in a test world, not yet in a game installed by the public installer.
- **"Prepare, then depart" is now on.** Before an outing, a member short of potions (or with fewer than 8 free bag slots) first goes to the chest of their site, a few seconds each, one at a time. This never blocks a departure, and a member can still leave without potions: the app only shows that line in the warning colour.
- **The 2-hour cooldown on repeatable contracts is provisional.** A repeatable regional contract that you delivered can be taken again two hours after its last delivery. The duration is a first guess and may change. Giving a contract up sets no cooldown. Proven by automated tests, not yet in a running world.
- **Brill, the outpost offered by the campaign.** It is now installed once the Undead are unlocked (before, the order was refused and Brill never came). Proven by automated tests, not yet in a running world.
- **Some warnings can be out of date.** "Far from the HQ" and "bags almost full" read the last saved sheet of the member. Right after a preparation, an outdated sheet can still block a departure with "no bag space" for a few minutes.
- **Squads can still stray or hunt slowly.** On the way back, a free movement point can fall outside the squares of the plan. Gathering only applies the squares you forbid, not the list of allowed ones. In one observation, a squad of two hunted about ten times slower than one member alone in the same squares; the cause is not known.

## Several guilds in one world (0.6.0-alpha.8)

- **A guild is added from the command line only.** `gm.mjs ajouter-guilde` (world stopped, backed up first) adds a guild led by a technical guild master who never logs in; the launcher has no button for it yet. The added guild has its own app and API, on the same PC.
- **One dungeon run at a time in the world.** A second guild's expedition waits for the current run to end. Crafting and steward orders are also served one at a time for the whole world.
- **Same faction and same death mode for every guild of a world.** No trading or grouping between guilds yet.
- **Not yet proven in a game installed by the public installer with two players.**

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
