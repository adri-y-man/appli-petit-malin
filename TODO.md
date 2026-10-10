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

3. **Nouveau jeu "Somme de fruits"** : plusieurs fruits affichés, chacun
   avec une valeur différente (ex. 🍎 = 2, 🍌 = 3, 🍇 = 5...), l'enfant
   doit trouver la somme totale. Probablement dans Calcul Malin, en
   mode-card à côté de "Mes premières équations"/"Compte les objets".
   Mécanique proche de "Compte les objets" (`generateCountProblem`) mais
   avec des valeurs différentes par type de fruit au lieu de compter des
   objets identiques -- et des niveaux qui font monter le nombre de
   fruits affichés / la variété de valeurs, comme les autres jeux de
   calcul (3 réponses au choix, mêmes mécaniques de niveau/étoiles).
   Points à trancher avant de coder :
   - Les valeurs sont-elles toujours visibles à l'écran (ex. une petite
     légende "🍎=2, 🍌=3") ou à mémoriser ?
   - Les fruits affichés sont-ils toujours les mêmes à chaque partie, ou
     tirés au sort parmi un pool plus large à chaque niveau ?
