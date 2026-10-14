---
name: Toute évolution UX crée sa règle de gestion
description: Dès qu'un élément touchant à l'UX est ajouté ou modifié sur un wireframe, il doit recevoir sa règle de gestion dans le drawer, au format Télécollecte, et dans le bon périmètre (MVP / Cible)
type: feedback
---
**Règle permanente, posée le 2026-10-14.** Chaque fois qu'on ajoute ou modifie un élément qui touche à l'UX d'un wireframe, on lui crée sa règle de gestion **dans le même mouvement**. Pas « plus tard », pas « quand on aura le temps » : la RG fait partie de la livraison, au même titre que le code.

**Why:** Les RG sont le contrat entre le design, les PO et les devs. Une UI livrée sans sa RG est une UI dont personne ne peut vérifier le comportement attendu — c'est exactement ce qui a produit l'écart entre la maquette Figma et le wireframe HTML du Calendrier.

**How to apply:**

1. **Format strict, identique à Télécollecte** — un objet par règle dans le tableau `RG_DATA` du wireframe :
   ```js
   { tab:'<section>', mode:'<périmètre>', titre:'<titre court>',
     regle:'<énoncé en prose, le pourquoi>',
     comportement:'• point\n• point\n• point',
     critere:'<critères vérifiables, un par ligne>' }
   ```
   Champ `question:` en plus quand un point reste à trancher avec le métier.

2. **Le champ `mode` porte le périmètre**, exactement comme Interfacé / Non interfacé côté Télécollecte :
   - `'MVP'` → propre à la première livraison
   - `'Cible'` → propre au périmètre visé
   - `'MVP · Cible'` → vrai dans les deux

3. **Clés localStorage isolées par sous-projet** — jamais les clés génériques :
   `wf_rg_blocks_<sousprojet>`, `wf_rg_version_<sousprojet>`. Incrémenter la version pour déclencher le merge.

4. **La numérotation est calée sur la liste complète**, jamais sur la liste filtrée : RG-14 doit désigner la même règle dans le document MVP et dans le document cible, sinon les deux ne sont plus comparables. Sommaire et corps partagent la même source de numéros.

5. **Ne jamais inventer une règle.** Une RG décrit un comportement réellement codé et vérifié. Un comportement souhaité mais non implémenté n'est pas une RG — c'est une proposition. Voir la constitution, règle 9.

6. **L'accessibilité fait partie du comportement attendu** : quand l'élément ajouté a un état, un libellé, une cible cliquable ou un focus, la RG le dit. Voir la RG « Accessibilité — exigences permanentes » du Calendrier.

État au 2026-10-14 : Calendrier = 20 RG (14 au périmètre MVP, 19 au périmètre cible), 4 sections — Planning, Fiche chambre, Actions, Panel & versions.
