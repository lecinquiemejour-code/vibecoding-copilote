# Plan d'action — [Nom du projet]

> **Document vivant** — mis à jour à **chaque tour** de la boucle PDCA. Son état doit toujours refléter la réalité du dépôt.
> **Méthodologie** VibeCoding PDCA · **Statut cadrage** brouillon | validé le [date] · **Dernière mise à jour** [date]

## Comment lire / tenir ce document

- L'agent prend la **première feature « à faire »** dans l'ordre du tableau (les *Must have* d'abord).
- Il la passe en **« en cours »** au début du tour, puis en **« fait »** après le **commit local** (Check OK + GO #2).
- États possibles : `à faire` · `en cours` · `fait`.
- Tant qu'il reste des `à faire`, la boucle continue. Toutes les features en `fait` → on passe à la **clôture** (déploiement Netlify + bilan).

## Tableau de pilotage

| Ordre | Feature (du FDD) | État | Critère de réussite | Tour / commit |
|-------|------------------|------|---------------------|---------------|
| 1 | [...] | à faire | [comment on saura que c'est OK — mesurable si possible] | [...] |
| 2 | [...] | à faire | [...] | [...] |
| 3 | [...] | à faire | [...] | [...] |
| — | **Déploiement Netlify** (mise en ligne — après la dernière feature) | à faire | site accessible à l'URL publique, vérifié par l'utilisateur | [...] |

> Formuler les critères de console comme « aucune erreur **liée à notre code** » : le navigateur génère du bruit bénin (ex. 404 sur la favicon) qui ne doit pas invalider un CHECK.

## Journal des passes de non-régression

> À remplir au feeling, tous les N tours. Trace ce qui a été re-testé **en local**. (Le smoke test de prod n'a lieu qu'à la mise en ligne, en clôture.)

| Date | Après feature # | Non-régression (local) | Anomalie / action |
|------|-----------------|------------------------|-------------------|
| [...] | [...] | OK / KO | [...] |

## Pour aller plus loin (backlog)

> Rempli en **clôture**, après la mise en ligne : pistes d'évolution proposées et retenues pour un futur cycle (repêchage des *Could have* et *Questions ouvertes* du PRD inclus).

| Idée de feature | Valeur | Effort estimé |
|-----------------|--------|---------------|
| [...] | [...] | [...] |

## Notes de session

> Reprise de chantier : relire le PRD, l'archi-stack, le FDD, puis ce plan. Reprendre à la première feature « à faire » ou « en cours ».

- [...]
