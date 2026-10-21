# Story 004: Livraison — chrono et checkpoints

> **Epic**: Coursier des Toits
> **Status**: Ready
> **Layer**: Core
> **Type**: Logic
> **Estimate**: M
> **Manifest Version**: N/A (minimal — no control manifest)
> **Last Updated**:

## Context

**GDD**: `design/game-brief.md`
**Requirement**: `Brief MVP feature 4` — livraison : départ, destination marquée, chrono et checkpoints

**ADR Governing Implementation**: N/A (minimal — no ADRs)
**ADR Decision Summary**: N/A (minimal — no ADRs)
**ADR Version**: N/A (minimal — no ADRs)

**Engine**: Unity 6000.3.26f1 | **Risk**: HIGH
**Engine Notes**: none (no ADR engine-compatibility analysis at minimal)

**Control Manifest Rules (this layer)**: N/A (minimal — no control manifest)

---

## Acceptance Criteria

*From the brief: MVP feature 4, Core loop and Player goal & fail state (« chrono à zéro = livraison ratée »):*

- [ ] Une livraison a un point de départ, une destination marquée dans le monde et un temps imparti.
- [ ] Le chrono démarre quand le joueur prend le colis au départ et s'arrête quand la livraison se termine.
- [ ] Entrer dans la zone de destination avant la fin du chrono = livraison réussie ; le temps final est enregistré.
- [ ] Chrono à zéro = livraison ratée ; le joueur peut la relancer depuis le départ.
- [ ] Des checkpoints sont placés sur le parcours ; entrer dans l'un d'eux en fait le checkpoint actif (le plus récent remplace l'ancien).
- [ ] L'état de livraison (Inactive, EnCours, Réussie, Ratée) est une logique pure, testable sans scène, séparée du MonoBehaviour.
- [ ] Temps imparti, positions de départ, de destination et de checkpoints viennent d'une donnée de livraison (ScriptableObject), pas du code.
- [ ] Un test Edit Mode couvre le chrono (démarrage, arrêt, expiration) et les transitions d'état.

---

## Implementation Notes

- Séparer la logique (classe C# simple) de la scène (MonoBehaviour qui la nourrit en temps) : c'est ce qui rend le test Edit Mode possible.
- Le temps vient du jeu (delta time), jamais d'une horloge système.
- Test : classe `DeliveryTests`, méthodes `[Scénario]_[Résultat]` en PascalCase (`.claude/rules/test-standards.md`).

---

## Out of Scope

*Handled by neighbouring stories — do not implement here:*

- Story 005: chute et pénalité de temps
- Story 006: affichage du chrono et de la direction
- Story 007: les 5 livraisons, médailles et écran de résultat

---

## Files

- `Assets/Scripts/Gameplay/Delivery/DeliveryState.cs`
- `Assets/Scripts/Gameplay/Delivery/DeliveryController.cs`
- `Assets/Scripts/Gameplay/Delivery/DeliveryData.cs` (ScriptableObject)
- `Assets/Scripts/Gameplay/Delivery/Checkpoint.cs`
- `Assets/Tests/EditMode/DeliveryTests.cs`

---

## QA Test Cases

*N/A — no qa-lead specs at this tier; implement against the Acceptance Criteria above*

---

## Test Evidence

*Governed by `qa.level`: at `qa.level: minimal` tests are **waived** (advisory), but a Visual/Feel or UI story's retained screenshot is not.*

**Story Type**: Logic
**Required evidence**:
- Logic: `Assets/Tests/EditMode/DeliveryTests.cs` — waived at `qa.level: minimal` (advisory) ; à écrire quand même, c'est la seule story à logique pure

**Status**: [ ] Not yet created

---

## Dependencies

- Depends on: `production/epics/coursier-des-toits/story-003-rooftop-district.md`
- Unlocks: `production/epics/coursier-des-toits/story-005-fall-respawn.md`, `production/epics/coursier-des-toits/story-006-minimal-hud.md`, `production/epics/coursier-des-toits/story-007-five-deliveries-results.md`
