# Story 003: Quartier de toits en blocout

> **Epic**: Coursier des Toits
> **Status**: Ready
> **Layer**: Core
> **Type**: Visual/Feel
> **Estimate**: L
> **Manifest Version**: N/A (minimal — no control manifest)
> **Last Updated**:

## Context

**GDD**: `design/game-brief.md`
**Requirement**: `Brief MVP feature 3` — un quartier de toits en blocout, avec plusieurs routes possibles

**ADR Governing Implementation**: N/A (minimal — no ADRs)
**ADR Decision Summary**: N/A (minimal — no ADRs)
**ADR Version**: N/A (minimal — no ADRs)

**Engine**: Unity 6000.3.26f1 | **Risk**: HIGH
**Engine Notes**: none (no ADR engine-compatibility analysis at minimal)

**Control Manifest Rules (this layer)**: N/A (minimal — no control manifest)

---

## Acceptance Criteria

*From the brief: MVP feature 3, Out of scope (un seul quartier, blocout et palette seulement) and Art & audio direction:*

- [ ] Un seul quartier de toits en blocout (formes simples, matériaux unis) se parcourt de bout en bout avec le contrôleur des stories 001 et 002.
- [ ] Il offre de la place pour 5 paires départ/destination, assez éloignées pour que chaque livraison dure de l'ordre de la minute.
- [ ] Chaque paire est reliée par au moins deux routes différentes.
- [ ] Une route « sûre » ne demande que course et saut ; une route « rapide » demande au moins un mouvement avancé (course murale, glissade ou rebord).
- [ ] Les vides entre toits sont franchissables ; aucun passage n'est impossible avec les mouvements du MVP.
- [ ] Un volume de chute sous les toits est détectable par le code (utilisé par la story 005).
- [ ] Surfaces blanches épurées ; une couleur vive marque les prises et les routes.
- [ ] Le parcours complet tient 60 fps (image ≤ 16,6 ms) sur la machine de développement.

---

## Implementation Notes

- Construire en blocout (cubes, rampes) : pas d'art final, hors périmètre du brief.
- Dessiner les routes d'abord sur papier ou en liste (départ → destination → route sûre / rapide), puis seulement en géométrie.
- Mesurer les distances de saut avec le contrôleur réel, pas à l'œil.
- Rendu URP : `docs/engine-reference/unity/modules/rendering.md`.

---

## Out of Scope

*Handled by neighbouring stories — do not implement here:*

- Story 004: logique de livraison (chrono, checkpoints)
- Story 005: réapparition après une chute
- Story 007: les 5 livraisons elles-mêmes (départs, destinations, temps)

---

## Files

- `Assets/Scenes/RooftopDistrict.unity`
- `Assets/Scripts/Gameplay/World/FallZone.cs`
- `Assets/Materials/Blockout/` (blanc, couleur vive)

---

## QA Test Cases

*N/A — no qa-lead specs at this tier; implement against the Acceptance Criteria above*

---

## Test Evidence

*Governed by `qa.level`: at `qa.level: minimal` tests are **waived** (advisory), but a Visual/Feel or UI story's retained screenshot is not.*

**Story Type**: Visual/Feel
**Required evidence**:
- Visual/Feel: une capture d'écran conservée dans `production/qa/evidence/` (vue d'ensemble du quartier + une route rapide en jeu) + sign-off dans `production/qa/evidence/rooftop-district-evidence.md`

**Status**: [ ] Not yet created

---

## Dependencies

- Depends on: `production/epics/coursier-des-toits/story-002-parkour-moves.md`
- Unlocks: `production/epics/coursier-des-toits/story-004-delivery-timer-checkpoints.md`, `production/epics/coursier-des-toits/story-005-fall-respawn.md`
