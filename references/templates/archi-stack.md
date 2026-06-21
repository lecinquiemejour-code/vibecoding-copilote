# Architecture & Stack — [Nom du projet]

> **Version** 0.1 · **Date** [date] · **Statut** Figé après choix · **Méthodologie** VibeCoding PDCA
> Dérivé du PRD. Décrit le *comment* technique. Une fois l'approche choisie, ce document est stable.

## Approche retenue

[Nom court de l'approche choisie, en une phrase.]

**Pourquoi celle-ci :** [justification en 2-3 phrases — pourquoi elle répond le mieux au besoin du PRD et aux contraintes.]

## Stack technique

| Couche | Choix | Rôle |
|--------|-------|------|
| Langage / framework | [...] | [...] |
| Interface / rendu | [...] | [...] |
| Données (si besoin) | [...] | [...] |
| Hébergement / déploiement | Netlify | mise en ligne en **étape finale** (après la dernière feature), puis auto à chaque `push` ultérieur |
| Versioning | Git + [GitHub / autre] | historique et synchronisation |

## Lancement local

**Commande :** `[npm run dev / npx serve / python -m http.server …]` · **Port :** `[ex. 5173 / 8080]`

> Commande et port **figés** ici : réutilisés **à l'identique** à chaque CHECK (test en local par l'utilisateur). Évite la dérive d'un port à l'autre d'un tour sur l'autre.

## Architecture en bref

[Description courte de l'organisation du code : les grandes parties et comment elles communiquent. Un schéma ASCII simple est le bienvenu si utile.]

## Contraintes techniques héritées du PRD

- **Performance :** [rappel du niveau attendu]
- **Compatibilité :** [mobile / desktop / navigateurs]
- **Accessibilité :** [niveau attendu]

## Alternatives écartées

> Trace des 2-3 approches proposées et non retenues — utile pour ne pas re-débattre plus tard.

- **[Approche B] :** écartée car [...].
- **[Approche C] :** écartée car [...].

## Notes

[Tout point technique à garder en tête : dépendances sensibles, librairies à ne pas changer sans GO, particularités d'environnement, etc.]
