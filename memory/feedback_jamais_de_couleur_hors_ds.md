---
name: Jamais de valeur hors design system — couleur ni typo
description: Interdiction absolue d'inventer une couleur, une taille de texte ou une graisse — tout vient d'un token ou d'un style du DS Trident 2.0 / Odyssey 2.0, jamais d'une valeur choisie à la main
type: feedback
---
**Interdiction posée le 2026-10-14, formulée comme absolue :** « je t'interdis de prendre d'autres couleurs qui ne sont pas du design system ou de la lib partagée, tu ne dois jamais faire ça ». Étendue le même jour à la typographie : « pourquoi la typo n'est pas un composant ? nous avons une typo sous format composant avec plusieurs strates de taille, regular ou semi bold ».

Aucune couleur, aucune taille de texte, aucune graisse ne se choisit à la main. Ni en Figma, ni en HTML/CSS, ni « juste pour un essai », ni « pour une nuance plus claire ». Toute valeur vient d'un token ou d'un style existant.

## Échelle typographique Trident — relevée le 2026-10-14

| Style | Taille | Graisses |
|---|---|---|
| `Inter/B0` | 28 px | Semi Bold |
| `Inter/B3` | 16 px | Semi Bold, Regular |
| `Inter/B4` | 14 px | Semi Bold, Regular |
| `Inter/B5` | 12 px | Semi Bold, Regular |

**Il n'y a pas de 11 px, pas de 13 px.** J'avais posé du 11 px pour des libellés de rubrique : ça n'existe pas, le plus petit cran est B5 à 12 px. En Figma, appliquer le style avec `setTextStyleIdAsync`, jamais `fontSize` + `fontName`. Pour retrouver l'id d'un style : le relever sur un texte DS existant du même usage (`node.textStyleId` puis `getStyleByIdAsync`).

**Why:** Un hex inventé casse le lien au DS. Il survit aux itérations, se propage par copier-coller, et finit en dette invisible : le jour où le token change, l'élément bricolé ne suit pas. C'est arrivé sur la carte de verrouillage du Calendrier — cinq couleurs inventées (`#FFF6F0`, `#F0C3A3`, `#8A3A00`, `#1F2937`, `#4B5563`), en Figma **et** en CSS.

**How to apply:**

1. **Avant de poser une couleur**, chercher le token :
   - `mcp__figma__search_design_system` avec `entity: "variable"` — collection **Semantic colors** de Main Trident Ψ 2.0 (`Background/*`, `Surface/*`, `Content/*`, `Border/*`)
   - ou relever les `boundVariables` d'un composant DS déjà utilisé pour le même usage
2. **La meilleure source est le composant existant** : si le DS a déjà un objet pour ce cas (ex. le `Toaster` orange pour le verrouillage), partir de ses tokens plutôt que d'en chercher d'autres.
3. **En Figma**, lier la variable (`setBoundVariableForPaint`) au lieu d'écrire une couleur en dur. Attention : `{...paint, color}` **conserve** le lien à l'ancienne variable — pour rebinder il faut un paint neuf puis un bind explicite.
4. **En CSS**, déclarer les tokens en variables (`--token: …`) en tête de fichier avec leur nom DS en commentaire, et ne jamais écrire un hex ailleurs dans la feuille.
5. **Si le token n'existe pas pour ce besoin** : ne pas inventer. Le dire, et demander — soit on détourne un token voisin assumé, soit on fait créer le token côté DS.
6. **Un composant DS peut imposer sa couleur par variable** : le `Utilities / Padlock` est blanc par binding, il disparaît sur fond clair. Ce n'est pas une raison pour le repeindre d'une couleur inventée — chercher la variante ou le token prévus.

Voir [[Utiliser uniquement Trident 2.0 et Odyssey 2.0]] et [[Trident UI (site) = référence absolue]].
