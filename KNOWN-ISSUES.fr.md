# Problèmes connus

[English version](KNOWN-ISSUES.md) · [Retour au README](README.fr.md)

Guildmaster 0.6.0-alpha.15. Les défauts et limites que nous connaissons dans cette version. Si vous rencontrez autre chose, signalez-le
dans le forum des bugs du [Discord](https://discord.gg/tGQMVByaH7) (le bouton « Signaler un bug » du lanceur prépare le rapport) ou
ouvrez un [ticket](https://github.com/Victor-Hanon/guildmaster/issues).

## Installation et lanceur

- **Windows seulement.** Windows 10 ou 11, 64 bits (essayé sur Windows 11). Pas de version pour Mac ni pour Linux.
- **Client anglais pas encore testé.** La 0.6.0-alpha.15 est testée avec le client français (frFR) ; le client anglais (enUS) est
  prévu mais n'a pas été essayé.
- **Première création du monde longue** : de 25 à 50 minutes environ selon le PC, plus d'une heure sur un PC plus lent, une seule
  fois ; les démarrages suivants prennent environ 1 minute (jusqu'à 10 minutes environ sur un PC plus lent). Ne fermez pas le
  lanceur pendant la création. Laissez le PC allumé, hors veille. Prévoyez environ 10 Go libres et 16 Go de mémoire, dont environ 6 Go libres
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

## Escouades

- **Un chef d'escouade peut attendre sans fin** un membre resté en arrière. Pendant une tournée de collecte en escouade, le suivi de
  la tournée dit qui il attend.

## Mort, résurrection et donjons

- **Un mort qui se reconnecte revient en fantôme.** En hardcore, un membre tombé attend 10 minutes qu'un membre de son groupe le
  relève. S'il est déconnecté pendant l'attente (ou si le monde redémarre), il revient en fantôme, que les autres aventuriers ne
  relèvent pas : sa mort devient définitive au bout des 10 minutes.
- **Renaissance du druide en recharge.** Un druide du groupe dont la Renaissance est en recharge compte encore comme un soigneur
  capable de relever : la mort ne devient définitive qu'à la fin des 10 minutes, et non tout de suite.
- **« Libérer l'esprit » n'est pas refusé** pour un membre à terre.
- **Un seul donjon pour les expéditions** : le Gouffre de Ragefeu. Pour tous les donjons de la campagne, Gouffre compris, l'étape
  compte quand votre guilde a abattu tous les chefs du donjon, en expédition lancée depuis l'appli ou en groupe mené par vous ; les
  chefs déjà abattus par votre guilde comptent.
- **Niveau du groupe pas encore vérifié en donjon.** Les chefs peuvent tomber en plusieurs passages, et un groupe au-dessus du niveau
  du donjon le valide aussi. Une prochaine version demandera tous les chefs dans le même passage, sans personne au-dessus du niveau
  maximum de la recherche de donjon (21 pour le Gouffre).
- **Un danger vu ne s'oublie pas.** Un carré où une escouade s'est repliée devant un danger reste marqué « danger » sur la carte et
  n'est plus proposé aux missions. Depuis la 0.6.0-alpha.3, seules les créatures hostiles déclenchent le repli (plus les gardes
  neutres, comme à Cabestan).

## Création d'un monde neuf, aventuriers figés en mode combat (0.6.0-alpha.15)

- **Création d'un monde neuf.** En 0.6.0-alpha.14, la création d'un monde neuf s'arrêtait à l'étape « Implantation fondatrice » : le lanceur attendait le représentant de la guilde, qui n'arrive qu'avec la guilde, et la guilde n'est fondée qu'à votre première connexion. Le lanceur attend maintenant que le QG soit ouvert et le coffre de guilde posé, et n'exige le représentant qu'une fois la guilde fondée. La 0.6.0-alpha.6 créait un monde neuf normalement ; d'après le code, le défaut remonte à la 0.6.0-alpha.8. Un monde créé avec une version précédente puis mis à jour ne repasse pas par cette étape. Éprouvé dans un monde d'essai le 8 novembre : une installation neuve de la 0.6.0-alpha.15 a créé son monde jusqu'au bout, et le représentant de la guilde était en place une fois la guilde fondée.
- **Aventuriers figés en mode combat.** Un aventurier pouvait rester en mode combat sans combattre, immobile en position de combat loin de toute créature, sans jamais en sortir. Hors donjon et hors groupe, un aventurier qui reste 30 secondes en mode combat sans être en combat, sans bouger et sans lancer de sort repasse maintenant hors combat, et une ligne COMBAT_IDLE du journal du serveur Playerbots.log nomme la cible qu'il gardait, sa distance et le chemin vers elle (au plus une fois toutes les 10 minutes par aventurier). Une première version de ce filet, sans le chemin dans la ligne du journal, a tourné 16 minutes dans un monde d'essai le 8 novembre, sans régression ni déclenchement à tort ; le défaut ne s'y est pas produit, et le filet n'a donc encore jamais été vu à l'œuvre sur un vrai cas. Si vos aventuriers restent figés malgré tout, « Signaler un bug » joint ce journal.

## Boucles de donjon, groupes laissés par une course, rapports de plantage (0.6.0-alpha.14)

- **Boucles de donjon.** Quand vous envoyez un groupe dans un donjon, vous choisissez maintenant combien de fois : une fois, trois fois, le nombre de votre choix ou à l'infini. Entre deux tours, le groupe rentre au coffre de guilde, dépose son butin, se répare et reprend son kit. La boucle attend un membre absent ou un kit incomplet, et s'arrête sur une mort définitive, un membre au-delà du niveau maximal du donjon, deux courses ratées de suite, ou quand vous choisissez « Arrêter après ce tour ». Si le monde redémarre pendant une boucle, la boucle s'arrête et ne reprend pas. Une boucle de deux tours du Gouffre de Ragefeu a été éprouvée dans un monde d'essai avec la 0.6.0-alpha.14, dans la nuit du 7 au 8 novembre : un tour gagné, le passage au coffre, un tour perdu, le dernier passage des survivants, puis la fin de la boucle. Après le dernier tour, la boucle attend jusqu'à 15 minutes qu'un membre mort revienne au coffre, puis se termine. « Arrêter après ce tour » n'a pas encore été essayé dans un monde d'essai.
- **Deux courses ratées de suite.** Le nombre de courses ratées de suite qui arrête une boucle (deux) est provisoire.
- **Or et valeur de vente.** Le résumé d'une course et d'une boucle donne maintenant l'or ramassé, les objets qui comptent (verts et mieux) et la valeur de vente des objets gris et blancs. Une course faite avec une version précédente montre son or comme non relevé. Éprouvé dans un monde d'essai avec la 0.6.0-alpha.14, dans la nuit du 7 au 8 novembre.
- **Un groupe laissé par une course.** Quand une course finissait alors que son chef n'était plus dans le monde (par exemple après une mort définitive), les autres membres restaient groupés et la course suivante ne pouvait pas se former. Le groupe est maintenant dissous même sans son chef, et un groupe de recherche de donjon de vos aventuriers resté sans course est dissous en une minute environ. Éprouvé par des tests automatiques seulement : un monde d'essai ne permet pas de retirer un aventurier en pleine course. Dans un monde d'essai, un tel groupe n'a pas survécu à un redémarrage du monde : à la reconnexion, les aventuriers d'un groupe sans son chef l'ont quitté d'eux-mêmes. Si l'un de vos aventuriers reste « déjà dans un groupe », redémarrer le monde devrait donc défaire ce groupe.
- **Envoyer une escouade en donjon.** Sur la carte d'une escouade (onglet Escouades), « Envoyer en donjon » ouvre l'écran du donjon avec les cinq places remplies par ses membres. Une place qui manque reste vide et l'écran le dit ; un membre occupé ailleurs est montré comme tel et bloque l'envoi tant qu'il l'est. Vérifié par des tests automatiques seulement, pas encore en jeu.
- **Rapports de plantage dans « Signaler un bug ».** « Signaler un bug » dans le lanceur joint maintenant les trois derniers rapports de plantage du serveur (piles d'appels et registres seulement, jamais les valeurs en mémoire, jamais les copies de la mémoire) et les erreurs notées par Windows sur les 14 derniers jours pour les programmes de Guildmaster, avec quelques signaux du PC (mémoire, disque, alimentation). Leur lecture peut ajouter jusqu'à 30 secondes. Vérifié par des tests automatiques et essayé sur un PC.

## Deux courses de donjon, le QG pour vos personnages, munitions, onglets du coffre (0.6.0-alpha.13)

- **Deux courses de donjon en même temps.** Deux courses de donjon peuvent maintenant avoir lieu en même temps dans le monde, chaque groupe dans sa propre instance, et un membre ne peut être que dans une course. Un troisième ordre attend son tour. Deux courses du Gouffre de Ragefeu en même temps, et un troisième ordre qui attend, ont été éprouvés dans un monde d'essai avec la 0.6.0-alpha.13 le 7 novembre. Le plafond de deux courses vaut pour l'ensemble du monde, toutes guildes confondues. Quatre courses à la fois, pour deux guildes, ont tenu dans un monde d'essai de la 0.6.0-alpha.14 le 8 novembre, avec un réglage d'essai que le jeu ne propose pas.
- **Onglet Donjons.** L'appli a un onglet Donjons (courses en cours, en attente et finies, butin par membre, résurrections) et des icônes de rôle. Il a été vérifié par des tests automatiques et des captures, pas encore en jeu.
- **Vos personnages au QG général d'Orgrimmar.** Un de vos personnages entre maintenant au QG général par une pierre de foyer liée là, ou par « S'installer ici » quand il est déconnecté à 10 yards au plus du point d'attente. Il prend une des 5 places, partagées avec les recrues, et aucune sortie ne part du QG pour lui, même joué par l'IA. Après « S'installer ici », la Gestion peut encore dire « En route ». Éprouvé dans un monde d'essai le 7 novembre : entrée par la pierre de foyer, « S'installer ici », et refus d'une sortie depuis le QG.
- **Munitions des chasseurs.** Sous 1000 flèches ou balles, un chasseur est complété jusqu'à 1000, maintenant aussi en groupe et donc en donjon, hors combat, au plus toutes les 30 secondes. Un de vos personnages joué par l'IA dans un groupe n'est pas couvert. Éprouvé dans un monde d'essai le 7 novembre, en course de donjon.
- **Rendu là où il est.** Quand vous vous connectez à un de vos personnages joué par l'IA et que l'IA ne peut pas le ramener (dans une instance, sur un autre continent), il vous est rendu là où il est, hors combat. L'appli dit alors « Rendu là où il était : connectez-vous pour le reprendre. » Un téléport lointain du groupe (recherche de donjon) n'est plus pris pour une absence. Éprouvé dans un monde d'essai le 7 novembre, au démarrage du monde et après une connexion refusée.
- **Les onglets du coffre se règlent.** Pour chaque onglet du coffre de guilde, vous choisissez ce qu'il reçoit (matières d'artisanat, consommables, équipement, recettes, outils, sacs, objets de quête, divers). L'onglet 1 reste celui par défaut. Un dépôt va à l'onglet de sa catégorie, puis dans un autre onglet qui a de la place, au lieu de s'arrêter quand un onglet est plein, et l'artisanat, les missions et l'enchantement lisent maintenant tous les onglets : l'artisanat peut prendre des matières dans n'importe quel onglet. Sans réglage, rien ne bouge. Éprouvé dans un monde d'essai le 7 novembre : réglage d'un onglet, tri, dépôt qui déborde quand l'onglet 1 est plein, fabrication avec des matières prises hors de l'onglet 1.

## Corrections, farm lisible et outils de métier (0.6.0-alpha.12)

- **Le transfert de Brill au Sépulcre fonctionne de nouveau.** Le zeppelin de Brill ne bloque plus un trajet sur la même carte ; Auberdine reste refusée, et le refus nomme le vrai transport (bateau ou zeppelin). L'aller a été éprouvé dans un monde d'essai ; le retour du Sépulcre à Brill a atteint la taverne pendant l'essai mais n'est pas compté comme éprouvé.
- **Un refus de mission nomme le palier.** Un refus pour palier insuffisant joint maintenant le palier demandé, votre réputation et l'écart.
- **Un personnage du joueur installé à un avant-poste y est servi partout.** La liste, la fiche, « S'installer ici » et le décompte des places sont d'accord.
- **Où, Farm et compte rendu.** Le « Où » est nommé ou masqué, le Grand livre a une catégorie Farm, l'étape FARM est visible, un retour par un carré interdit est dit dans le compte rendu (le retour n'est jamais refusé), et un solo montre la liste de ses carrés. La nature de chaque chiffre (relevé, estimé) est indiquée.
- **Le tronçon t043 de Tirisfal sert maintenant.** Une nouvelle migration (0066) marque comme éprouvé le tronçon nord-ouest de Deathknell : 22 tronçons servent au lieu de 21. Il a été parcouru dans les deux sens dans un monde d'essai.
- **Petites corrections d'affichage.** La récompense de l'Accueil est repliée, les puces de filtres passent à la ligne à 360 px de large au lieu d'être coupées, et le test des missions est remis à jour.
- **Les outils de métier sont achetés par la guilde.** Quand un artisan n'a pas l'outil dont une recette a besoin et que cet outil s'achète, la guilde l'achète une fois avec l'or de sa banque et le garde au coffre ; l'API ne répond plus « outil absent » pour un tel outil. Éprouvé par un seul essai dans un monde d'essai, avec une seule recette.
- **Pas vu en vrai.** L'alerte rouge et l'écran de perte de la nouvelle interface n'ont été vérifiés que par des tests automatiques et des captures, jamais en jeu. Les tirages de « new rpg » (D-018) n'ont pas été observés dans un monde d'essai : ils ne sont éprouvés que par des tests automatiques.

## Nouvelle interface et outils de guilde (0.6.0-alpha.11)

- **L'appli a une nouvelle interface, pensée pour moins de touchers.** Chaque écran allume son onglet ; Réglages et Aide sont nouveaux ; l'Accueil ne garde que ce qui vous attend ; la Guilde a trois parties (Membres, Escouades, Recrues) et l'ancien écran Commandant est dans Escouades ; envoyer une escouade en sortie tient sur une page de résumé (de 11 touchers à 5) ; la fiche d'un membre montre ses actions sous son nom. Toutes les fonctions de l'appli d'avant restent accessibles. Les nouveaux écrans ont été vérifiés par des tests automatiques et des captures à la largeur d'un téléphone, pas encore par des joueurs : dites-nous si quelque chose est difficile à trouver.
- **Une escouade qui a subi une perte non tranchée ne part pas sans votre ordre explicite.** Depuis n'importe quel bouton (Accueil, Escouades, compte rendu, « Repartir »), l'envoi reste désactivé tant que vous n'avez pas coché « ordre après perte ». Les membres de cette escouade envoyés seuls ne sont pas encore bloqués.
- **Relevé de compte de la guilde.** Le grand livre montre maintenant les recrutements payés (y compris ceux qui ont échoué en route), les apprentissages, les réparations, le prix d'engagement des artisans et l'or versé par les membres, avec des totaux par catégorie et par jour. Une ligne dont le montant n'a jamais été enregistré le dit ; rien n'est estimé. Le prix d'un outil de récolte acheté à l'apprentissage n'est pas encore enregistré par le jeu.
- **Fil des événements de la guilde.** Morts, retours, niveaux, nouvelles recrues, soigneurs et chasseurs vus au vivier, missions prêtes ou payées, ordres finis ou refusés. Les noms de zone y sont en français seulement.
- **Hardcore : marge de 40 yards autour des carrés interdits.** Dans un monde hardcore, les cibles de chasse et les trajets hors route restent à 40 yards d'un carré interdit, et la vérification avertit quand une zone de farm en touche un. Cette marge n'a pas encore été éprouvée dans un monde de jeu ; un farm trop proche d'un carré interdit est signalé, pas refusé.
- **Les tournées de collecte restent sur vos carrés autorisés.** Une tournée ne travaille que sur les carrés que vous avez autorisés ; les marches entre deux emplacements peuvent encore traverser d'autres carrés, et la vérification les nomme.
- **Un peuple verrouillé ne se recrute pas.** Tant que la récompense de campagne d'un peuple n'est pas obtenue, ses nouveaux membres ne se recrutent pas ; les membres déjà dans la guilde restent. Éprouvé par des tests automatiques seulement.
- **Petits sacs.** Avant un farm ou une chasse, la vérification avertit quand un membre a moins de 24 cases de sacs : l'escouade rentrera tôt, sacs pleins.

## Routes de Tirisfal, carrés interdits, morts en chemin et carte (0.6.0-alpha.10)

- **Les routes des Clairières de Tirisfal sont maintenant suivies, mais seule la partie parcourue lors d'un essai sert.** Les recrues mortes-vivantes suivent maintenant les routes des Clairières de Tirisfal jusqu'à Brill, comme les recrues orques suivent celles du Durotar. Le réseau compte 45 tronçons (environ 9 170 yards) ; 21 d'entre eux (environ 6 230 yards) ont été parcourus dans les deux sens dans un monde d'essai et sont les seuls utilisés. Les 24 autres ne servent pas encore. Lors de l'essai de la nuit, deux recrues sauvages posées dans les Clairières de Tirisfal ont rejoint Brill par les routes et sont toutes deux arrivées (en 100 et 272 secondes), sans mort.
- **Une recrue peut encore mourir en chemin, surtout avant d'atteindre une route.** Les recrues qui partent d'un camp de créatures hostiles, ou qui doivent en traverser un pour atteindre le premier tronçon (un camp près de l'entrée d'un tronçon, à l'ouest des Clairières, est connu), peuvent encore être tuées. Sur la route elle-même, aucune mort n'a été vue pendant l'essai, qui était modeste (deux recrues).
- **Les lieux éloignés des routes éprouvées restent refusés.** Au Durotar comme dans les Clairières de Tirisfal, un trajet qui commence ou finit dans la même région à plus de 650 yards des routes éprouvées est toujours refusé : le membre reste où il est et le plan se termine « sans route » (trajet-impossible). Les îles de l'Écho, au Durotar, sont un tel lieu. Les deux sens ont été vus dans un monde d'essai : le plan de la taverne vers les îles, puis le retour depuis les îles, se sont terminés « sans route » et le membre est resté où il était.
- **Trajets entre une région à routes et le reste du monde.** Un trajet qui sort des Clairières de Tirisfal (par exemple de Brill au Sépulcre, dans la forêt des Pins argentés), ou qui y revient, prend maintenant la route aussi loin qu'elle sert, puis marche le reste comme avant, au lieu d'être refusé. Il en va de même pour le Durotar. Éprouvé dans un monde d'essai à l'aller, de Brill au Sépulcre ; le retour a rejoint Brill par la même route mais n'est pas éprouvé.
- **Tirages de « new rpg ».** Le choix automatique d'un point de chasse ou de camp par les bots est maintenant abandonné quand la route le refuse, sans mettre fin au plan, et il n'est plus fait pendant l'aller, le dépôt et le retour d'un plan dans une région à routes. Non observé dans un monde d'essai : le bot d'essai (niveau 60) n'a fait aucun tirage de ce genre ; ce comportement n'est éprouvé que par des tests automatiques.
- **Les trajets d'un plan évitent les carrés que vous interdisez.** Les carrés que vous interdisez dans une région sont maintenant transmis au jeu avec chaque plan de farm ou d'exploration. L'entrée et la sortie du réseau de routes sont choisies pour que la marche hors des routes ne traverse aucun carré interdit ; si aucun chemin n'existe, l'aller est refusé avant le départ (le plan est rejeté avec « le chemin vers cette zone traverse un carré interdit ») et le membre reste à la taverne. Le retour n'est jamais refusé : il se fait comme avant, avec une alerte dans le journal du jeu. Vu dans un monde d'essai : avec deux carrés interdits posés sur le chemin habituel de l'aller, le membre a pris une autre entrée et une autre sortie des routes, n'est jamais entré dans ces carrés et a atteint son travail ; avec l'évitement éteint, les mêmes carrés ont été traversés comme avant. Un plan refusé pour « carré interdit » et l'écriture des carrés par l'application elle-même n'ont pas été vus dans le monde d'essai : ils ne sont éprouvés que par des tests automatiques.
- **Ce que la garde des carrés interdits ne couvre pas.** Les routes elles-mêmes ne sont pas jugées (une route éprouvée qui traverse un carré interdit est suivie) ; la marche libre entre deux carrés du plan pendant son travail évite un carré interdit si elle le peut mais ne refuse jamais ; un carré interdit après le départ d'un plan ne s'applique pas à ce plan ; une marge de 20 yards autour d'un carré interdit compte comme une traversée. La vérification avant le départ avertit seulement quand la ligne droite de la taverne au premier carré visé traverse un carré interdit ; elle ne refuse jamais. Avant cette version, les carrés interdits n'étaient pas transmis du tout au jeu, et un aller pouvait en traverser un.
- **Une recrue morte en chemin figure maintenant au Mémorial.** Dans la 0.6.0-alpha.9, deux recrues mortes en chemin n'ont laissé aucune trace : absentes du Mémorial, leur fiche disait toujours « vivante » et leur ordre ne donnait aucun indice. Maintenant l'ordre dit « morte en route », la fiche de l'aventurier la dit morte, et les journaux de la guilde remontent jusqu'à la date demandée. Éprouvé par des tests automatiques seulement : aucune recrue n'est morte en route pendant l'essai.
- **La carte hachure l'inexploré.** Les carrés d'une région que vous n'avez pas explorés sont maintenant hachurés, et la légende dit « Hachuré : inexploré », au lieu d'un grand vide gris. La mer à l'intérieur d'une région inexplorée reste montrée sous le voile gris, pas en eau : la peindre révélerait la côte avant que vous l'ayez explorée. C'est un choix de conception qui peut changer ; une maquette attend une décision.
- **Un tronçon n'est pas éprouvé.** Le tronçon du nord-ouest de Deathknell (environ 290 yards, une pente de 41 %) ne sert pas encore. Il a été parcouru dans les deux sens lors d'un essai (sans blocage), mais ne sert pas encore.

## Kits de sortie, carrés du plan et recharge (0.6.0-alpha.9)

- **Le partage des potions n'est éprouvé que dans un monde d'essai.** Avant une sortie et au retour de l'escouade, les potions du coffre de guilde sont partagées dans le groupe : la suivante va au membre le moins pourvu, à égalité dans l'ordre tank (sinon le chef de l'escouade), soigneur, dps. Les potions de mana gardent le réglage de votre guilde. Cela a été éprouvé avec des escouades de trois dans un monde d'essai, pas encore dans une partie installée par l'installeur public.
- **« Préparer puis partir » est maintenant allumé.** Avant une sortie, un membre à qui il manque sa part de potions (ou qui a moins de 8 cases libres) passe d'abord au coffre de son implantation, quelques secondes chacun, un à la fois. Cela ne bloque jamais un départ, et un membre peut toujours partir sans potion : l'appli montre alors seulement la ligne en couleur d'alerte.
- **Le temps de recharge de 2 heures des contrats refaisables est provisoire.** Un contrat régional refaisable que vous avez livré ne se reprend que deux heures après sa dernière livraison. La durée est une première estimation et peut changer. Renoncer à un contrat ne pose aucune recharge. Éprouvé par des tests automatiques, pas encore dans un monde en marche.
- **Brill, l'avant-poste offert par la campagne.** Il s'installe maintenant une fois les Morts-vivants débloqués (avant, l'ordre était refusé et Brill n'arrivait jamais). Éprouvé par des tests automatiques, pas encore dans un monde en marche.
- **Certains avertissements peuvent être périmés.** « Loin du QG » et « sacs presque pleins » lisent la dernière fiche sauvegardée du membre. Juste après une préparation, une fiche périmée peut encore bloquer un départ avec « plus de place dans les sacs » pendant quelques minutes.
- **Les escouades peuvent encore s'écarter ou chasser lentement.** Au retour, un point de déplacement libre peut tomber hors des carrés du plan. La collecte n'applique que les carrés que vous interdisez, pas la liste des carrés autorisés. Dans un cas observé, une escouade de deux a chassé environ dix fois moins vite qu'un membre seul dans les mêmes carrés ; la cause n'est pas connue.

## Plusieurs guildes dans un monde (0.6.0-alpha.8)

- **Une guilde s'ajoute seulement en ligne de commande.** `gm.mjs ajouter-guilde` (monde arrêté, sauvegardé d'abord) ajoute une guilde menée par un chef de guilde technique qui ne se connecte jamais ; le lanceur n'a pas encore de bouton pour cela. La guilde ajoutée a sa propre appli et sa propre API, sur le même PC.
- **Une seule course de donjon à la fois dans le monde.** L'expédition d'une seconde guilde attend la fin de la course en cours. Les ordres d'artisanat et de l'Intendant sont aussi servis un par un pour tout le monde.
- **Même faction et même mode de mort pour toutes les guildes d'un monde.** Pas encore de commerce ni de groupe entre guildes.
- **Pas encore éprouvé dans une partie installée par l'installeur public avec deux joueurs.**

## Flotte (nouveau dans la 0.6.0-alpha.6)

- **Un seul navire et un seul port.** La flotte de cette version compte un navire, acheté au comptoir de Cabestan. Il part de
  Cabestan et y revient au bout d'une heure.
- **Matières brutes seulement.** Seules les matières brutes déposées au coffre de guilde embarquent (253 marchandises). Les outils,
  l'équipement et les objets de quête restent au coffre.

## La nouvelle appli

- **La nouvelle interface** (accueil, fiches, carte, Mémorial, Artisanat, Gestion, coffre et intendance) a été éprouvée sur les
  mondes de développement. Dites-nous ce qui cloche.
- **La flotte, la tournée de collecte en escouade et les nouveaux chapitres de la campagne orque** ont été éprouvés sur les mondes
  de développement, pas encore dans une partie installée par l'installeur public.

## Pas encore disponible

D'autres donjons que le Gouffre de Ragefeu pour les expéditions, d'autres navires et d'autres ports, le bateau sans vous. Voir la
[feuille de route](ROADMAP.md).
