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

4. **Nouveau jeu "Devine la comptine chantée"** dans Musique Malin (à
   côté de Musique libre / Quel instrument ? / Répète le rythme / grave-
   aigu) : un extrait chanté (vrai enregistrement, pas synthétisé) est
   joué, l'enfant doit deviner de quelle chanson/comptine il s'agit
   parmi plusieurs titres proposés. Mécanique proche de "Quel
   instrument ?" (`instruments` : joue un son, 3 réponses au choix) mais
   avec des chansons chantées à la place de sons d'instruments, et des
   pochettes/emoji ou juste le titre en texte comme réponses.
   Points à trancher avant de coder :
   - Quelles comptines (domaine public/libres de droits, comme la
     musique de fond actuelle via Pixabay) et combien au départ ?
   - Extrait complet ou juste les premières secondes (plus facile de
     deviner vite = indice progressif selon le niveau) ?

5. **Nouveau jeu "Devine le pays à partir de son drapeau"** : un drapeau
   affiché, l'enfant choisit le bon nom de pays parmi plusieurs
   propositions. Il existe déjà un pool de 10 drapeaux réutilisable,
   `FLAG_SYMBOL_POOL` (actuellement utilisé par "Paires cachées
   (drapeaux)" en Mémoire Malin) -- il manque juste l'association
   drapeau → nom de pays (en français). Mécanique proche de "Les
   couleurs"/"Les animaux" (image + choix de mots). Points à trancher :
   - Dans quelle catégorie (Mémoire Malin à côté des paires de drapeaux,
     Anglais Malin si les noms sont en anglais, ou nouvelle catégorie
     "Géographie" à créer) ?
   - Faut-il plus de 10 drapeaux que le pool actuel pour un vrai jeu de
     quiz (celui-là était pensé pour un jeu de mémoire, pas un quiz) ?

6. **Revoir la mécanique du Sudoku** (`sudokuforme`/`sudokuchiffre`,
   partagent le même moteur -- `onSudokuCellTap`/`onSudokuPaletteTap`/
   `onSudokuComplete` dans `index.html`). Aujourd'hui `onSudokuPaletteTap`
   vérifie chaque case IMMÉDIATEMENT contre `state.sudokuSolution` : si ce
   n'est pas la bonne valeur, la case secoue et refuse de se remplir --
   impossible de poser autre chose que la bonne réponse, donc pas un vrai
   sudoku. À la place : laisser remplir n'importe quelle case avec
   n'importe quelle valeur (y compris en corrigeant une case déjà remplie),
   et ajouter un bouton "Valider" qui vérifie toute la grille d'un coup à
   la fin et dit si c'est bon ou pas.
   Points à trancher avant de coder :
   - Si c'est faux après validation, qu'est-ce qui est montré : juste
     "c'est pas encore ça" sans détail, ou les cases en erreur
     surlignées (sans donner la bonne réponse) ?
   - Le bouton "Valider" est-il actif seulement grille pleine, ou
     utilisable à tout moment pour vérifier l'avancement ?

7. **"Guide le renard" : 2-3 friandises aux niveaux supérieurs** (mode
   `codeseq`). Aujourd'hui `codeGenerateMaze`/`codeGenerateLayout` ne
   placent qu'une seule case cible ("T", trouvée via BFS depuis le
   départ), et `codeLaunchSeq` considère le niveau réussi dès que le
   renard atteint cette case. Pour les niveaux élevés, générer 2 puis 3
   cases à manger au lieu d'une seule -- parcours plus long, niveau plus
   difficile.
   Points à trancher avant de coder :
   - À partir de quel niveau (3 ? 4-5 seulement ?) et combien de
     friandises par niveau ?
   - Le renard doit-il les manger dans un ordre précis, ou n'importe
     lequel/dans n'importe quel ordre tant que toutes y passent ?
   - Chaque friandise reste-t-elle le même emoji (`codeCurrentTreat`,
     tiré une fois) ou un emoji différent par case ?
