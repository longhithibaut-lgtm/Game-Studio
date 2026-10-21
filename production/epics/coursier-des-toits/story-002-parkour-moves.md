# Story 002: Mouvements de parkour

> **Epic**: Coursier des Toits
> **Status**: Ready
> **Layer**: Core
> **Type**: Visual/Feel
> **Estimate**: L
> **Manifest Version**: N/A (minimal — no control manifest)
> **Last Updated**:

## Context

**GDD**: `design/game-brief.md`
**Requirement**: `Brief MVP feature 2` — mouvements de parkour : course murale, glissade, escalade de rebord

**ADR Governing Implementation**: N/A (minimal — no ADRs)
**ADR Decision Summary**: N/A (minimal — no ADRs)
**ADR Version**: N/A (minimal — no ADRs)

**Engine**: Unity 6000.3.26f1 | **Risk**: HIGH
**Engine Notes**: none (no ADR engine-compatibility analysis at minimal)

**Control Manifest Rules (this layer)**: N/A (minimal — no control manifest)

---

## Acceptance Criteria

*From the brief: MVP feature 2 and Core loop (« enchaîner sauts, courses murales, glissades et escalades sans perdre l'élan »):*

- [ ] Course murale : en l'air contre un mur latéral en avançant, le joueur court le long du mur pendant une durée limitée, puis retombe.
- [ ] Saut depuis le mur : il projette le joueur à l'opposé du mur en conservant son élan.
- [ ] Glissade : lancée en pleine course, elle conserve l'élan, passe sous un obstacle bas et rend le joueur en vitesse de course à la sortie.
- [ ] Escalade de rebord : sauter vers un rebord à portée de main hisse le joueur dessus sans remettre sa vitesse à zéro.
- [ ] Les quatre mouvements s'enchaînent (course → saut → course murale → saut mural → rebord) sans blocage ni retour forcé à l'arrêt.
- [ ] Durée de course murale, vitesse de glissade et portée de rebord sont dans la configuration de la story 001, jamais en dur.
- [ ] Tous les mouvements se déclenchent à la manette et au clavier/souris (actions ajoutées à l'asset d'entrées).
- [ ] `TestRoom` est étendue avec un mur de course murale, un obstacle bas, un rebord et une chaîne qui enchaîne les quatre mouvements.

---

## Implementation Notes

- Étendre le contrôleur de la story 001 (même moteur de déplacement) plutôt que d'en écrire un second.
- Lire `docs/engine-reference/unity/modules/physics.md` pour la détection des murs et des rebords.
- Régler à la manette d'abord : la manette est l'entrée principale du projet.

---

## Out of Scope

*Handled by neighbouring stories — do not implement here:*

- Story 001: course et saut de base
- Story 003: le quartier de toits
- Story 005: chute et réapparition

---

## Files

- `Assets/Scripts/Gameplay/Player/PlayerController.cs`
- `Assets/Scripts/Gameplay/Player/PlayerMovementConfig.cs`
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
- Visual/Feel: une capture d'écran conservée dans `production/qa/evidence/` (la chaîne de quatre mouvements dans `TestRoom`) + sign-off dans `production/qa/evidence/parkour-moves-evidence.md`

**Status**: [ ] Not yet created

---

## Dependencies

- Depends on: `production/epics/coursier-des-toits/story-001-first-person-controller.md`
- Unlocks: `production/epics/coursier-des-toits/story-003-rooftop-district.md`
