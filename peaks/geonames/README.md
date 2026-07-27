# Packs de sommets GeoNames — Altika

971 268 sommets nommés, monde entier, découpés en cellules de 1° × 1°.

## Pourquoi

La base embarquée dans l'application (`peaks-db.json`, OSM + Wikidata) est à 83 %
européenne. Autour de Tétouan (Maroc), dans un rayon de 25 km, elle contient
2 entrées — dont un doublon. GeoNames en contient 447. Sans sommet dans la base,
la vue en réalité augmentée n'a rien à afficher, quelle que soit la précision de
la boussole.

| Zone | Base embarquée | Ces packs |
|---|---|---|
| Tétouan, rayon 25 km | 2 | 447 |
| Rif occidental (110 × 90 km) | 8 | 2 056 |
| Haut Atlas (Toubkal) | 88 | 3 453 |

## Format

Un fichier par cellule, nommé `<floor(lat)>_<floor(lon)>.json` :

```json
{"source":"GeoNames","license":"CC-BY-4.0","attribution":"https://www.geonames.org/",
 "cell":[35,-6],"fetchedAt":"...","peaks":[["Jebel Kelti",35.358,-5.2758,1926,0]]}
```

Chaque sommet est `[nom, latitude, longitude, altitude_m, proéminence_m]`.
La proéminence vaut toujours `0` = **inconnue** : GeoNames ne la fournit pas.
L'application trie par proéminence puis altitude, donc les sommets OSM/Wikidata
(qui en ont une) restent affichés en premier ; ces packs complètent, ils ne
remplacent pas.

`index.json` liste les cellules disponibles.

## Contenu retenu

Codes GeoNames `MT`, `PK`, `PKS`, `HLL`, `VLC` — des **points**.

Écartés volontairement :
- `MTS` / `HLLS` (massifs, groupes de collines) : ce sont des **ensembles**, dont
  la position est un centre et l'altitude celle d'un sommet situé à plusieurs
  kilomètres. Ils produisent des étiquettes flottant à mi-pente.
- entrées sans altitude ;
- cols (`PASS`, `GAP`) : traités séparément par l'application.

## Licence et attribution

Données © [GeoNames](https://www.geonames.org/), sous licence
[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).
**L'attribution est obligatoire** et figure dans l'écran « À propos » d'Altika.

Régénération : `tools/geonames-peaks/build_packs.py` dans le dépôt de l'application.
