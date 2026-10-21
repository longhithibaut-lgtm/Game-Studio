# Story 001: Contrôleur en première personne

> **Epic**: Coursier des Toits
> **Status**: Ready
> **Layer**: Foundation
> **Type**: Visual/Feel
> **Estimate**: L
> **Manifest Version**: N/A (minimal — no control manifest)
> **Last Updated**:

## Context

**GDD**: `design/game-brief.md`
**Requirement**: `Brief MVP feature 1` — contrôleur en première personne : course et saut avec conservation de l'élan

**ADR Governing Implementation**: N/A (minimal — no ADRs)
**ADR Decision Summary**: N/A (minimal — no ADRs)
**ADR Version**: N/A (minimal — no ADRs)

**Engine**: Unity 6000.3.26f1 | **Risk**: HIGH
**Engine Notes**: none (no ADR engine-compatibility analysis at minimal)

**Control Manifest Rules (this layer)**: N/A (minimal — no control manifest)

---

## Acceptance Criteria

*From the brief: MVP feature 1, Core loop, Art & audio direction and Platform settings:*

- [ ] Le joueur se déplace et regarde en première personne à la manette (stick gauche = déplacement, stick droit = caméra) et au clavier/souris.
- [ ] La vitesse monte progressivement jusqu'à une vitesse de course maximale ; relâcher l'entrée décélère sans arrêt instantané.
- [ ] Le saut a une hauteur variable (appui court / appui long) et laisse un contrôle aérien partiel.
- [ ] Courir puis sauter conserve la vitesse horizontale pendant le saut ; l'élan n'est pas remis à zéro à l'atterrissage tant que le joueur continue d'avancer.
- [ ] La détection du sol est fiable : aucun saut refusé alors que le joueur est visiblement sur un bord ou une marche.
- [ ] Vitesse maximale, accélération, décélération, hauteur de saut et gravité sont dans un asset de configuration (ScriptableObject), jamais en dur dans le code.
- [ ] Les entrées passent par le package Input System (pas l'ancien Input Manager), avec un asset d'actions couvrant manette et clavier/souris.
- [ ] Une salle de test (`TestRoom`) contient sol, marches, vides et plateformes à distances variées pour essayer course, saut et atterrissage.
- [ ] La salle de test tourne à 60 fps (image ≤ 16,6 ms) sur la machine de développement.

---

## Implementation Notes

- **Prérequis :** le projet Unity (3D, URP) doit exister à la racine du dépôt (`Assets/`, `Packages/`, `ProjectSettings/`). CCGS ne le crée pas : voir le résumé de `/setup-engine`.
- Lire avant d'écrire : `docs/engine-reference/unity/modules/input.md` (Input System, ancien Input Manager déprécié) et `docs/engine-reference/unity/modules/physics.md`. Unity 6.3 est hors des connaissances du modèle : aucune API de mémoire.
- Choisir `CharacterController` ou `Rigidbody` d'après `physics.md` et noter le choix dans **Files**. Les stories 002 et 005 s'appuient sur ce choix.
- Avancer en mesurant la sensation : c'est le risque n°1 du brief. Régler les valeurs dans l'asset de configuration, pas dans le code.

---

## Out of Scope

*Handled by neighbouring stories — do not implement here:*

- Story 002: course murale, glissade, escalade de rebord
- Story 003: le quartier de toits (ici, seulement la salle de test)
- Story 005: chute dans le vide et réapparition

---

## Files

- `Assets/Scripts/Gameplay/Player/PlayerController.cs`
- `Assets/Scripts/Gameplay/Player/PlayerMovementConfig.cs` (ScriptableObject)
- `Assets/Settings/PlayerInput.inputactions`
- `Assets/Scenes/TestRoom.unity`

---

## QA Test Cases

*N/A — no qa-lead specs at this tier; implement against the Acceptance Criteria above*

---

## Test Evidence

*Governed by `qa.level`: at `qa.level: minimal` tests are **waived** (advisory), but a Visual/Feel or UI story's retained screenshot is not.*

**Story Type**: Visual/Feel
**Required evidence**:
- Visual/Feel: une capture d'écran conservée dans `production/qa/evidence/` (vue première personne dans `TestRoom`, compteur de fps visible) + sign-off dans `production/qa/evidence/first-person-controller-evidence.md`

**Status**: [ ] Not yet created

---

## Dependencies

- Depends on: None (prérequis : projet Unity créé, voir Implementation Notes)
- Unlocks: `production/epics/coursier-des-toits/story-002-parkour-moves.md`, `production/epics/coursier-des-toits/story-003-rooftop-district.md`
