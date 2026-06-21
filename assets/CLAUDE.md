# Règles du projet — [Nom du projet]

Ces règles encadrent le comportement attendu de l'agent de codage dans ce projet. Elles sont **non négociables** au niveau projet. En cas de conflit avec les contraintes système ou session de l'agent, les instructions de niveau supérieur restent prioritaires.

> Fichier de règles **canonique** (lu automatiquement par Claude Code). Transposable vers d'autres agents (`AGENTS.md`, `.clinerules`…) par simple copie/renommage — le contenu est volontairement agnostique.

---

## RÈGLE 0 — Méthode : VibeCoding PDCA, feature par feature

Le travail se fait **une feature à la fois**, en cycles PDCA. Chaque cycle suit cet ordre, sans le raccourcir :

**Plan → 🛑 GO #1 → Do → Check (local) → Act**

- **Plan** : proposer 3 options d'implémentation conformes à ces règles, expliquer le raisonnement. Ne rien coder à ce stade.
- **🛑 GO #1** : ne **jamais** écrire ou modifier du code sans approbation explicite (« GO »).
- **Do** : coder dans le périmètre strict de la feature.
- **Check** : lancer le **serveur local** et faire **tester par l'utilisateur** lui-même (jamais d'auto-validation par navigateur intégré ou sous-agent de navigation). Rien ne se publie sans vérification humaine en local.
- **Act** : si Check **KO** → revenir au Plan (rien n'est commité). Si Check **OK** → **🛑 GO #2** obligatoire avant le `commit` **local** (pas de `push` à ce stade — rien ne part en ligne). Puis mettre à jour l'état de la feature dans `plan-action.md`.
- **Non-régression (en local)** : à déclencher périodiquement, au jugement du dev (re-tester que les features déjà validées marchent toujours).
- **Mise en ligne — étape finale unique** : quand **toutes** les features sont « fait », clôture du chantier (**🛑 GO MISE EN LIGNE** : `push` + Netlify + URL vérifiée par l'utilisateur → puis walkthrough + post-mortem dans le dépôt → nouvelles features → checklist). Le déploiement n'arrive qu'**une fois**, en fin de projet, jamais à chaque feature.

> Méthode complète : voir `references/methode-pdca.md` (ou la doc de méthode du projet). Cette Règle 0 n'en est que le rappel exécutable.

---

## GARDE-FOUS

### Règle 1 — Checkpoint obligatoire
Ne jamais écrire ou modifier du code sans un GO explicite (GO #1). Ne jamais committer/pousser sans un GO explicite (GO #2).

### Règle 2 — Périmètre strict
Ne modifie que ce qui est explicitement demandé pour la feature en cours.

### Règle 2b — Éléments intouchables *(à adapter au projet)*
Ne change jamais [librairies sensibles / modèle IA / dépendances clés — **inscrire ici les vrais noms de fichiers et de librairies de ce projet**] sans GO explicite.

### Règle 3 — Réflexion avant action
Avant de demander le GO, explique ton raisonnement de façon pédagogique. Avant et pendant chaque action, explique en termes simples ce que tu fais et pourquoi. L'utilisateur doit comprendre et apprendre, même passivement.

---

## MÉTHODE DE TRAVAIL

### Règle 4 — Décomposition en sous-tâches
Décompose chaque tâche complexe en étapes petites et séquentielles.

### Règle 5 — 3 options systématiques
Propose 3 approches distinctes pour chaque modification significative.

### Règle 6 — Plan d'action avant le code
Rédige un plan d'action détaillé avant chaque génération de code.

### Règle 7 — Suivi à jour en permanence
Tiens l'état d'avancement (`plan-action.md`, todo list) à jour en temps réel.

---

## QUALITÉ DU CODE

### Règle 8 — Simplicité d'abord (KISS)
Privilégie toujours la solution la plus simple. *(KISS : Keep It Simple, Stupid.)*

### Règle 9 — Rien de superflu (YAGNI)
N'ajoute jamais de fonctionnalité non demandée. *(YAGNI : You Aren't Gonna Need It.)*

### Règle 10 — Code modulaire
Structure le code de manière modulaire (un fichier par responsabilité).

### Règle 11 — Logs de débogage détaillés
Ajoute des logs explicites à chaque étape clé.

### Règle 12 — Commentaires utiles
Explique le *pourquoi* (l'intention) plutôt que le *quoi*.

---

## POSTURE

### Règle 13 — Communication pédagogique
Explique chaque décision technique en termes accessibles, à un niveau calibré sur le profil de l'utilisateur (non-dev vs dev découvrant le vibecoding).

---

## ENVIRONNEMENT *(à adapter au poste / projet)*

### Règle 14 — Shell
[Inscrire ici les particularités du shell utilisé — ex. PowerShell n'accepte pas `&&`, utiliser `;` pour enchaîner les commandes.]

### Règle 15 — Build et sandbox
[Inscrire ici les pièges connus de l'environnement — ex. traiter une erreur `spawn EPERM` comme une limite probable du sandbox avant de conclure à un problème du projet.]
