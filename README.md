# VibeCoding Copilote

Un skill **pédagogique** pour Claude : il pilote tout le développement d'une
application assistée par IA à partir d'un PRD, en suivant la méthode
**VibeCoding PDCA** (Le Cinquième Jour) — cadrage en dialogue (architecture,
découpage, plan d'action), puis construction *feature par feature* avec une
**validation humaine à chaque étape** (les « GO »), jusqu'à la mise en ligne et
le bilan.

> Pré-requis : un **PRD** déjà rédigé. Pour le créer pas à pas, voir le skill
> compagnon `vibecoding-prd`.

## ⬇️ Télécharger le skill

1. Sur la page d'accueil de ce dépôt GitHub, cliquez sur le bouton vert **`<> Code`**.
2. Cliquez sur **`Download ZIP`**.

*(Note : Le fichier `.zip` ainsi téléchargé sert directement de package pour le skill. N'extrayez pas son contenu).*

## Contenu du dépôt

- `SKILL.md` — l'orchestrateur : posture, phases (cadrage → construction → clôture) et les trois GO.
- `references/methode-pdca.md` — la méthode VibeCoding PDCA en détail (source unique de vérité).
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

### Dans Claude Code
```bash
git clone https://github.com/lecinquiemejour-code/vibecoding-copilote.git ~/.claude/skills/vibecoding-copilote
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

## Auteur & usage

Créé par [Jean Noël Lefebvre (L5J)](https://cv-jean-noel.netlify.app/).

© Jean Noël Lefebvre — Le Cinquième Jour. Tous droits réservés.
Ce skill est mis à disposition pour un **usage pédagogique** (notamment dans le cadre du bootcamp VibeCoding). Sa reproduction, sa modification et sa rediffusion publiques sont soumises à l'autorisation de l'auteur.
