# Problèmes connus

[English version](KNOWN-ISSUES.md) · [Retour au README](README.fr.md)

Guildmaster 0.6.0-alpha.3. Les défauts et limites que nous connaissons dans cette version. Si vous rencontrez autre chose, signalez-le
dans le forum des bugs du [Discord](https://discord.gg/tGQMVByaH7) (le bouton « Signaler un bug » du lanceur prépare le rapport) ou
ouvrez un [ticket](https://github.com/Victor-Hanon/guildmaster/issues).

## Installation et lanceur

- **Windows seulement.** Windows 10 ou 11, 64 bits (essayé sur Windows 11). Pas de version pour Mac ni pour Linux.
- **Client anglais pas encore testé.** La 0.6.0-alpha.3 est testée avec le client français (frFR) ; le client anglais (enUS) est
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
- **Un de vos personnages dans une autre implantation.** Depuis la 0.5.1, un de vos personnages appartient à l'implantation dont la
  taverne garde sa pierre de foyer, et « S'installer ici », sur sa fiche dans l'appli, le rattache à l'implantation dont il occupe la
  taverne. Si l'appli l'affiche encore « loin de son implantation », elle dit pourquoi ; sinon, ramenez-le à la taverne de sa propre
  implantation et déconnectez-le là.

## Mort, résurrection et donjons

- **Un mort qui se reconnecte revient en fantôme.** En hardcore, un membre tombé attend 10 minutes qu'un membre de son groupe le
  relève. S'il est déconnecté pendant l'attente (ou si le monde redémarre), il revient en fantôme, que les autres aventuriers ne
  relèvent pas : sa mort devient définitive au bout des 10 minutes.
- **Renaissance du druide en recharge.** Un druide du groupe dont la Renaissance est en recharge compte encore comme un soigneur
  capable de relever : la mort ne devient définitive qu'à la fin des 10 minutes, et non tout de suite.
- **« Libérer l'esprit » n'est pas refusé** pour un membre à terre.
- **Un seul donjon pour les expéditions** : le Gouffre de Ragefeu. Un donjon fini en menant vous-même le groupe ne compte pas pour la
  campagne : l'étape est validée par la victoire d'une expédition lancée depuis l'appli.
- **Un danger vu ne s'oublie pas.** Un carré où une escouade s'est repliée devant un danger reste marqué « danger » sur la carte et
  n'est plus proposé aux missions. Depuis la 0.6.0-alpha.3, seules les créatures hostiles déclenchent le repli (plus les gardes
  neutres, comme à Cabestan).

## La nouvelle appli

- **La nouvelle interface** (accueil, fiches, carte, Mémorial, Artisanat, Gestion, coffre et intendance) a été éprouvée sur les
  mondes de développement. Dites-nous ce qui cloche.

## Pas encore disponible

D'autres donjons que le Gouffre de Ragefeu, tournées en escouade, le bateau sans vous. Voir la [feuille de route](ROADMAP.md).
