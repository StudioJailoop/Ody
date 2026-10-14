---
name: loopcraft-constitution
description: "Constitution Loopcraft — socle produit immuable, règles fonctionnelles et invariants techniques non négociables"
metadata:
  node_type: memory
  type: project
  originSessionId: current
---

# LOOPCRAFT — CONSTITUTION PRODUIT IMMUABLE

Loopcraft est un système de capitalisation de la connaissance produit.
Sa valeur est dans la mémoire accumulée, pas dans les écrans.

## RÈGLES FONCTIONNELLES IMMUTABLES

**R1 — Commentaires PO**
- Arrivent dans "Commentaires équipe"
- Ne sont jamais perdus
- Restent visibles jusqu'à traitement
- Peuvent être requalifiés

**R2 — Requalification Designer**
- Retour / Idée / Règle de gestion / Question
- Aucune autre catégorie sans validation de la constitution

**R3 — Archivage**
- Traité → quitte les vues actives immédiatement
- Apparaît uniquement dans les archives
- Reste consultable
- N'est jamais supprimé automatiquement

**R4 — Envoi Claude**
- Considéré comme traité
- Archivé automatiquement
- Reste consultable dans l'historique

**R5 — Commentaires équipe = boîte de réception unique**
- Entrée unique des retours PO
- Aucun commentaire PO ne contourne cette étape

**R6 — Séparation PO / Designer**
- PO : consulte, commente, lit la documentation
- Designer : requalifie, archive, génère, documente, construit les PRD
- Cette séparation ne doit jamais être cassée

**R7 — Documentation**
- Consultable, persistante, versionnée
- Survit aux évolutions

**R8 — Règles de gestion**
- Survivent aux mises à jour, changements de machine, changements de version
- Ne sont jamais écrasées silencieusement

## INVARIANTS TECHNIQUES

**Invariant A** — Aucune donnée critique uniquement en localStorage
- Données critiques → Firebase : commentaires, archives, documentation, RG, PRD, historique Claude

**Invariant B** — Aucun versioning destructif
- Interdit : overwrite, reset automatique, remplacement silencieux
- Autorisé : merge, migration, enrichissement

**Invariant C** — Isolation par projet
- Préfixe obligatoire : wf_telecollecte_*, wf_cardex_*, wf_ddj_*, wf_dashboard_*
- Aucune collision possible entre projets sur le même domaine

**Invariant D** — Archives sacrées
- Consultable, restaurable, indestructible

## OBJECTIF FINAL
Conserver : décisions, commentaires, RG, documentation, historique.
Éviter toute perte silencieuse.
Si une évolution améliore l'UI mais menace la mémoire produit → elle est refusée.

**Why:** Constitution établie après audit complet juin 2026 — ces règles protègent 6+ mois de mémoire produit accumulée.
**How to apply:** Avant tout développement Loopcraft (Télécollecte, Cardex, DDJ, dashboard), vérifier chaque invariant. Si un invariant est menacé → STOP, signaler avant d'implémenter.
