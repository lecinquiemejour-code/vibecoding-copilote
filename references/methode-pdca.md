# La méthode PDCA du VibeCoding — Le Cinquième Jour

> Document de référence. Source **unique** de vérité sur la méthode : le `SKILL.md` et la « Règle 0 » du `CLAUDE.md` n'en donnent qu'un résumé et renvoient ici pour le détail.

## L'idée maîtresse

Le VibeCoding applique le cycle **PDCA** (Plan-Do-Check-Act, la roue de Deming — un cycle d'amélioration continue issu de la qualité industrielle) au développement assisté par IA. La particularité : le cycle ne tourne **pas** au niveau du projet entier, mais **feature par feature**, en micro-itérations. C'est du développement **itératif et incrémental** (cycles courts + livraison par petits morceaux), proche du **Feature-Driven Development (FDD)**.

Ce que le VibeCoding ajoute : l'IA raccourcit drastiquement la durée de chaque itération, ce qui rend ce micro-incrémental praticable même pour un public non-développeur.

## Les deux niveaux

**Cadrage amont (une fois par projet).** Quatre documents, créés dans l'ordre des dépendances :

```
PRD  →  archi-stack  →  fdd  →  plan-action
```

- `PRD.md` — le *quoi* et le *pourquoi* (besoin, table MoSCoW, contraintes, critères de succès). Stable.
- `archi-stack.md` — le *comment* technique (architecture + stack), figé après le choix ; fige aussi la **commande de lancement local** (+ port) réutilisée à chaque CHECK.
- `fdd.md` — la décomposition du PRD en **features-unités de construction**.
- `plan-action.md` — l'ordonnancement, l'état et les critères ; le **document vivant**, mis à jour à chaque tour.

Le `CLAUDE.md` (fichier de règles canonique) surplombe ces documents : il est consulté **en continu** pendant toute la boucle.

**Boucle d'exécution (à chaque tour = une feature).** Le cœur de la méthode, détaillé ci-dessous.

## La boucle, tour par tour

1. **Choix de la feature.** Lire le `plan-action.md`, prendre la première feature « à faire » dans l'ordre de priorité (les *Must have* d'abord). La marquer « en cours ».

2. **PLAN.** Proposer **3 options d'implémentation** conformes aux règles du `CLAUDE.md`, en expliquant le raisonnement de façon pédagogique, à un niveau calibré sur le profil de l'utilisateur. On décrit le *comment* de cette feature ; on n'écrit rien encore.

3. **🛑 GO #1 — checkpoint humain avant tout code.** Attendre une validation explicite. Sans GO, pas de code. Un refus n'est pas un échec : on révise la proposition et on re-soumet.

