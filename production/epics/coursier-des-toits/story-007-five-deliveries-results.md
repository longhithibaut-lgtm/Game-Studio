# Story 007: 5 livraisons, médailles et écran de résultat

> **Epic**: Coursier des Toits
> **Status**: Ready
> **Layer**: Feature
> **Type**: UI
> **Estimate**: M
> **Manifest Version**: N/A (minimal — no control manifest)
> **Last Updated**:

## Context

**GDD**: `design/game-brief.md`
**Requirement**: `Brief MVP feature 6` — 5 livraisons avec temps cibles (bronze, argent, or) et écran de résultat

**ADR Governing Implementation**: N/A (minimal — no ADRs)
**ADR Decision Summary**: N/A (minimal — no ADRs)
**ADR Version**: N/A (minimal — no ADRs)

**Engine**: Unity 6000.3.26f1 | **Risk**: HIGH
**Engine Notes**: none (no ADR engine-compatibility analysis at minimal)

**Control Manifest Rules (this layer)**: N/A (minimal — no control manifest)

---

## Acceptance Criteria

*From the brief: MVP feature 6 and Player goal & fail state (« réussir les 5 livraisons sous le temps imparti, au moins le bronze »). Interprétation à confirmer : le temps imparti de chaque livraison est son temps bronze.*

- [ ] 5 livraisons sont définies dans le quartier (départ, destination, checkpoints, temps imparti) avec des distances variées.
- [ ] Chaque livraison a trois temps cibles (bronze, argent, or) ; la médaille obtenue se calcule à partir du temps final.
- [ ] Après une livraison réussie, un écran de résultat montre le temps, la médaille et le meilleur temps de la session, avec « Rejouer » et « Livraison suivante ».
- [ ] Après une livraison ratée (chrono à zéro), l'écran propose « Rejouer ».
- [ ] Les meilleurs temps ne sont gardés que pendant la session (aucune sauvegarde).
- [ ] La session est complète quand les 5 livraisons ont été réussies au moins en bronze ; un écran de fin de session le montre.
- [ ] Les écrans se parcourent entièrement à la manette.

---

## Implementation Notes

- Les temps cibles et la liste des livraisons sont des données (ScriptableObject de la story 004), pas du code.
- Calcul de médaille : une petite classe C# pure, testable en Edit Mode (`MedalTests`), même si les tests sont facultatifs à `qa.level: minimal`.
- Réutiliser le HUD (story 006) pour la livraison en cours ; cette story ajoute seulement les écrans de résultat et de fin.
- Placer les 5 paires départ/destination sur les routes de la story 003 ; régler les temps en jouant les routes rapide et sûre.

---

## Out of Scope

*Handled by neighbouring stories — do not implement here:*

- Story 004: logique de livraison (chrono, checkpoints)
- Story 006: HUD en cours de livraison
- Hors brief : sauvegarde, classement en ligne, déblocage de contenu

---

## Files

- `Assets/Scripts/Gameplay/Delivery/MedalCalculator.cs`
- `Assets/Scripts/Gameplay/Delivery/DeliverySession.cs`
- `Assets/Scripts/UI/Results/ResultScreen.cs`
- `Assets/UI/Results/ResultScreen.uxml`
- `Assets/Data/Deliveries/` (5 assets de livraison)
- `Assets/Tests/EditMode/MedalTests.cs`

---

## QA Test Cases

*N/A — no qa-lead specs at this tier; implement against the Acceptance Criteria above*

---

## Test Evidence

*Governed by `qa.level`: at `qa.level: minimal` tests are **waived** (advisory), but a Visual/Feel or UI story's retained screenshot is not.*

**Story Type**: UI
**Required evidence**:
- UI: une capture d'écran conservée dans `production/qa/evidence/` de chaque écran touché (résultat réussi, résultat raté, fin de session)

**Status**: [ ] Not yet created

---

## Dependencies

- Depends on: `production/epics/coursier-des-toits/story-004-delivery-timer-checkpoints.md`, `production/epics/coursier-des-toits/story-005-fall-respawn.md`, `production/epics/coursier-des-toits/story-006-minimal-hud.md`
- Unlocks: None
