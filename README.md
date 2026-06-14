# INF83 — Déploiement continu DevOps (CESI)

Support de cours **INF83 — Déploiement continu DevOps** et son **parcours de TP**, sous forme de présentations [Slidev](https://sli.dev).

## 🌐 En ligne (GitHub Pages)

| Deck | Lien |
|---|---|
| **Cours principal** | https://killian-aidalinfo.github.io/inf83-devops-cesi/ |
| **Parcours TP** (créneaux libres) | https://killian-aidalinfo.github.io/inf83-devops-cesi/tp/ |

Déploiement automatique à chaque push sur `main` via `.github/workflows/deploy-pages.yml`.

## 💻 En local

```bash
cd slide
npm install

npm run dev      # cours principal → http://localhost:3030
npm run dev:tp   # parcours TP     → http://localhost:3031
```

Les deux serveurs peuvent tourner **en parallèle** (ports différents).

## 📁 Contenu

- `slide/slides.md` — le cours principal (Git, culture DevOps, Docker, CI/CD GitHub Actions, tests, supervision, projet continu).
- `slide/slides-tp.md` — le parcours de petits TP qui s'assemblent sur les créneaux libres des 5 jours.
- `slide/style.css` — charte graphique (bleu CivilisationIT).
- `slide/global-bottom.vue` — pied de page de marque (titre dynamique selon le deck).

> Les schémas (boucle DevOps, pipeline CI/CD, flux dev/main → staging/prod) sont en **SVG vectoriel** dans `slides.md` (nets à la projection et à l'export PDF).
