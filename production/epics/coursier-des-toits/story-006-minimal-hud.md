# Story 006: HUD minimal

> **Epic**: Coursier des Toits
> **Status**: Ready
> **Layer**: Presentation
> **Type**: UI
> **Estimate**: S
> **Manifest Version**: N/A (minimal — no control manifest)
> **Last Updated**:

## Context

**GDD**: `design/game-brief.md`
**Requirement**: `Brief MVP feature 7` — HUD minimal : chrono et direction de la destination

**ADR Governing Implementation**: N/A (minimal — no ADRs)
**ADR Decision Summary**: N/A (minimal — no ADRs)
**ADR Version**: N/A (minimal — no ADRs)

**Engine**: Unity 6000.3.26f1 | **Risk**: HIGH
**Engine Notes**: none (no ADR engine-compatibility analysis at minimal)

**Control Manifest Rules (this layer)**: N/A (minimal — no control manifest)

---

## Acceptance Criteria

*From the brief: MVP feature 7 and Art & audio direction (ville blanche épurée):*

- [ ] Le HUD affiche le chrono de la livraison en cours (secondes et dixièmes), mis à jour à chaque image.
- [ ] Un indicateur de direction montre où se trouve la destination et suit la rotation du joueur.
- [ ] Le HUD apparaît au début d'une livraison et disparaît ou se fige à sa fin.
- [ ] Rien d'autre n'est affiché en cours de course (HUD minimal).
- [ ] Le chrono reste lisible sur les surfaces blanches du blocout (contraste suffisant) à 1280×720.
- [ ] Aucun élément n'exige la souris ; l'ensemble est lisible à la manette.

---

## Implementation Notes

- Choisir UI Toolkit ou UGUI avec `unity-ui-specialist`, d'après `docs/engine-reference/unity/modules/ui.md` (UI Toolkit recommandé pour le nouveau runtime UI).
- Le HUD lit l'état de la livraison (story 004) ; il ne possède aucun état de jeu.
- Textes prêts pour la localisation : pas de chaîne en dur dans le code (`.claude/rules/ui-code.md`).

---

## Out of Scope

*Handled by neighbouring stories — do not implement here:*

- Story 004: logique du chrono
- Story 007: écran de résultat et menus

---

## Files

- `Assets/Scripts/UI/Hud/DeliveryHud.cs`
- `Assets/UI/Hud/DeliveryHud.uxml`
- `Assets/UI/Hud/DeliveryHud.uss`

---

## QA Test Cases

*N/A — no qa-lead specs at this tier; implement against the Acceptance Criteria above*

---

## Test Evidence

*Governed by `qa.level`: at `qa.level: minimal` tests are **waived** (advisory), but a Visual/Feel or UI story's retained screenshot is not.*

**Story Type**: UI
**Required evidence**:
- UI: une capture d'écran conservée dans `production/qa/evidence/` du HUD en cours de livraison, sur le blocout blanc

**Status**: [ ] Not yet created

---

## Dependencies

- Depends on: `production/epics/coursier-des-toits/story-004-delivery-timer-checkpoints.md`
- Unlocks: `production/epics/coursier-des-toits/story-007-five-deliveries-results.md`
