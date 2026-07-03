# FDD — Décomposition en features — [Nom du projet]

> **Version** 0.1 · **Date** [date] · **Statut** brouillon | validé le [date] · **Méthodologie** VibeCoding PDCA
> Traduit les fonctionnalités du PRD (table MoSCoW) en **features-unités de construction** — des morceaux assez petits pour tenir dans un cycle PDCA chacun.
> Dérivé du PRD **et** de l'architecture retenue (la façon de découper dépend de la stack).

## Principe de formulation

Chaque feature est nommée à la manière FDD : **`<action> <résultat> <objet>`**
*Exemples :* « afficher la liste des clics », « enregistrer une partie en cours », « valider le formulaire de contact ».

Une bonne feature-unité est : **petite** (réalisable en un cycle), **testable seule** (on sait dire si elle marche), et **autonome** (elle n'exige pas qu'une autre soit finie en même temps).

## Features issues des « Must have »

> Le cœur de la v1. Ce sont elles qui peupleront le plan d'action en priorité.
> Pour une app web, inclure la **favicon** dès la feature-squelette : évite un 404 permanent en console qui parasite tous les CHECK.

| # | Feature (`action résultat objet`) | Issue de (PRD) | Note |
|---|-----------------------------------|----------------|------|
| 1 | [...] | [feature MoSCoW d'origine] | [...] |
| 2 | [...] | [...] | [...] |

## Features issues des « Should / Could have »

> À construire après la v1, dans des tours ultérieurs.

| # | Feature | Priorité (Should / Could) | Note |
|---|---------|---------------------------|------|
| ... | [...] | [...] | [...] |

## Couverture du PRD

> Vérification de complétude, **dans les deux sens** : chaque exigence du PRD (Must have + spécifications visuelles/sonores) est mappée vers une feature, ou explicitement non couverte (avec raison). Aucune omission silencieuse.

| Exigence du PRD | Couverte par | Si non couverte : raison |
|-----------------|--------------|--------------------------|
| [...] | F[n] | — |
| [...] | — | [reportée / écartée car ...] |

## Hors périmètre (« Won't have »)

> Rappel des exclusions du PRD — pour ne pas dériver.

- [...]

## Dépendances entre features

> Si une feature en exige une autre avant elle, le noter ici (ça guidera l'ordre dans le plan d'action).

- [Feature X] avant [Feature Y] car [...].