4. **DO.** Écrire le code, dans le **périmètre strict** de la feature, proprement : structure modulaire, logs utiles, commentaires qui expliquent le *pourquoi* (l'intention) plutôt que le *quoi*. Expliquer au fil de l'eau, en termes simples, ce qu'on fait et pourquoi.

5. **CHECK — l'utilisateur teste, pas l'agent.** Lancer le **serveur local** du projet (typiquement `npm run dev` ; pour une stack sans build, un serveur statique type `npx serve` / `python -m http.server`), donner à l'utilisateur l'**URL locale** et la liste de ce qu'il doit observer (le **critère de réussite** de la feature), puis **attendre son verdict**. L'agent ne s'auto-valide pas : ni navigateur intégré, ni sous-agent de navigation, ni capture d'écran prise comme preuve. C'est le **garde-barrière** : rien ne part en ligne tant que l'humain n'a pas vérifié localement.

6. **ACT — deux issues :**
   - **Check KO** → retour au PLAN pour corriger. **Aucun GO, rien n'est publié.** Corriger ne fait que reboucler.
   - **Check OK** → **🛑 GO #2 — checkpoint humain avant sauvegarde.** Attendre une validation explicite. Sur GO : **`commit` local uniquement** — pas de `push`, rien ne part en ligne (la mise en ligne est une étape finale unique, voir « Clôture du chantier »). Puis marquer la feature « fait » dans le `plan-action.md` — ce changement d'état fait partie du commit.

7. **Feature suivante.** Reboucler tant qu'il reste des features « à faire ».

### Pourquoi trois GO ?

Trois actions engagent à des degrés différents, chacune sa porte :
- **GO #1** protège l'**écriture** : lâcher un agent sur une feature sans valider l'approche mène souvent à du code qu'on ne maîtrise plus.
- **GO #2** protège la **sauvegarde locale** (commit) : on grave un état dans l'historique seulement quand l'utilisateur a constaté que la feature marche.
- **GO MISE EN LIGNE** protège la **publication** : c'est l'unique moment où le code quitte la machine pour internet. Il n'arrive **qu'une fois**, en fin de projet (voir « Clôture du chantier »).

Rien d'irréversible — et surtout rien de public — ne se produit sans une approbation humaine explicite.

## La passe périodique — non-régression (en local)

Tous les **N tours, au jugement du dev** (au feeling, sans plancher imposé), faire **re-tester par l'utilisateur, en local**, que les features déjà validées fonctionnent toujours — vérifier qu'une nouvelle feature n'a rien cassé d'ancien (*regression testing*). Si KO → ouvrir un cycle de correction.

Le N est laissé au jugement : c'est un choix de fluidité assumé. Pendant toute la boucle, le projet n'existe **qu'en local** ; le **smoke test de prod** (vérifier que le site réellement en ligne fonctionne) appartient à l'étape de mise en ligne, en clôture.

## Clôture du chantier

Quand toutes les features sont « fait », la *construction* est finie — mais le chantier se clôt en **cinq temps**, dans l'ordre, chacun validé. **Tant que la dernière étape n'est pas franchie, le projet n'est pas « terminé ».**

1. **🛑 GO MISE EN LIGNE** — l'unique porte de publication : vérifier/créer le dépôt distant, `push` de tous les commits de la boucle, connecter Netlify, puis **faire vérifier l'URL publique par l'utilisateur** (le smoke test de prod ; jamais d'auto-validation par l'agent). Une fois cette porte franchie, le dépôt distant existe : les documents qui suivent sont commités **puis poussés** en routine.
2. **Walkthrough** — un `walkthrough.md` écrit **dans le dépôt** (visite guidée du code pour les élèves, peut renvoyer à l'URL en ligne) ; commit + push.
3. **Post-mortem** — un `post-mortem.md` écrit **dans le dépôt** : prévu vs réalisé, ce qui a marché, les frictions (déploiement compris), les décisions revues, les leçons ; commit + push.
4. **Nouvelles features** — proposer 3 pistes d'évolution (valeur + effort), en repêchant les *Could have* et les *Questions ouvertes* du PRD ; consigner les retenues dans une section « Pour aller plus loin » du `plan-action.md`.
5. **Fin de chantier** — ne déclarer « terminé » qu'avec la checklist complète (features « fait » · site en ligne vérifié · walkthrough · post-mortem · nouvelles features consignées), puis récapituler avec l'**URL publique**.

> Le déploiement est une étape **planifiée** du `plan-action.md`, inscrite dès le cadrage **après la dernière feature** — pas une surprise de dernière minute.

## Le plan d'action comme mémoire persistante

Le contexte de l'agent s'efface entre deux sessions ; le `plan-action.md`, lui, persiste dans le dépôt. Son état doit **toujours refléter la réalité du dépôt** : on l'ouvre, on voit immédiatement ce qui est fait et ce qui reste. C'est lui qui dit par où commencer, où on en est, et quand s'arrêter (toutes les features « fait » = v1 terminée).

## Schéma de synthèse

```
                 ┌──────────────────────────────────────┐
                 │  CADRAGE : PRD → archi-stack → fdd →  │
                 │            plan-action  (+ CLAUDE.md) │
                 └───────────────────┬──────────────────┘
                                     │  (sas + GO)
                                     ▼
   ┌─────────────────── BOUCLE PDCA (par feature) ───────────────────┐
   │  lire plan-action → PLAN (3 options/règles)                      │
   │      → 🛑 GO #1 → DO → CHECK local (l'utilisateur teste)         │
   │          ├─ KO → retour PLAN (rien commité)                      │
   │          └─ OK → 🛑 GO #2 → commit LOCAL → état « fait »         │
   │      → feature suivante                                          │
   │  (tous les N tours, au feeling : non-régression locale)         │
   └───────────────────────────────┬─────────────────────────────────┘
                                    │  (toutes les features « fait »)
                                    ▼
   ┌────────────────────── CLÔTURE DU CHANTIER ──────────────────────┐
   │  🛑 GO MISE EN LIGNE : push + Netlify + URL vérifiée            │
   │   → walkthrough → post-mortem  (dans le dépôt, commit + push)    │
   │   → nouvelles features (« Pour aller plus loin »)                │
   │   → checklist → FIN (récap + URL publique)                       │
   └─────────────────────────────────────────────────────────────────┘
```
