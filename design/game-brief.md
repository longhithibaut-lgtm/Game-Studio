# Game Brief: Coursier des Toits

**One-sentence pitch:** Coursier clandestin d'une ville verticale, tu livres des colis urgents en courant sur les toits : chaque seconde se gagne dans l'enchaînement de tes mouvements.

## Core loop
- Accepter une livraison : un départ, une destination, un chrono.
- Trouver sa route sur les toits en enchaînant sauts, courses murales, glissades et escalades sans perdre l'élan.
- Livrer, voir son temps et sa médaille, puis rejouer pour optimiser la route ou passer à la suivante.

## Player goal & fail state — what "working" looks like
- Objectif : réussir les 5 livraisons du quartier sous le temps imparti (au moins le bronze). Une session est complète quand les 5 sont livrées.
- Échec : chrono à zéro = livraison ratée, à relancer. Une chute dans le vide renvoie au dernier checkpoint avec une pénalité de temps.

## MVP — what must exist to be the game
- Contrôleur en première personne : course et saut avec conservation de l'élan.
- Mouvements de parkour : course murale, glissade, escalade de rebord.
- Un quartier de toits en blocout, avec plusieurs routes possibles.
- Livraison : départ, destination marquée, chrono et checkpoints.
- Chute et réapparition au dernier checkpoint, avec pénalité de temps.
- 5 livraisons avec temps cibles (bronze, argent, or) et écran de résultat.
- HUD minimal : chrono et direction de la destination.

## Out of scope — not building this
- Pas de combat ni d'ennemis.
- Pas d'histoire, de cinématiques ni de dialogues.
- Pas de multijoueur ni de classement en ligne.
- Un seul quartier ; pas de monde ouvert.
- Pas de personnalisation, d'arbre de compétences ni d'économie.
- Pas de sauvegarde : les meilleurs temps ne durent que la session.
- Pas d'art final : blocout et palette de couleurs seulement.

## Build order
1. Le contrôleur et les mouvements dans une salle de test : prouver que courir est grisant (le risque n°1 du genre, c'est la sensation).
2. Le quartier de toits en blocout, avec plusieurs routes.
3. Livraisons : chrono, checkpoints, chute et réapparition.
4. Les 5 livraisons avec médailles, HUD et écran de résultat.

---
**Who it's for / what they feel:** Joueurs qui aiment la vitesse et l'optimisation de parcours, en sessions de 15 à 30 minutes ; sensation de flow et de maîtrise.

**Art & audio direction:** Ville blanche épurée, avec une couleur vive qui signale les prises et les routes ; souffle, pas, vent et musique électronique ambiante.

**Reference game:** Mirror's Edge — la course sur les toits en première personne et les contre-la-montre ; sans combat ni histoire.
