# Guildmaster

[English version](README.md)

**Gérez votre guilde de partout. Rejoignez-la en Azeroth quand vous rentrez.**

### [Découvrir le jeu sur le site : guildmaster-game.pages.dev](https://guildmaster-game.pages.dev/?lang=fr)

**[⬇ Télécharger l'installeur (Windows, 197 Mo)](https://github.com/Victor-Hanon/guildmaster/releases/download/v0.5.1-alpha.1/Guildmaster-Setup-0.5.1-alpha.1.exe)** · **[Site](https://guildmaster-game.pages.dev/?lang=fr)** · **[Discord](https://discord.gg/tGQMVByaH7)** · **[Soutenir sur Ko-fi](https://ko-fi.com/ragolk)**

Guildmaster fait vivre, sur votre ordinateur, un monde World of Warcraft 3.3.5a hors ligne peuplé d'aventuriers autonomes. Ils
naissent, progressent et meurent ; vous les recrutez dans votre guilde, vous les envoyez explorer, récolter et chasser depuis l'appli
Guildmaster (sur votre PC ou votre téléphone), et vous vous connectez au jeu quand vous voulez combattre à leurs côtés.

Gratuit. Un monde par joueur, sur son propre PC. Aucun serveur en ligne, aucun compte Guildmaster.

> Guildmaster est un projet de fans non officiel. Il n'est ni affilié à Blizzard Entertainment, ni approuvé par elle.
> Un client World of Warcraft 3.3.5a que vous possédez est nécessaire ; il n'est pas fourni.

## Télécharger

Dernière version : page [Releases](https://github.com/Victor-Hanon/guildmaster/releases). Téléchargez `Guildmaster-Setup-<version>.exe` et vérifiez son SHA-256
(fichier `.sha256` à côté, ou commande `certutil -hashfile Guildmaster-Setup-<version>.exe SHA256`).

Windows peut afficher « Windows a protégé votre ordinateur » : l'installeur n'est pas encore signé. Cliquez sur « Informations
complémentaires » puis « Exécuter quand même », après avoir vérifié la somme.

## Prérequis

| | |
|---|---|
| Système | Windows 10 ou 11, 64 bits (essayé sur Windows 11). |
| Client du jeu | World of Warcraft 3.3.5a (build 12340), en français (frFR) ou en anglais (enUS), que vous possédez (testé avec le client français ; client anglais pas encore testé). Guildmaster lit ses fichiers sur votre PC pour préparer les données du serveur et les icônes ; il ne le modifie pas, à part le fichier `realmlist.wtf` (remis à l'origine sur demande) et les addons Guildmaster dans `Interface\AddOns`. |
| Espace disque | Prévoyez environ 10 Go libres : programme environ 0,4 Go, données du monde après sa création environ 8,4 Go, plus la place de vos sauvegardes. |
| Mémoire | 16 Go conseillés, dont environ 6 Go libres au premier démarrage ; en jeu, le serveur utilise environ 5 Go. |
| Internet | Pour télécharger l'installeur et les mises à jour. Le monde tourne ensuite hors ligne. |

## Installer et jouer

1. Lancez l'installeur, choisissez le dossier d'installation.
2. Dans le lanceur, indiquez le dossier de votre client WoW 3.3.5a.
3. Créez votre monde : faction, peuple, nom de la guilde, mode de mort (normal ou hardcore).
4. Attendez la création du monde, la première fois seulement : de 25 à 50 minutes environ selon le PC. Guildmaster prépare les
   cartes, les décors et les chemins des créatures à partir de votre propre client. Les démarrages suivants prennent environ 1 minute.
5. Cliquez sur JOUER, ou ouvrez l'appli Guildmaster.

Problèmes connus : [KNOWN-ISSUES.fr.md](KNOWN-ISSUES.fr.md). La suite : [ROADMAP.md](ROADMAP.md).

## Mises à jour

Le lanceur vous propose les nouvelles versions ; vous pouvez refuser et continuer sur la vôtre. Avant une mise à jour, votre monde
est sauvegardé ; il est restauré automatiquement si quelque chose échoue.

## Source

- Le serveur de jeu (AzerothCore, mod-playerbots modifié par Guildmaster, mod-wowquarium) est distribué sous GNU GPL v2 ou ultérieure
  et GNU AGPL v3 ou ultérieure. Sa source complète, aux révisions exactes de chaque version, est jointe à chaque release
  (`Guildmaster-<version>-server-source.tar.gz`).
- Le code propre de Guildmaster (API, appli, lanceur, installeur, outils du runtime) est distribué sous GNU AGPL v3 ou ultérieure
  ([LICENSE](LICENSE)) ; les addons en jeu sous licence MIT. Sa source, à la révision exacte de chaque version, est elle aussi jointe
  à chaque release (`Guildmaster-<version>-source.tar.gz`).
- Détail des composants et de leurs licences : [THIRD-PARTY-NOTICES.md](THIRD-PARTY-NOTICES.md) ; remerciements :
  [CREDITS.md](CREDITS.md).

## Avertissements

Alpha : des défauts sont attendus, faites des sauvegardes. En mode hardcore, la mort est définitive, pour les aventuriers comme pour
vos personnages. Lire [AVERTISSEMENT.fr.md](AVERTISSEMENT.fr.md).

## Contact

Discord : https://discord.gg/tGQMVByaH7 · Site : https://guildmaster-game.pages.dev · Signaler un défaut : [Issues](https://github.com/Victor-Hanon/guildmaster/issues).

World of Warcraft, Warcraft et Blizzard Entertainment sont des marques ou des marques déposées de Blizzard Entertainment, Inc.
