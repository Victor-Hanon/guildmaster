# Problèmes connus

[English version](KNOWN-ISSUES.md) · [Retour au README](README.fr.md)

Guildmaster 0.5.0-alpha.1. Les défauts et limites que nous connaissons dans cette version. Si vous rencontrez autre chose, signalez-le
dans le forum des bugs du [Discord](https://discord.gg/tGQMVByaH7) (le bouton « Signaler un bug » du lanceur prépare le rapport) ou
ouvrez un [ticket](https://github.com/Victor-Hanon/guildmaster/issues).

## Installation et lanceur

- **Windows seulement.** Windows 10 ou 11, 64 bits (essayé sur Windows 11). Pas de version pour Mac ni pour Linux.
- **Client anglais pas encore testé.** La 0.5.0-alpha.1 est testée avec le client français (frFR) ; le client anglais (enUS) est
  prévu mais n'a pas été essayé.
- **Première création du monde longue** : de 25 à 50 minutes environ selon le PC, une seule fois ; les démarrages suivants prennent
  environ 1 minute. Laissez le PC allumé, hors veille. Prévoyez environ 10 Go libres et 16 Go de mémoire, dont environ 6 Go libres
  au premier démarrage : fermez les programmes lourds avant de lancer la création.
- **Installeur non signé.** Windows peut afficher « Windows a protégé votre ordinateur » : cliquez sur « Informations
  complémentaires » puis « Exécuter quand même », seulement après avoir vérifié l'empreinte SHA-256 publiée avec la release.
- **Pas encore de bouton de restauration.** Le lanceur sauvegarde votre monde, mais vous ne pouvez pas encore restaurer une
  sauvegarde vous-même depuis le lanceur.

## En jeu

- **« Sur moi »** ne fonctionne qu'en donjon à cinq ; ni en raid, ni en champ de bataille, ni en arène.
- **Un de vos personnages emmené dans une autre implantation n'est pas joué par l'IA.** Si vous déconnectez un personnage dans la
  taverne d'une autre implantation de votre guilde, l'appli l'affiche « loin de son implantation » et l'IA ne le reprend pas. En
  attendant un correctif : ramenez-le à la taverne de sa propre implantation et déconnectez-le là.

## Pas encore disponible

Donjons autonomes, tournées en escouade, le bateau sans vous. Voir la [feuille de route](ROADMAP.md).
