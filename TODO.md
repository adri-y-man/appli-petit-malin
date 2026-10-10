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
