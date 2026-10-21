# Story 005: Chute et réapparition au dernier checkpoint

> **Epic**: Coursier des Toits
> **Status**: Ready
> **Layer**: Feature
> **Type**: Integration
> **Estimate**: S
> **Manifest Version**: N/A (minimal — no control manifest)
> **Last Updated**:

## Context

**GDD**: `design/game-brief.md`
**Requirement**: `Brief MVP feature 5` — chute et réapparition au dernier checkpoint, avec pénalité de temps

**ADR Governing Implementation**: N/A (minimal — no ADRs)
**ADR Decision Summary**: N/A (minimal — no ADRs)
**ADR Version**: N/A (minimal — no ADRs)

**Engine**: Unity 6000.3.26f1 | **Risk**: HIGH
**Engine Notes**: none (no ADR engine-compatibility analysis at minimal)

**Control Manifest Rules (this layer)**: N/A (minimal — no control manifest)

---

## Acceptance Criteria

*From the brief: MVP feature 5 and Player goal & fail state (« une chute dans le vide renvoie au dernier checkpoint avec une pénalité de temps »):*

- [ ] Tomber dans le volume de chute (story 003) renvoie le joueur au checkpoint actif le plus récent, ou au départ s'il n'y en a pas.
- [ ] À la réapparition, la vitesse du joueur est remise à zéro et la caméra regarde vers l'avant du parcours.
- [ ] Chaque chute ajoute une pénalité de temps au chrono ; la valeur est configurable, jamais en dur.
- [ ] Le chrono continue de tourner pendant la chute et la réapparition.
- [ ] Si la pénalité fait atteindre zéro au chrono, la livraison est ratée (story 004).
- [ ] La réapparition est instantanée ou presque : pas d'écran de chargement ni d'attente supérieure à une seconde.

---

## Implementation Notes

- Relier le volume de chute (story 003) au checkpoint actif (story 004) ; la pénalité s'ajoute au chrono de la livraison, elle ne le remplace pas.
- Remettre aussi à zéro l'état de mouvement du contrôleur (course murale, glissade) à la réapparition.

---

## Out of Scope

*Handled by neighbouring stories — do not implement here:*

- Story 004: chrono et checkpoints eux-mêmes
- Story 006: affichage de la pénalité à l'écran

---

## Files

- `Assets/Scripts/Gameplay/Delivery/RespawnController.cs`
- `Assets/Scripts/Gameplay/World/FallZone.cs`
- `Assets/Tests/PlayMode/FallRespawnTests.cs`

---

## QA Test Cases

*N/A — no qa-lead specs at this tier; implement against the Acceptance Criteria above*

---

## Test Evidence

*Governed by `qa.level`: at `qa.level: minimal` tests are **waived** (advisory), but a Visual/Feel or UI story's retained screenshot is not.*

**Story Type**: Integration
**Required evidence**:
- Integration: `Assets/Tests/PlayMode/FallRespawnTests.cs` OU un document de playtest — waived at `qa.level: minimal` (advisory)

**Status**: [ ] Not yet created

---

## Dependencies

- Depends on: `production/epics/coursier-des-toits/story-003-rooftop-district.md`, `production/epics/coursier-des-toits/story-004-delivery-timer-checkpoints.md`
- Unlocks: `production/epics/coursier-des-toits/story-007-five-deliveries-results.md`
