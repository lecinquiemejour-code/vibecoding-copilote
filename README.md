# VibeCoding Copilote

Un skill **pédagogique** pour Claude : il pilote tout le développement d'une
application assistée par IA à partir d'un PRD, en suivant la méthode
**VibeCoding PDCA** (Le Cinquième Jour) — cadrage en dialogue (architecture,
découpage, plan d'action), puis construction *feature par feature* avec une
**validation humaine à chaque étape** (les « GO »), jusqu'à la mise en ligne et
le bilan.

> Point d'entrée : un **PRD**. S'il existe déjà (par ex. créé avec le skill
> compagnon `vibecoding-prd`), le copilote part de lui ; sinon, il commence par
> le **co-construire en dialogue** grâce au parcours d'élaboration embarqué
> (`references/prd/`), puis enchaîne sur le cadrage.

## ⬇️ Télécharger le skill

1. Sur la page d'accueil de ce dépôt GitHub, cliquez sur le bouton vert **`<> Code`**.
2. Cliquez sur **`Download ZIP`**.

*(Note : pour l'app Claude et Claude Desktop, le fichier `.zip` sert directement de package — ne l'extrayez pas. Pour un agent de code (Claude Code, Cursor, Antigravity…), c'est l'inverse : on l'extrait à la racine du projet — voir **Installation**).*

## Contenu du dépôt

- `SKILL.md` — l'orchestrateur : posture, phases (cadrage → construction → clôture) et les trois GO.
- `references/methode-pdca.md` — la méthode VibeCoding PDCA en détail (source unique de vérité).
- `references/prd/` — le parcours d'élaboration du PRD (`elaboration-prd.md` + support de cours `tuteur-PRD-L5J.md`), déroulé par le copilote quand le projet n'a pas encore de PRD.
- `references/templates/` — les gabarits des documents produits : `archi-stack.md`, `fdd.md`, `plan-action.md`, `walkthrough.md`, `post-mortem.md`.
- `assets/CLAUDE.md` — le gabarit de règles (Règle 0 / garde-fous) déposé à la racine du projet.

## Installation

### Dans l'app Claude (claude.ai) et Claude Desktop
1. Téléchargez le fichier ZIP du dépôt (voir **Télécharger le skill** ci-dessus).
2. Dans Claude, allez dans **Customize** (Personnaliser) → **Skills** (Compétences) → **« + »** → **« + Create skill »** (Créer une compétence) → **« Upload a skill »** (Importer une compétence).
3. Téléversez le fichier `.zip` téléchargé.
4. Activez le skill (toggle sur **ON**).
5. **Claude Desktop :** Si vous utilisez l'application de bureau, il peut être nécessaire de **quitter complètement et relancer Claude Desktop** pour que le nouveau skill soit visible et actif.

> Prérequis : l'**exécution de code** doit être activée dans vos préférences (Settings → Capabilities).

### Dans un agent de code (Claude Code, Cursor, Antigravity…)

1. Téléchargez le fichier ZIP du dépôt (voir **Télécharger le skill** ci-dessus).
2. Extrayez-le **à la racine de votre dossier de projet**, en conservant son dossier (typiquement `vibecoding-copilote-main/`) — ne mélangez pas son contenu avec les fichiers du projet.
3. Ouvrez le dossier du projet dans votre agent, puis collez le **prompt de démarrage** (ou de **reprise**) ci-dessous.

## Démarrer ou reprendre un projet

### Démarrage d'un projet neuf

Collez ce prompt dans l'agent, tel quel :

```text
Cherche dans ce projet le fichier `SKILL.md` du skill VibeCoding Copilote
(dans un dossier nommé `vibecoding-copilote`, `vibecoding-copilote-main`
si extrait d'un ZIP GitHub, ou directement à la racine). Lis-le et
déroule-le fidèlement : tu es le copilote VibeCoding (Le Cinquième Jour),
et ce fichier est ton mode d'emploi complet, avec ses références dans
le sous-dossier `references/` situé à côté de lui.

Commence par la Phase 0 : cherche un PRD dans le projet (co-construis-le
avec moi s'il n'existe pas), présente-toi, puis pose ta question de calibrage.
```

### Reprise d'un projet déjà entamé (avec la méthode)

Le contexte de l'agent s'efface entre deux sessions, mais les documents de
cadrage persistent — c'est le `plan-action.md` qui fait foi. Pour reprendre
le chantier, collez ce prompt :

```text
Ce projet est déjà en cours et suit la méthode VibeCoding PDCA.

Cherche dans ce projet le fichier `SKILL.md` du skill VibeCoding Copilote
(dans un dossier nommé `vibecoding-copilote`, `vibecoding-copilote-main`
si extrait d'un ZIP GitHub, ou directement à la racine). Lis-le — en
particulier sa section « Reprise de session » — ainsi que le fichier de
règles à la racine (`CLAUDE.md` / `AGENTS.md` / `.clinerules`) : tu es
le copilote VibeCoding qui reprend le chantier.

Ne refais pas le cadrage. Relis dans l'ordre : `PRD.md`, `archi-stack.md`,
`fdd.md`, puis `plan-action.md` — c'est lui qui fait foi sur l'état du
projet. Vérifie que son état correspond bien au dépôt (historique git) ;
si tu constates un écart, signale-le moi avant toute chose.

Cas particulier : si le cadrage était inachevé (documents en statut
« brouillon », ou `plan-action.md` absent), reprends au premier document
non validé — re-montre-le moi et redemande sa validation — au lieu
d'entrer dans la boucle.
```

## La méthode en bref

VibeCoding est une méthode de développement assisté par IA fondée sur la boucle
**PDCA** (Plan-Do-Check-Act) et la **validation humaine** à chaque étape :

- **Cadrage** — à partir du PRD, on co-construit en dialogue l'architecture & la stack, le découpage en features (FDD) et le plan d'action. Chaque document est validé un par un.
- **Construction** — on bâtit l'app **une feature à la fois**, avec **trois portes** : **GO #1** (autoriser l'écriture du code), **GO #2** (autoriser le commit local), **GO MISE EN LIGNE** (l'unique publication, en fin de projet).
- **Le test, c'est l'humain** — à chaque feature, l'agent lance le **serveur local** et c'est *vous* qui validez dans votre navigateur ; l'agent ne s'auto-valide jamais.
- **Clôture** — mise en ligne (Netlify), `walkthrough`, `post-mortem`, puis pistes pour aller plus loin.

## Sécurité

Un skill peut, en principe, faire exécuter du code par Claude. **Relisez toujours
le contenu d'un skill avant de l'activer.** Celui-ci ne contient que du
**Markdown** — aucun script ni dépendance. En usage, c'est l'agent qui écrit du
code et lance des commandes (serveur local, `git`) dans *votre* projet — mais
toujours après votre accord explicite (les GO), jamais de lui-même.

## Auteur, licence & usage

Créé par [Jean Noël Lefebvre (L5J)](https://cv-jean-noel.netlify.app/) — © Jean Noël Lefebvre, Le Cinquième Jour.

[![Licence : CC BY-NC-SA 4.0](https://img.shields.io/badge/Licence-CC%20BY--NC--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-nc-sa/4.0/deed.fr)

Ce skill (méthode, gabarits et documentation) est publié sous licence [Creative Commons Attribution - Pas d'Utilisation Commerciale - Partage dans les Mêmes Conditions 4.0 International (CC BY-NC-SA 4.0)](https://creativecommons.org/licenses/by-nc-sa/4.0/deed.fr) :

- **Usage non commercial** (personnel, éducatif, associatif) : **libre** — utilisez, copiez, adaptez et rediffusez, à condition de **créditer l'auteur** et de **partager vos adaptations sous la même licence**.
- **Usage commercial** (formation facturée, prestation, intégration à une offre payante…) : soumis à une **licence commerciale séparée** — contactez **Le Cinquième Jour** : <lecinquiemejour@gmail.com>.

Texte complet de la licence : voir [LICENSE](LICENSE).
