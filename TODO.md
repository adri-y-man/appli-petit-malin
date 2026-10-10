# À faire

Liste des prochaines modifications demandées, pas encore faites.

1. **Vrais cris d'animaux dans "Trouve l'animal selon son cri"** (mode
   `animalsound`, `ANIMAL_SOUND_DEFS` dans `index.html`) : actuellement le
   "cri" n'est qu'une onomatopée affichée en texte (`cry: "OUAF"`, etc.),
   pas un son audio. Remplacer/compléter par de vrais enregistrements de
   cris d'animaux, lus au clic (même principe que les instruments de
   Musique Libre : `MUSIC_INSTRUMENT_AUDIO` + `new Audio(src)` mis en
   cache, voir aussi `audio/level-up.mp3` pour le pattern fichier externe
   plutôt que data URI inline).

2. **Mode solo (contre l'ordinateur) aux Dames**, avec une IA dont la
   force dépend du niveau choisi. État actuel (`index.html`, à partir de
   `var DAMES_SIZE = 6;`) : Dames n'est que du 2 joueurs en local, pas
   d'IA, pas de pilule de niveau (jeu de société = `isBoardGameMode` =
   écran "noStars", voir `selectMode`). `damesLegalMovesFor(board, row,
   col)` existe déjà et donne les coups légaux d'une case -- base
   réutilisable pour une IA (lister tous les coups de toutes les pièces
   du joueur "w", choisir selon la force voulue).
   Points à trancher avant de coder :
   - Comment choisir solo vs 2 joueurs (écran de choix avant la partie ?
     bouton dans le menu Dames ?) -- et comment choisir le niveau de
     l'IA dans ce cas (la pilule de niveau n'existe pas sur cet écran
     aujourd'hui).
   - Niveaux de force envisageables : facile = coup aléatoire parmi les
     légaux (en priorisant une prise si possible) ; moyen = + éviter de
     se faire prendre sans raison ; fort = minimax/évaluation simple sur
     quelques coups.
   - Le joueur reste toujours les pions noirs (`b`), l'IA joue les
     blancs (`w`) ?
