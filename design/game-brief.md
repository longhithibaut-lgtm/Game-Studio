# Game Brief: Le Comptoir du Hameau

**One-sentence pitch:** Tiens l'unique boutique d'un hameau isolé : chaque vente finance les bâtiments qui attirent de nouveaux habitants, donc de nouveaux clients.

## Core loop
- Le jour : approvisionner les rayons, fixer les prix, servir les clients qui défilent.
- Le soir : compter la caisse et la dépenser en bâtiments (puits, atelier, auberge).
- Chaque bâtiment attire de nouveaux habitants : plus de clients, journée suivante plus riche.
- Plus tard : embaucher des vendeurs-caissiers pour automatiser la boutique et se consacrer au village.

## Player goal & fail state — what "working" looks like
- Objectif : faire passer le hameau de 5 à 30 habitants en 20 jours sans faire faillite. Une partie est réussie quand les 30 habitants sont atteints.
- Échec : caisse négative après le bilan du soir, ou tous les habitants ont quitté le hameau.

## MVP — what must exist to be the game
- Boutique : des rayons avec un stock et un prix modifiable par le joueur.
- Clients : des habitants avec un besoin et un budget, qui achètent ou repartent.
- Journée : un cycle jour (vente) / soir (bilan) rythmé par une horloge.
- Réapprovisionnement : commander du stock (coût d'achat contre prix de vente).
- Construction : placer 3 bâtiments sur une grille, payés avec la caisse ; chacun attire de nouveaux habitants.
- Employés : embaucher un vendeur ou caissier qui sert les clients à ta place, contre un salaire payé au bilan du soir.
- Victoire / défaite : conditions ci-dessus et écran de bilan de partie.

## Out of scope — not building this
- Pas de multijoueur, pas de sauvegarde (une partie = une session).
- Pas de carte libre ni d'exploration ; une seule grille de village.
- Pas d'habitants aux goûts différents : tous ont les mêmes besoins dans le MVP.
- Un seul type d'employé (vendeur-caissier) ; pas de gestion fine du personnel (horaires, compétences, moral).
- Pas de météo, de saisons, de dialogues ni d'histoire.
- Pas de version mobile.

## Build order
1. La boucle de vente seule : un rayon, un type de client, un prix. Prouver que fixer le prix est amusant (le cœur du jeu).
2. Cycle jour/soir et réapprovisionnement.
3. Construction et arrivée d'habitants : le lien boutique-village, la partie la moins éprouvée.
4. Employés : un vendeur-caissier qui automatise la vente.
5. Victoire, défaite et écran de bilan.

---
**Who it's for / what they feel:** Joueurs de jeux de gestion cosy qui veulent des sessions de 20 à 30 minutes et la satisfaction de voir un hameau grandir grâce à leurs choix de prix.

**Art & audio direction:** Pixel art 2D en vue de dessus, palette chaude de campagne ; musique acoustique douce et bruitages de boutique (tiroir-caisse, clochette).

**Reference game:** Recettear — la tenue de boutique et la fixation des prix ; sans donjon, avec un village qui grandit autour de la boutique.
