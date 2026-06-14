# INF83 — Déploiement continu DevOps — Slides

Deux présentations [Slidev](https://sli.dev) du module **INF83 — Déploiement continu DevOps** (CESI) : le **cours** et le **parcours de TP**.
En ligne : <https://killian-aidalinfo.github.io/inf83-devops-cesi/> · TP : <https://killian-aidalinfo.github.io/inf83-devops-cesi/tp/>

## Installation

```bash
npm install
```

## Mode présentation (rechargement à chaud)

```bash
npm run dev      # cours principal → http://localhost:3030
npm run dev:tp   # parcours TP     → http://localhost:3031
```

Les deux peuvent tourner en parallèle (ports différents).

## Export PDF / Build statique

```bash
npm run export     # cours principal
npm run export:tp  # parcours TP
npm run build      # build statique du cours
npm run build:tp   # build statique du parcours TP (dossier dist-tp/)
```

## Structure

- `slides.md` — le cours principal (couverture, programme, 10 chapitres + annexes).
- `slides-tp.md` — le parcours de petits TP qui s'assemblent (créneaux libres des 5 jours).
- `style.css` — charte graphique (bleu CivilisationIT).
- `global-bottom.vue` — pied de page de marque (titre dynamique selon le deck).
- `public/images/` — schémas restants en image (les principaux sont en SVG dans `slides.md`).

## Raccourcis Slidev utiles en présentation

- `f` : plein écran
- `o` : vue d'ensemble des slides
- `d` : mode sombre / clair
- `←` `→` : navigation
