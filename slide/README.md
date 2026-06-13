# INF83 - Déploiement continu DevOps — Slides

Présentation [Slidev](https://sli.dev) du support de cours **INF83 - Déploiement continu DevOps** (CESI), générée à partir de `../INF83_support_deploiement_continu_devops.md`.

Identité visuelle aux couleurs de [CivilisationIT](https://civilisation-it.fr).

## Installation

```bash
npm install
```

## Lancer le mode présentation (avec rechargement à chaud)

```bash
npm run dev
```

Puis ouvrir <http://localhost:3030>.

## Export PDF

```bash
npm run export
```

## Build statique (pour déploiement web)

```bash
npm run build
```

## Structure

- `slides.md` — toutes les diapositives (13 sections du cours + couverture, sommaire et clôture)
- `style.css` — charte graphique CivilisationIT (couleurs, badges, callouts)
- `global-bottom.vue` — pied de page de marque affiché sur chaque diapositive
- `public/images/` — schémas originaux du support (boucle DevOps, cycle Git, pipeline CI/CD, conteneurisation, stratégies de déploiement)

## Raccourcis Slidev utiles en présentation

- `f` : plein écran
- `o` : vue d'ensemble des slides
- `d` : mode sombre / clair
- `←` `→` : navigation
