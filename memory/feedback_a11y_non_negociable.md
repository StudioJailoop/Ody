---
name: Accessibilité non négociable sur tous les écrans Club Med
description: Tout écran produit sur le projet Club Med doit être accessible (a11y) — règle permanente, aucune exception, aucun arbitrage possible
type: feedback
---
TOUS les écrans demandés sur le projet **Club Med** (Odyssey / Trident) doivent être accessibles. L'accessibilité n'est jamais une variable d'ajustement : si un choix de design ou une contrainte de place la compromet, on change le choix de design — pas l'accessibilité.

**Why:** Règle posée explicitement par Sébastien le 2026-10-14, formulée comme intransigeante (« on ne doit jamais transiger »). Les utilisateurs sont des pros internes Club Med qui passent la journée sur ces écrans.

**How to apply:**

1. **Avant de livrer un écran**, vérifier et annoncer explicitement dans la réponse :
   - Contraste texte/fond ≥ **4.5:1** (≥ 3:1 pour texte ≥ 24px ou ≥ 19px bold, et pour les bordures de composants / états de focus)
   - Cibles cliquables ≥ **44 × 44 px** (switch, checkbox, icône-bouton, croix de fermeture)
   - **Jamais l'information par la seule couleur** : un statut coloré (bandes du calendrier, badges Platinum/Gold/Silver) doit aussi porter un libellé, une icône ou une forme
   - **Chaque champ a un libellé visible** — un placeholder n'est PAS un libellé
   - **Chaque switch / checkbox a un libellé texte** adjacent
   - Ordre de lecture = ordre visuel ; ordre de tabulation cohérent
   - État **focus visible** sur tout élément interactif
2. **Si la maquette source viole une de ces règles**, le signaler au lieu de recopier le défaut.
3. **Si une contrainte de place empêche de respecter la règle**, ne pas le faire silencieusement : proposer une autre mise en page.
4. Un token du DS ne dispense pas de vérifier le contraste réel de la paire texte/fond utilisée.
5. L'exigence est documentée côté produit dans la RG « Accessibilité — exigences permanentes » du Calendrier — voir [[Toute évolution UX crée sa règle de gestion]].
