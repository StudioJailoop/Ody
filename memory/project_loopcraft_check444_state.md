---
name: project-loopcraft-check444-state
description: "État exact du wireframe au checkpoint check-444 — commit 0da33b2, session 2026-06-25/26"
metadata:
  type: project
---

# État wireframe check-444 — commit `0da33b2`

> Checkpoint de référence au 2026-06-25/26. Commande de retour : `git reset --hard check-444`

## Fichier de travail
`wireframe-telecollecte-cas1-V4.html` dans Dropbox/Taff/.../01_Club Med/

## Ce qui est validé et fonctionnel

### Workflow Loopcraft commentaires PO
- Archivage via `archiveClaudeSelection()` : ping disparaît ✅, commentaire quitte l'actif ✅, apparaît dans Archives ✅
- Archive locale de sécurité : `TEAM_ARCHIVES_KEY = 'wf_team_comments_archives'`
- `upsertTeamArchive()` alimentée lors du traitement Claude
- `loadTeamComments()` merge l'archive locale en mode Archives (résistant aux race conditions Firebase)
- `setCommentArchived()` utilise `fbSaveOne` atomique (plus de race condition PUT global)
- `loadTeamComments()` et `refreshTeamCommentsCount()` utilisent `isPinArchived()` au lieu de `p.archived` directement

### Bloc écart par MDP — pattern complet sur les 3 onglets
Règle : dès qu'un écart est calculable → 2 niveaux (bloc principal + sticky)

**Télécollecte** : `_updateBadges(ecart, fmt)` → `#kpi-ecart` + `#proposal-a-pill`
**Previous Date** : `_updateBadgesAnt()` → `#ant-kpi-ecart-bloc` + `#ant-pill` (sim: Visa 8€, Amex 12€, WeChat 0€)
**Régularisation** : `_updateBadgesReg(ecartBase, ecartRestant, byMdp)` → `#reg-kpi-ecart-bloc` + `#reg-pill` (sim: Visa 400€, Amex 600€, WeChat 0€)

Couleurs : MDP avec écart → rouge `#BF2F17`, MDP OK ou 0 → vert `#088A20`
Sticky : visible uniquement quand `bloc-date` sort du viewport, piloté par `updateStickyState()`

### Barre sticky Régularisation
- `id="tpe-tabs-bar-reg"` — même classe `.tpe-tabs-bar` que Télécollecte et Previous Date
- `#reg-pill` + `#btnv-reg-sticky`
- `goTo('reg')` → affiche la barre, cache les autres
- `checkReg()` appelle `_updateBadgesReg()` + sync `btnv-reg-sticky.className`

### Éléments conservés intacts
- `#reg-ecart` (caché, `display:none`) — toujours lu par `checkReg()` via `dataset.initial`
- `#reg-ecart-wrap` (caché) — compatibilité `checkReg()`
- `#btnv-reg` libellé : "Submit regularisation"
- `#btnv-reg-sticky` libellé : "Submit regularisation"

### Libellés boutons
- Télécollecte : `#btnv`, `#btnv-sticky`, `#btnv-ant`, `#btnv-ant-sticky` → **"Submit"**
- Régularisation : `#btnv-reg`, `#btnv-reg-sticky` → **"Submit regularisation"**
- JS : `btnv.textContent = 'Complete'` / `'Submit'` selon `saisieMode`

## Tags git
- `check-444` → `0da33b2`
- `check-444-final` → `0da33b2`
- `checkpoint/check-444` → `0da33b2`
- `check-444-before-final` → `4671b55` (ancienne présentation)

## À faire au prochain démarrage
- Régularisation écart : simulé (Visa 400€, Amex 600€, WeChat 0€) — pas encore connecté aux vraies saisies
- Push GitHub non effectué (en attente de validation finale)
- `server.py` modifié non commité (non bloquant)

**Why:** Checkpoint créé après session de présentation 2026-06-25 + ajout écart Régularisation.
**How to apply:** Au démarrage suivant, lire ce fichier pour reprendre exactement là où on s'est arrêtés sans re-diagnostiquer.
