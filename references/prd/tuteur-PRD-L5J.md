# Le PRD, en 5 minutes — Tuteur L5J

> *Comprendre pourquoi un PRD change tout, avant d'en écrire un.*
> Partie **tuteur** du parcours « Élaboration d'un PRD » — VibeCoding · Le Cinquième Jour.

---

## 📍 Où tu es dans le parcours

Élaborer un PRD se fait ici en **deux temps** :

1. **Comprendre** *(tu es ici)* — cette page t'explique ce qu'est un PRD et pourquoi il change tout. **5 minutes de lecture.**
2. **Faire** — ensuite, tu élabores **ton** PRD directement avec **Claude**, qui t'interviewe brique par brique et rédige le document avec toi.

> Tu n'as donc rien à rédiger en lisant cette page. Lis pour comprendre — Claude s'occupera de la mise en forme à l'étape 2.

---

## C'est quoi un PRD ?

**PRD** = *Product Requirements Document*, ou **Document de Spécifications Produit**.

Une seule idée à retenir : un PRD décrit **ce que** le produit doit faire — **jamais comment** il le fait techniquement.

> ✅ **Bon** : « Une appli web de feu d'artifice où l'on lance des fusées en cliquant sur l'écran. »
>
> ❌ **À éviter** : « Une appli React utilisant Canvas 2D et `requestAnimationFrame` pour le rendu des particules. »

Le second n'est pas faux — il est juste **au mauvais endroit**. Il décrit le *comment* (l'implémentation), alors qu'un PRD parle du *quoi* (l'intention).

| Document | Répond à la question |
|----------|----------------------|
| **PRD** | Le **quoi** — les besoins |
| Spec technique | Le **comment** — l'architecture, le code |
| Design doc | L'**apparence** — UI/UX, maquettes |
| Manuel | L'**usage** — comment s'en sert l'utilisateur |

---

## Pourquoi s'embêter à en écrire un ?

Parce que sans PRD, on **code à vue**. Et coder à vue, ça produit deux maladies :

- **Le scope creep** (*dérive du périmètre*) : on ajoute des fonctionnalités non prévues, « tant qu'on y est »… et le projet ne finit jamais.
- **Le flou du "terminé"** : sans cap défini, impossible de savoir si c'est fini, ou si c'est bon.

Un PRD, c'est le **cap partagé** : tout le monde — toi, ton client, et ton IA — vise la même chose.

---

## La nuance qui fait la différence : « à quel niveau ? »

« Pas de technique dans un PRD » ne veut **pas** dire « pas d'exigences chiffrées ».

On distingue deux familles :

- Une **fonctionnalité** dit ce que le produit *fait* → « lancer une fusée au clic ».
- Une **exigence non-fonctionnelle** dit la *qualité* attendue, transversale → « l'animation doit rester fluide (60 images/seconde) ».

> 💡 **FPS** = *frames per second*, images par seconde. En dessous de ~30, l'œil perçoit des saccades ; 60 donne une animation fluide.

La règle simple : **le niveau de qualité a sa place dans le PRD** (« ça doit être rapide, fluide, accessible »). **Le moyen de l'atteindre, non** (« avec Canvas 2D », « avec tel framework »). Ça, c'est la spec technique.

---

## Pour QUI écrit-on ce PRD ? (le point qui change tout en VibeCoding)

Réponse classique : pour l'équipe, le client, les développeurs.

Réponse **VibeCoding** : de plus en plus, **pour une IA qui va coder à partir de lui**.

Et ça change la donne. Un développeur humain *comble les trous* : si ton PRD est vague, il devine ton intention. **Une IA, non.** Elle prend ton PRD au pied de la lettre — et là où c'est flou, elle *invente* (on parle d'**hallucination** : l'IA produit une réponse plausible mais non fondée sur tes intentions réelles).

> **Le PRD précis n'est pas de la bureaucratie. C'est ce qui empêche l'IA de décider à ta place.**

C'est la même logique qu'un bon prompt : un brief vague produit un résultat générique et sans intention ; un brief structuré produit un résultat fidèle à ta vision. **Un bon PRD, c'est du prompting structuré appliqué à la conception d'un produit.**

---

## Le PRD n'a pas à être parfait du premier coup

Important, parce que la page blanche intimide : **le PRD est un point de départ, pas un contrat gravé dans le marbre.**

Dans le cycle **PDCA** (*Plan – Do – Check – Act* : planifier, faire, vérifier, ajuster) qui structure le VibeCoding, le PRD est l'artefact du **Plan**. C'est la **première boucle**.

- Tu **planifies** (le PRD).
- L'IA **fait** (le code).
- Tu **vérifies** (ça correspond ?).
- Tu **ajustes** (tu enrichis le PRD).

