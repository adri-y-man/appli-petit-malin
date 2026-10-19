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

2. **Nouveau jeu "Devine la comptine chantée"** dans Musique Malin (à
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
