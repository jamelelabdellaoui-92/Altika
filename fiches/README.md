# Fiches sommets — Altika

Fiches enrichies des sommets, consommées par l'application Altika.

## Accès (repo public)

```
https://raw.githubusercontent.com/jamelelabdellaoui-92/Altika/main/fiches/<slug>.json
https://raw.githubusercontent.com/jamelelabdellaoui-92/Altika/main/fiches/index.json
```

Le `slug` est dérivé du nom du sommet : minuscules, accents retirés, espaces → `-`
(ex. « Mont Blanc » → `mont-blanc`, « Aiguille du Midi » → `aiguille-du-midi`).

## Format d'une fiche

```json
{
  "v": 1,
  "name": "Mont Blanc",
  "elevation_m": 4807,
  "location": "Alpes — Massif du Mont-Blanc",
  "country": "France / Italie",
  "summary": "Résumé d'une à trois phrases.",
  "sections": [
    { "title": "Géographie", "body": "..." },
    { "title": "Alpinisme", "body": "..." }
  ],
  "first_ascent": "8 août 1786 — Balmat & Paccard",
  "source": "Données publiques (Wikipédia, OpenStreetMap)"
}
```

`index.json` liste les `slug` disponibles → l'appli n'interroge le réseau que
pour les sommets qui ont effectivement une fiche.

Si aucune fiche n'existe pour un sommet, l'application génère une fiche
hors-ligne à partir des données connues (altitude, proéminence, repérage).