Donc : les zones de flou que tu laisses aujourd'hui se refermeront aux boucles suivantes. Tu as le droit d'écrire « *à décider plus tard* ». Le PRD **évolue avec le projet** — c'est sa nature.

---

## Ce qu'on va construire ensemble

Un PRD pour une petite application (visuelle, chatbot, outil…) tient sur **7 briques**. Tu n'as pas à les maîtriser maintenant — on les remplira **une par une en mode interview**. Juste pour que tu saches où on va :

1. **Vision & Objectifs** — *pourquoi ce projet ?*
2. **Utilisateurs cibles** — *pour qui ?* (via des **personas** : des profils-types d'utilisateurs, fictifs mais représentatifs)
3. **Fonctionnalités** — *quoi exactement ?* (priorisées en **MoSCoW** : *Must / Should / Could / Won't* — l'indispensable, l'important, le souhaitable, l'exclu)
4. **Interactions** — *comment on l'utilise ?*
5. **Spécifications visuelles** — *à quoi ça ressemble, comment ça bouge ?*
6. **Contraintes** — *les limites et exigences (performance, compatibilité…)*
7. **Critères de succès** — *comment on saura que c'est réussi ?*

---

## À quoi ça ressemble, un PRD fini ? (exemple express)

Voici le projet « Feu d'artifice interactif » résumé en PRD — volontairement court, juste pour que tu voies la forme :

**1. Vision** — Une appli web où on lance des fusées en cliquant sur l'écran ; elles explosent en particules colorées. But : s'amuser, effet « wow ».

**2. Utilisateurs** — Grand public (tous âges, non technique) qui veut une animation ludique sans rien installer.

**3. Fonctionnalités (MoSCoW)**
- *Must* : lancer une fusée au clic · explosion en particules · animation fluide
- *Should* : plusieurs types d'explosion · image de fond personnalisable
- *Could* : sons d'explosion · mode automatique
- *Won't* : multijoueur

**4. Interactions** — Clic gauche → une fusée part du bas vers le point cliqué. Menu déroulant → change le type d'explosion.

**5. Spécifications visuelles** — Ambiance nuit étoilée, fond bleu nuit profond. Particules colorées qui scintillent puis retombent et s'éteignent en fondu.

**6. Contraintes** — Animation fluide (60 images/seconde) même avec beaucoup de particules · marche sur navigateurs récents · desktop en priorité, mobile supporté.

**7. Critères de succès** — Effet « wow » à la première fusée · chaque type d'explosion est visuellement distinct · aucune saccade après plusieurs minutes.

> 💡 Une demi-page, et pourtant tout y est : le *quoi*, les priorités, la qualité attendue. C'est ça, l'objectif — pas un pavé.

---

## À retenir avant de passer à la pratique

- Un PRD décrit le **quoi**, pas le **comment**.
- La **qualité attendue** (fluide, rapide) y a sa place ; le **moyen technique**, non.
- En VibeCoding, le PRD est souvent **lu par une IA** → la précision n'est pas optionnelle, elle empêche l'IA d'inventer.
- C'est l'étape **Plan** du PDCA : **itératif**, jamais parfait du premier coup.
- Un bon PRD = du prompting structuré appliqué à ton produit. **Précis en entrée, fidèle en sortie.**

> **Prêt ? On passe à la pratique : on va élaborer *ton* PRD, brique par brique.**

---

## 🚀 Passer à la pratique avec Claude

Maintenant que tu comprends l'intérêt d'un PRD, **Claude va t'aider à écrire le tien**. Pas de page blanche : il te pose les questions, une par une, et rédige le PRD au fur et à mesure.

**Comment lancer l'interview :**

> Ouvre une conversation avec Claude et tape **`/vibecoding-prd`**
> ou écris simplement : *« aide-moi à élaborer le PRD de mon projet »*.

**Ce qui t'attend :**

- Claude t'**interviewe brique par brique** (les 7 sections vues plus haut), **une question à la fois**.
- Tu réponds avec tes mots — **pas besoin de jargon**, Claude reformule.
- Tu as le droit de dire **« je ne sais pas encore »** : on l'inscrit comme question ouverte, à trancher plus tard *(souviens-toi : le PRD est itératif)*.
- À la fin, Claude te livre **deux choses** : ton **PRD rédigé**, et une **amorce de prompt** prête à coller à ton agent de code.
- Cette amorce commence par te faire **choisir ton approche technique** (architecture, stack) : l'agent te propose 2-3 options avec avantages/inconvénients, et **c'est toi qui tranches** — avant qu'une seule ligne soit codée.

> 🎯 **Compte ~10 à 15 minutes.** Un premier PRD imparfait vaut toujours mieux qu'un projet codé à vue.

---

*Le Cinquième Jour — parcours VibeCoding · document tuteur, v1*
